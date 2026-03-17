# Core Reverse Engineering Reference
## Character Loading, Connection Binding, Inventory, Equipment, Spawn, and Error Model

## Document Purpose

This document describes the most probable runtime behavior of the game core based on recovered code structure, recovered function names, and observed runtime logs.

It is intended to help with:

- understanding the player lifecycle
- understanding online versus offline/NPC character flow
- understanding how character state is loaded
- understanding how inventory and equipment depend on character state
- understanding what can fail during spawn, respawn, and modding
- rebuilding mental models for future maintenance and extension work

This document is intentionally written as clean technical documentation.

It is not a raw decompilation dump.

It is a reconstruction of the likely design and execution model of the core.

---

## Confidence Model

This document is based on recovered code and logs, but should still be treated as a **probable runtime model**, not as a perfect statement of the original source.

The strongest confidence areas are:

- manager responsibilities
- load order dependencies
- connection versus character identity separation
- spawn lifecycle stages
- major failure cases and their meaning

The weakest confidence areas are:

- unnamed helper functions
- internal utility methods recovered as generic `FUN_...`
- hidden side effects of deeply nested runtime calls
- exact data layouts for all supporting classes

Even with those limitations, the recovered structure is strong enough to produce a very usable technical map of the system.

---

# 1. Core Runtime Philosophy

The core appears to be **character-state driven**, not purely connection-driven.

The most likely dependency chain is:

**playerId → CharacterInfo → CharacterParameters → Inventory/Equipment → Runtime Player Object → World → Online Systems**

This means:

- a live network connection alone is not enough to produce a valid player
- a runtime Player object alone is not enough to produce a valid player
- the central dependency is most likely **CharacterInfo**
- inventory and equipment appear to depend on valid character state
- connection-dependent systems appear to sit later in the lifecycle

This design also explains how a character-like entity may exist without a live player connection, which is highly relevant for NPCs or server-side characters.

---

# 2. Main Systems and Their Most Probable Responsibilities

## 2.1 ConnectedPlayersManager

### Purpose

This system appears to manage the online registry of active players.

### Most probable responsibilities

- track which players are known as connected/active
- map player identity to online runtime state
- notify other players about player visibility events
- broadcast connect/disconnect style updates
- support GM-related online management actions

### Recovered callable functions

`ConnectedPlayersManager::_notifyAll_sendInfo`  
`ConnectedPlayersManager::_notifyAll_disconnect`  
`ConnectedPlayersManager::onGmStatusChanged`  
`ConnectedPlayersManager::kickPlayer`  
`ConnectedPlayersManager::setGM`  
`ConnectedPlayersManager::banPlayer`  
`YoConnectedPlayerEvent::pack`  
`YoConnectedPlayerEvent::unpack`

### Most important interpretation

This system does **not** look like the character creation system.

It looks like a **post-registration online visibility layer**.

It expects valid player data to already exist.  
If it cannot find that data, it fails with `"no player info found"`.

### Modding implication

If this manager errors out, the root cause is usually earlier:

- bad player identity
- missing registration
- incomplete spawn
- invalid respawn cleanup
- trying to broadcast a player that was never fully initialized

---

## 2.2 CharacterInfo

### Purpose

CharacterInfo appears to be the central bridge between identity, persistent state, runtime player state, and simulation.

### Most probable responsibilities

- represent the active logical character
- store or resolve the active character identity
- expose inventory access
- expose player access
- hold simulation-related state
- mark data as dirty and push changes
- send initial character data to the client
- bridge loaded data into live runtime behavior

### Recovered callable functions

`CmCharacterInfo::_loadCharParamsFromDb`  
`CmCharacterInfo::_loadCarriedMovableFromDb`  
`CmCharacterInfo::~CmCharacterInfo`  
`CmCharacterInfo::getConstitution`  
`CmCharacterInfo::getWillpower`  
`CmCharacterInfo::_setDirty`  
`CmCharacterInfo::changeLockStat`  
`CmCharacterInfo::changeStatValue`  
`CmCharacterInfo::checkStat`  
`CmCharacterInfo::getAgility`  
`CmCharacterInfo::getEffects`  
`CmCharacterInfo::getIntellect`  
`CmCharacterInfo::getInventory`  
`CmCharacterInfo::getNominalStrength`  
`CmCharacterInfo::getStrength`  
`CmCharacterInfo::getPlayer`  
`CmCharacterInfo::getRealStatValue`  
`CmCharacterInfo::getSkills`  
`CmCharacterInfo::getValueByName`  
`CmCharacterInfo::setStatValue`  
`CmCharacterInfo::onTickSignal`  
`CmCharacterInfo::sendFirstDataClient`  
`CmCharacterInfo::startSim`

### Important observed behavior

This system repeatedly asserts `"CmCharacterInfo not init"` when accessed too early.

That strongly suggests CharacterInfo is a foundational state object that must be fully initialized before most of its public surface is safe to use.

`sendFirstDataClient()` also explicitly fails if it cannot resolve the player for the current character.

### Most important interpretation

CharacterInfo is the strongest candidate for the **source of truth for a living character**.

Without CharacterInfo, later systems can still exist as objects, but they do not appear to be safe as a complete gameplay entity.

---

## 2.3 CharacterParameters

### Purpose

This system appears to load the runtime gameplay parameter block for a character.

### Most probable responsibilities

- copy persistent character data into active runtime state
- initialize health/stat-related values
- initialize flags and gameplay parameters
- bind runtime values to the current player object
- support both load and save behavior

### Recovered callable functions

`CharacterStatsAPI::CharacterParameters::_getObjectBindPoint`  
`CharacterStatsAPI::CharacterParameters::_convertCarriedMovableToDeedAndDropItToBag`  
`CharacterStatsAPI::CharacterParameters::Add_or_remove_character_listeners`  
`CharacterStatsAPI::CharacterParameters::Calc_equipment_item_effective_quality`  
`CharacterStatsAPI::CharacterParameters::Calc_hit_damage_distribution`  
`CharacterStatsAPI::CharacterParameters::Current_stance`  
`CharacterStatsAPI::CharacterParameters::LoadPlayer`  
`CharacterParameters::LoadPlayer`  
`CharacterStatsAPI::CharacterParameters::Apply_damage_to_this`  
`CharacterStatsAPI::CharacterParameters::On_shield_hit_occured`  
`CharacterStatsAPI::CharacterParameters::Ranged_time_scale`  
`CharacterStatsAPI::CharacterParameters::UrgentlyDropCarriedMovable`  
`CharacterStatsAPI::CharacterParameters::Warstance_required_by_current_ability`  
`CharacterStatsAPI::CharacterParameters::getBindPoint`  
`CharacterStatsAPI::CharacterParameters::getRallyPoint`  
`CharacterStatsAPI::CharacterParameters::getShieldArmorType`  
`CharacterStatsAPI::CharacterParameters::onArmNodeHit`  
`CharacterStatsAPI::CharacterParameters::validateCurrentTitle`  
`CharacterStatsAPI::CharacterParameters::getPossibleMountControls`  
`CharacterStatsAPI::CharacterParameters::SavePlayer`  
`CharacterParameters::SavePlayer`  
`CharacterStatsAPI::CharacterParameters::getSaveableEffects`  
`CharacterStatsAPI::CharacterParameters::isTitleValid`  
`CharacterStatsAPI::CharacterParameters::GetHpDamageSkillEffect`

### Important observed behavior

`LoadPlayer()` explicitly logs:

- `CharacterParameters::LoadPlayer() - empty cpData`
- `no character info for player %u`
- `no player equipment`
- `NetConnection have no GameConnection`
- `GameConnection have no Player`

This is extremely valuable.

It strongly suggests that CharacterParameters sits at the center of several dependencies:

- it expects valid character parameter data
- it expects valid CharacterInfo
- it may interact with equipment
- some of its paths are aware of connection/game connection/player relationships

### Most important interpretation

CharacterParameters looks like the **main gameplay-state loader**, while CharacterInfo looks like the **main character-state owner/bridge**.

That distinction matters.

A player can exist as a runtime object, but still fail if CharacterParameters cannot populate it correctly.

---

## 2.4 Player

### Purpose

The Player object appears to be the live world entity representing the character.

### Most probable responsibilities

- exist in the world as the active entity
- bind to a controlling client
- host runtime gameplay state
- participate in replication
- participate in simulation
- expose character-dependent world behavior

### Recovered callable functions directly relevant to this document

`Player::setControllingClient`  
`Player::packGMFlags`

There are many more player-side functions in the recovered file, but for this lifecycle document the most important recovered entry point is `setControllingClient()`.

### Important observed behavior

`Player::setControllingClient()` logs:

- `Player::setControllingClient() - invalid player_id`
- `Player::setControllingClient() -- can't find CharacterInfo for player %u`
- `Loaded player data from DB...`
- `can't load player`

This clearly shows that `setControllingClient()` is not just an input-binding helper.

It appears to behave like a **runtime character activation gateway**.

### Most important interpretation

This function likely performs some or all of the following:

- validate player identity
- resolve CharacterInfo
- invoke or depend on character load logic
- apply loaded state to the Player object
- transition the player into an active runtime state
- prepare the object for control and later replication

That makes it one of the most important lifecycle functions in the entire pipeline.

---

## 2.5 Inventory Manager

### Purpose

This system appears to own item definitions, inventory operations, container moves, and some player data load follow-up logic.

### Recovered callable functions

`CmPlayerManager::_loadObjectTypesFromDb`  
`CmPlayerManager::ItemMove`  
`CmPlayerManager::movePlayerInventoryTo`  
`CmPlayerManager::onDataLoaded`

### Most probable responsibilities

- load object type definitions from database tables
- load object conversions
- validate the item type registry
- handle item transfers
- handle container logic
- handle inventory/equipment interactions
- react to the moment when player data is considered loaded

### Important observed behavior

`_loadObjectTypesFromDb()` contains hard validations such as:

- `can't load objects conversions`
- `empty object type ID`
- `can't load object types`
- duplicate object type ID validation
- successful `%u types loaded` style reporting

`ItemMove()` contains concrete failure messages such as:

- `Equipment not found`
- `CmInventoryManager::ItemMove() - Can't replace item in equipment.`
- `CmInventoryManager::ItemMove() - Unknown item move`
- `CmInventoryManager::ItemMove() - Item limit in building container reached`

`movePlayerInventoryTo()` asserts:

- `object root container must be empty`

`onDataLoaded()` contains a direct `trySpawnPlayer` call path if the connection does not already have a control object.

### Most important interpretation

Inventory is **not** an isolated or early system.

It looks like a mid-pipeline system that depends on:

- valid player identity
- valid CharacterInfo
- valid runtime containers
- valid equipment context when required

It also appears to participate in spawn progression through `onDataLoaded()`.

---

## 2.6 Equipment Manager

### Purpose

This system appears to own equipment slot definitions, root equipment container binding, slot changes, and equip usage behavior.

### Recovered callable functions

`CmPlayerEquipment::_selectSlotsDB`  
`CmEquipmentManager::_loadEquipmentTypes`  
`CmEquipmentManager::_registerEquipmentType`  
`CmEquipmentContainer::_setSlot`  
`CmPlayerEquipment::applySlotChanges`  
`CmPlayerEquipment::canSetSlot`  
`CmPlayerEquipment::isSlotLocked`  
`CmPlayerEquipment::removeItemQuantity`  
`CmPlayerEquipment::setRootContainer`  
`CmPlayerEquipment::_setSlotDB`  
`CmEquipmentType::_getSkin`  
`CmEquipmentType::createFromXmlNode`  
`CmEquipmentManager::FindEquipmentTool`  
`EquipmentEvent::SendUseSlot`  
`CmEquipmentManager::_validateEquipmentType`  
`CmPlayerEquipment::checkSkills`  
`CmPlayerEquipment::getAgility`  
`CmPlayerEquipment::getConstitution`  
`CmPlayerEquipment::getMovementSoftStaminaRatio`  
`CmPlayerEquipment::getWeaponSlotItem`  
`CmPlayerEquipment::initialize`  
`EquipmentEvent::pack`  
`EquipmentEvent::unpack`  
`CmPlayerEquipment::unuseWeaponSlot`  
`CmPlayerEquipment::useWeaponSlot`

### Important observed behavior

The recovered strings show:

- `player_id is null`
- `SELECT Slot, ItemID, SkinID FROM equipment_slots WHERE CharacterID=%u`
- XML-based equipment type loading
- equipment type validation failures

This strongly suggests equipment has both:

- database-backed per-character slot state
- data-driven static type configuration

### Most important interpretation

Equipment depends on valid character identity and probably valid CharacterInfo.

It does not look connection-driven.

It looks character-driven and container-driven.

The most probable dependency chain is:

**charId → CharacterInfo → inventory/container resolution → equipment root container → slot state**

---

## 2.7 CharacterTriggers

### Purpose

This system appears to process event-driven gameplay triggers attached to character-related conditions.

### Recovered callable functions

`CharacterTriggers::NewItemInInventoryTriggerSignal::checkRequirements`  
`CharacterTriggers::Trigger::testConditions`  
`CharacterTriggers::Trigger::_loadActionFromXml`  
`CharacterTriggers::FinishedBuildingTriggerSignal::checkRequirements`  
`CharacterTriggers::EquipTriggerSignal::loadFromXml`  
`CharacterTriggers::Manager::_createStaticData`  
`CharacterTriggers::Manager::_loadTriggersXml`  
`CharacterTriggers::EquipTriggerSignal::checkRequirements`  
`CharacterTriggers::ShowHelpsTriggerAction::fireAction`  
`CharacterTriggers::NewItemInInventoryTriggerSignal::loadFromXml`  
`CharacterTriggers::Trigger::_loadSignalFromXml`

### Important observed behavior

The recovered strings show very important dependency failures:

- `Can't find player inventory`
- `Can't find player root container`
- `Can't find player id=%u connection`
- `Bad connection for player is=%u`

This is one of the strongest proofs in the recovered code that:

- some trigger paths depend on inventory and root container
- some trigger paths depend on an active connection mapping

### Most important interpretation

Triggers are not foundational.

They are downstream consumers of already-correct character state.

They can only work reliably once:

- identity is valid
- CharacterInfo is valid
- inventory/root containers are valid when required
- connection mapping is valid when required

This is crucial for modding and NPC design.

---

# 3. Full Recovered Inventory of Lifecycle-Relevant Callable Functions

This section groups the most relevant callable functions into a likely runtime graph.

## Identity and Online Registration Layer

`ConnectedPlayersManager::_notifyAll_sendInfo`  
`ConnectedPlayersManager::_notifyAll_disconnect`  
`ConnectedPlayersManager::onGmStatusChanged`  
`ConnectedPlayersManager::kickPlayer`  
`ConnectedPlayersManager::setGM`  
`ConnectedPlayersManager::banPlayer`

## Character State Layer

`CmCharacterInfo::_loadCharParamsFromDb`  
`CmCharacterInfo::_loadCarriedMovableFromDb`  
`CmCharacterInfo::_setDirty`  
`CmCharacterInfo::getInventory`  
`CmCharacterInfo::getPlayer`  
`CmCharacterInfo::sendFirstDataClient`  
`CmCharacterInfo::startSim`  
`CmCharacterInfo::onTickSignal`

## Character Parameter Load Layer

`CharacterStatsAPI::CharacterParameters::LoadPlayer`  
`CharacterParameters::LoadPlayer`  
`CharacterStatsAPI::CharacterParameters::SavePlayer`  
`CharacterParameters::SavePlayer`  
`CharacterStatsAPI::CharacterParameters::Add_or_remove_character_listeners`

## Inventory and Container Layer

`CmPlayerManager::_loadObjectTypesFromDb`  
`CmPlayerManager::ItemMove`  
`CmPlayerManager::movePlayerInventoryTo`  
`CmPlayerManager::onDataLoaded`

## Equipment Layer

`CmPlayerEquipment::_selectSlotsDB`  
`CmEquipmentManager::_loadEquipmentTypes`  
`CmPlayerEquipment::setRootContainer`  
`CmPlayerEquipment::applySlotChanges`  
`CmPlayerEquipment::initialize`  
`CmPlayerEquipment::useWeaponSlot`  
`CmPlayerEquipment::unuseWeaponSlot`

## Trigger and Event Layer

`CharacterTriggers::Trigger::testConditions`  
`CharacterTriggers::Trigger::_loadSignalFromXml`  
`CharacterTriggers::Trigger::_loadActionFromXml`  
`CharacterTriggers::NewItemInInventoryTriggerSignal::checkRequirements`  
`CharacterTriggers::EquipTriggerSignal::checkRequirements`  
`CharacterTriggers::FinishedBuildingTriggerSignal::checkRequirements`

## Player Activation Layer

`Player::setControllingClient`  
`Player::packGMFlags`

---

# 4. Most Probable Online Player Lifecycle

This is the most likely high-level execution graph for a normal online player.

## Stage 1: A live connection exists

A connection object is present.

At this point the client is online, but there may still be no valid runtime player entity and no fully loaded character state.

## Stage 2: Player identity is resolved

The system resolves a logical player identity, most likely through `playerId`, `charId`, or equivalent internal mapping.

This is the first hard gate.

If identity is bad here, later stages produce misleading secondary errors.

## Stage 3: CharacterInfo becomes available

The core resolves or creates CharacterInfo for the identified character.

This appears to be the point where the system transitions from “connection exists” to “character state exists”.

## Stage 4: Character parameter loading begins

`CharacterParameters::LoadPlayer()` appears to populate runtime player state using persistent character data.

This likely includes:

- stats
- flags
- derived values
- load-time parameters
- references to other character-bound systems

## Stage 5: Character simulation becomes active

CharacterInfo appears to transition the character into active simulation.

The logs and function model strongly suggest a sequence similar to:

- stop or clear stale simulation state if needed
- start simulation
- initialize dependent systems such as wounds
- mark the character as active

## Stage 6: Inventory and equipment become valid

Now that identity and character state are stable, inventory and equipment can safely resolve:

- item type metadata
- root inventory containers
- equipment root container
- slot state
- item-to-player runtime relationships

## Stage 7: Initial client sync occurs

`CmCharacterInfo::sendFirstDataClient()` suggests that initial character state is pushed toward the client only after CharacterInfo is valid.

This is an important stage because it separates “loaded on server” from “presentable to client”.

## Stage 8: Runtime player activation completes

`Player::setControllingClient()` appears to be the main gateway that binds loaded character state into the active world-side Player object.

The function strongly suggests:

- player identity validation
- CharacterInfo lookup
- player data load dependency
- final player activation

## Stage 9: Control object is assigned and world spawn completes

After runtime state is valid, the connection can safely control the Player object and the spawn can complete.

This is likely the point where the player becomes visible and interactive in the world.

## Stage 10: Online registry and trigger-safe state

Only after the previous stages are complete do online systems and trigger systems become truly safe.

That includes:

- ConnectedPlayersManager broadcast/update behavior
- connection-dependent triggers
- connection-dependent replication behavior
- GM/network flag packing

---

# 5. Most Probable Offline / NPC Lifecycle

A second lifecycle appears possible for NPCs or server-only characters.

## Most probable sequence

1. Create runtime Player object  
2. Assign valid identity  
3. Resolve CharacterInfo  
4. Load character parameters  
5. Resolve inventory  
6. Resolve equipment  
7. Enter simulation  
8. Spawn in world  

## Key difference

This flow appears capable of working **without a live connection**.

## What still must be valid

Even without connection, the following still likely must exist:

- valid player identity or character identity
- valid CharacterInfo
- valid character parameter load
- valid inventory/equipment context

## What may fail without connection

The following areas are likely unsafe if they assume online player state:

- connection-based trigger checks
- first-data-to-client logic
- connection-bound replication helpers
- code paths expecting a GameConnection/control object
- code paths requiring player registration in online structures

This explains why a character can exist as an NPC, but some player-specific systems still fail on it.

---

# 6. Reconstructed Load / Set / Init / Spawn Graph

This section expresses the probable execution graph in compact form.

## Core dependency graph

**Identity Resolution**  
→ **CharacterInfo Resolution**  
→ **CharacterParameters::LoadPlayer**  
→ **Simulation Start**  
→ **Inventory Resolution**  
→ **Equipment Root Binding**  
→ **Initial Client Sync**  
→ **Player::setControllingClient**  
→ **Control Object / Spawn Completion**  
→ **Connected Online State**  
→ **Connection-Dependent Triggers and Replication**

## Practical graph interpretation

If one early stage fails, every later stage may still attempt to run and produce secondary errors.

That means:

- a missing CharacterInfo can later appear as a spawn bug
- an invalid playerId can later appear as a trigger bug
- a missing connection can later appear as a replication bug
- a missing equipment root can later appear as an inventory bug

The graph is layered, and bugs cascade downward.

---

# 7. Error and Log Index

This section maps observed or recovered errors to their most probable meaning.

## `no player info found`

### Most probable origin

ConnectedPlayersManager online registry paths

### Most probable meaning

The system tried to broadcast or process an online player that is not fully registered.

### Most likely causes

- player registration never completed
- notify/disconnect path ran too early
- respawn cleanup was incomplete
- stale state remained from a previous player object

### Practical effect

Online visibility and connect/disconnect behavior becomes inconsistent.

---

## `player not found (id=%u)`

### Most probable origin

CharacterInfo first-data or update paths

### Most probable meaning

CharacterInfo attempted to resolve the runtime player for the current character, but the lookup failed.

### Most likely causes

- runtime player object not created yet
- player identity mismatch
- character state exists without corresponding world object
- load order mistake

### Practical effect

Client sync or later character-bound logic cannot proceed safely.

---

## `CmCharacterInfo not init` / `CmCharacterInfo not inited`

### Most probable origin

CharacterInfo accessor and lifecycle methods

### Most probable meaning

CharacterInfo API is being used before proper initialization.

### Most likely causes

- CharacterInfo created but not fully loaded
- code calling getters too early
- simulation/client sync attempted too early

### Practical effect

Unreliable access to inventory, stats, player binding, and runtime state.

---

## `CharacterParameters::LoadPlayer() - empty cpData`

### Most probable origin

Character parameter load stage

### Most probable meaning

The runtime attempted to load character parameters from an empty or invalid parameter source block.

### Most likely causes

- missing database payload
- invalid cpData pointer/state
- load pipeline invoked before data preparation

### Practical effect

Player object may exist but without valid gameplay state.

---

## `no character info for player %u`

### Most probable origin

CharacterParameters::LoadPlayer

### Most probable meaning

LoadPlayer was invoked for a player identity that does not resolve to CharacterInfo.

### Most likely causes

- CharacterInfo not created yet
- bad player identity
- identity/state registration mismatch

### Practical effect

Character parameter loading cannot complete.

This is one of the most important hard failures in the whole pipeline.

---

## `player_id is null`

### Most probable origin

Equipment-related paths

### Most probable meaning

Equipment logic is being asked to load or resolve state for a character with no valid identity.

### Most likely causes

- bad NPC/player setup
- equip load too early
- identity not assigned before equipment initialization

### Practical effect

Equipment cannot safely attach to the character.

---

## `Equipment not found`

### Most probable origin

Inventory move logic

### Most probable meaning

An inventory action required equipment context, but no valid equipment object or root was available.

### Most likely causes

- equipment manager not initialized
- root container not set
- item move executed before equipment load

### Practical effect

Equip/unequip and some item transfer paths fail.

---

## `CmInventoryManager::ItemMove() - Can't replace item in equipment.`

### Most probable origin

Inventory equipment-replacement path

### Most probable meaning

The system attempted to replace an equipped item, but slot replacement logic failed.

### Most likely causes

- invalid slot state
- blocked slot
- bad container/equipment synchronization
- unsupported swap scenario

### Practical effect

Equipment changes fail in-place.

---

## `CmInventoryManager::ItemMove() - Unknown item move`

### Most probable origin

Inventory move dispatch path

### Most probable meaning

The system encountered a move scenario that did not match any known movement case.

### Most likely causes

- unsupported item transfer context
- broken source/destination setup
- invalid move type
- modded code using unsupported inventory paths

### Practical effect

Move request is rejected and state may remain unchanged.

---

## `CmInventoryManager::ItemMove() - Item limit in building container reached`

### Most probable origin

Inventory move into special container context

### Most probable meaning

A move attempted to place an item into a container that has reached its configured limit.

### Practical effect

The move is blocked for capacity reasons, not because the item or player is invalid.

---

## `Can't find player inventory`

### Most probable origin

Character trigger inventory-based checks

### Most probable meaning

A trigger signal expected a valid inventory but could not resolve it.

### Most likely causes

- CharacterInfo not fully ready
- inventory not initialized yet
- trigger fired too early

### Practical effect

Inventory-based triggers cannot evaluate correctly.

---

## `Can't find player root container`

### Most probable origin

Character trigger inventory/root-container checks

### Most probable meaning

The trigger expected a valid root container and failed to find it.

### Most likely causes

- inventory root not ready
- item-container graph not initialized
- trigger timing too early

### Practical effect

Container-driven trigger logic fails.

---

## `Can't find player id=%u connection`

### Most probable origin

CharacterTriggers::Trigger::testConditions

### Most probable meaning

A trigger path required online connection mapping for a character identity, but none existed.

### Most likely causes

- player identity is invalid
- character is offline/NPC
- trigger fired before connection binding completed
- online registration incomplete

### Practical effect

Connection-dependent triggers fail repeatedly.

This is especially relevant when reusing player code for NPCs.

---

## `Bad connection for player is=%u`

### Most probable origin

Character trigger action logic

### Most probable meaning

A connection object exists or is referenced, but it is not valid for the expected trigger path.

### Practical effect

Trigger actions depending on client communication may not execute correctly.

---

## `Player::setControllingClient() - invalid player_id`

### Most probable origin

Player activation stage

### Most probable meaning

The runtime attempted to activate control for a player with an invalid identity.

### Most likely causes

- playerId never assigned
- playerId still zero
- bad binding sequence

### Practical effect

Player activation halts very early.

---

## `Player::setControllingClient() -- can't find CharacterInfo for player %u`

### Most probable origin

Player activation stage

### Most probable meaning

The player object was asked to activate for a given identity, but the core could not resolve CharacterInfo for that identity.

### Most likely causes

- CharacterInfo load missing
- activation happened too early
- identity mismatch

### Practical effect

The player object exists but cannot become a valid character.

---

## `Loaded player data from DB...`

### Most probable origin

Player activation stage after successful player data load

### Most probable meaning

Character parameter load and/or linked state resolution succeeded enough to continue activation.

### Practical effect

This is a very important “green path” log.

It strongly suggests the pipeline is moving from load into activation.

---

## `can't load player`

### Most probable origin

Player activation stage after failed load

### Most probable meaning

The runtime player could not complete the load process even though activation was attempted.

### Most likely causes

- failed data resolution
- failed CharacterInfo dependency
- failed parameter load
- internal load-stage dependency failure

### Practical effect

The Player object does not become a fully valid active character.

---

## `object root container must be empty`

### Most probable origin

Inventory transfer path

### Most probable meaning

A transfer operation expected a clean destination root container, but found existing contents.

### Practical effect

Full inventory transfer is blocked until the destination context is clean.

---

## `game connection already has a control object`

### Most probable origin

Spawn or post-load activation stage

### Most probable meaning

The system attempted to spawn or activate a new player on a connection that is already controlling something.

### Most likely causes

- duplicate spawn
- respawn without cleanup
- mod script calling spawn repeatedly

### Practical effect

Duplicate player creation or duplicate control assignment problems.

---

## `Attempting to create a player for a client that already has one!`

### Most probable origin

Spawn script/runtime guard

### Most probable meaning

Spawn was attempted again while the connection already owned a player.

### Most likely causes

- duplicate script call
- incorrect respawn handling
- race condition between stop/restart logic

### Practical effect

One of the strongest indicators of bad respawn order or double-spawn mistakes.

---

## `Player::packGMFlags() -- missing GameConnection ...`

### Most probable origin

Player replication/network packing

### Most probable meaning

A replicated or packed player-related path expected a GameConnection and failed to find it.

### Most likely causes

- partial spawn completion
- ghosting or packing before connection binding completed
- stale replicated object from an earlier player state

### Practical effect

Network state becomes inconsistent even if spawn looked successful earlier.

---

## `NetConnection have no GameConnection`

### Most probable origin

Character parameter logic

### Most probable meaning

A code path expected a GameConnection-compatible wrapper for the current network object and failed.

### Practical effect

Any logic relying on gameplay-specific connection state cannot continue.

---

## `GameConnection have no Player`

### Most probable origin

Character parameter logic

### Most probable meaning

A GameConnection exists, but it has no active Player object attached.

### Most likely causes

- early load path
- failed spawn
- disconnected runtime object
- broken respawn transition

### Practical effect

Connection exists, but no valid world-side player is bound.

---

# 8. Spawn and Respawn Model

## Normal spawn model

A likely successful spawn sequence is:

1. validate connection state  
2. validate identity  
3. resolve CharacterInfo  
4. load character parameters  
5. start or restore simulation  
6. initialize inventory and equipment  
7. send initial client data  
8. activate Player through controlling-client path  
9. assign control object  
10. finalize world spawn  
11. expose player to online systems  
12. allow connection-dependent triggers to operate safely  

## Respawn dangers

Respawn appears highly sensitive to stale state.

The recovered logs strongly suggest the following are dangerous:

- spawning when the connection already controls a player
- leaving stale tracked character state behind
- leaving old network ownership behind
- allowing trigger and replication systems to observe half-initialized state

## Practical respawn rule

A connection should not receive a new active player until the previous one is fully released from:

- world control
- online registry
- replicated ownership
- tracked character state
- equipment/inventory-dependent runtime bindings

---

# 9. Practical Modding Rules

## Rule 1

Never treat connection existence as proof that the character is fully valid.

A connection is only the beginning of the lifecycle.

## Rule 2

Never treat the Player object alone as proof that the character is fully valid.

A Player object may exist before the character is truly loaded.

## Rule 3

CharacterInfo is the most important dependency in the recovered design.

If CharacterInfo is missing, many later errors are only secondary noise.

## Rule 4

Do not initialize equipment before identity and CharacterInfo are valid.

Equipment appears to depend on character-bound container context.

## Rule 5

Do not fire inventory-dependent or connection-dependent triggers too early.

Triggers appear to be downstream consumers of already-correct state.

## Rule 6

For NPCs, separate “character validity” from “online validity”.

An NPC may be character-valid but intentionally connection-less.

## Rule 7

During respawn, clear old control and tracking state before creating a new player for the same connection.

Most duplicate spawn errors strongly point to stale state.

---

# 10. Most Probable Final Architectural Conclusion

The recovered core most likely uses a layered model:

**Connection Layer**  
creates online presence but not full character validity

**Identity Layer**  
determines which logical player/character is being activated

**CharacterInfo Layer**  
makes the character meaningful to the core

**CharacterParameters Layer**  
loads gameplay state into runtime form

**Inventory and Equipment Layer**  
binds item state and gear state to the character

**Player Runtime Layer**  
places the character into a live world object

**Online/Replication Layer**  
makes that world object visible and controllable online

**Trigger Layer**  
reacts safely only after the earlier layers are valid

This means the most important rule in the entire recovered design is:

**valid identity must lead to valid CharacterInfo before the rest of the core can be trusted**

If that step fails, the system can still continue producing objects, logs, and side effects, but most of them become secondary symptoms rather than the true root cause.

---

# 11. Short Diagnostic Checklist

When debugging a broken player lifecycle, check in this order:

1. Does the player have a valid non-zero identity?  
2. Does CharacterInfo exist for that identity?  
3. Did CharacterParameters::LoadPlayer succeed?  
4. Did simulation actually start?  
5. Did inventory initialize?  
6. Did equipment root/container bind correctly?  
7. Did sendFirstDataClient run successfully?  
8. Did Player::setControllingClient succeed?  
9. Does the connection already have another control object?  
10. Is the player registered in online/connected player structures?  
11. Are triggers being fired before connection-dependent state is valid?  
12. Is replication/GM packing observing stale or incomplete connection state?  

---

# 12. Final Summary

The recovered core is not best understood as:

**connection → spawn**

It is better understood as:

**identity → CharacterInfo → gameplay state load → simulation → inventory/equipment → player activation → online state**

That is the key mental model for future maintenance, debugging, modding, and reconstruction work.
