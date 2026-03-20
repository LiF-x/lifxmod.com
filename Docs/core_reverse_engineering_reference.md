# Core Reverse Engineering Reference
## Character Loading, Connection Binding, Inventory, Equipment, Spawn, and Error Model

## Document Purpose

This document describes **externally observable runtime behavior** of the game core based on:

- recovered callable function names
- runtime logs
- exposed scripting behavior
- practical modding experiments
- known Torque3D runtime patterns

It is intended as a **reverse-engineering reference**, not as authoritative source-level documentation of the original closed-core implementation.

The goal is to help reconstruct a usable mental model of the system for:

- debugging
- maintenance
- modding
- future documentation work

This document is not a raw decompilation dump.

It is also not a claim of exact original internal architecture.

It is a structured interpretation of observed runtime behavior.

---

## Evidence Model

### Confirmed

Behavior directly observed in:

- runtime logs
- recovered callable functions
- exposed script/runtime interfaces
- practical experiments

### Inferred

Behavior strongly suggested by repeated observations and known Torque3D patterns, but not directly visible in original source code.

### Unknown

Internal implementation details, ownership boundaries, hidden manager relationships, and side effects that are not directly observable.

---

## Scope Limitation

This document does **not** claim full knowledge of:

- original class ownership boundaries
- hidden manager internals
- exact internal data layouts
- whether a recovered function is a primary implementation, helper, wrapper, or facade
- all side effects triggered by deeply nested runtime calls

Where such details are not directly visible, they are described as inferred or unknown.

---

# 1. Core Runtime Model

## Confirmed

Observed runtime behavior shows that:

- a live connection alone is not enough to guarantee a valid fully playable character
- a runtime `Player` object alone is not enough to guarantee a valid fully playable character
- some character-backed runtime state must exist before full activation succeeds
- later runtime systems may still execute even after early character-state failure

## Inferred

A useful practical model of the core is:

**identity → character-backed runtime state → player world object → online/connection-facing systems**

This suggests the runtime does **not** behave as a purely connection-driven system.

## Unknown

It is not fully proven how much of this model is implemented through direct ownership versus lookup/coordination between hidden subsystems.

---

# 2. Main Systems and Their Probable Roles

## 2.1 ConnectedPlayersManager

### Confirmed

Recovered callable functions include:

`ConnectedPlayersManager::_notifyAll_sendInfo`  
`ConnectedPlayersManager::_notifyAll_disconnect`  
`ConnectedPlayersManager::onGmStatusChanged`  
`ConnectedPlayersManager::kickPlayer`  
`ConnectedPlayersManager::setGM`  
`ConnectedPlayersManager::banPlayer`  
`YoConnectedPlayerEvent::pack`  
`YoConnectedPlayerEvent::unpack`

### Inferred

This system appears to be related to:

- online player registry
- online visibility or broadcast updates
- GM/admin online actions
- connect/disconnect style propagation

### Safe interpretation

This system does **not** appear to be the primary character creation system.

It more likely behaves as a **post-activation online-state layer** that expects valid player state to already exist.

### Unknown

The exact ownership relationship between this system and lower-level connection/registration structures is not directly visible.

---

## 2.2 CharacterInfo

### Confirmed

Recovered callable functions include:

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

Runtime observations also support the existence of:

- `CmCharacterInfo::stopSim(...)`
- `CmCharacterInfo::startSim(...)`
- `CmCharacterInfo::sendFirstDataClient()`

### Confirmed observed behavior

CharacterInfo-related paths fail when accessed too early or when expected backing state is missing.

This strongly indicates that CharacterInfo-backed state is part of valid character activation.

### Inferred

CharacterInfo appears to act as a bridge between:

- character identity
- persistent/runtime character state
- simulation state
- client-facing initialization
- runtime player linkage

### Safe interpretation

CharacterInfo is one of the strongest visible candidates for the required character-backed runtime layer.

### Unknown

It is not directly proven whether CharacterInfo owns all gameplay state itself, or whether it coordinates access to other hidden systems.

It is also not directly proven whether inventory/equipment are owned by CharacterInfo or only resolved through it.

---

## 2.3 CharacterParameters

### Confirmed

Recovered callable functions include:

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

Observed error/log strings include:

- `CharacterParameters::LoadPlayer() - empty cpData`
- `no character info for player %u`
- `no player equipment`
- `NetConnection have no GameConnection`
- `GameConnection have no Player`

### Confirmed observed behavior

`LoadPlayer()` is part of real activation and load failure paths.

It clearly depends on more than just a raw `Player` object.

### Inferred

CharacterParameters appears to be one of the main gameplay-state load layers used to populate runtime character state after valid character-backed resolution.

### Safe interpretation

A `Player` object may exist while CharacterParameters load still fails.

That means:

**player object existence != successful gameplay-state load**

### Unknown

The exact internal separation between CharacterParameters and CharacterInfo remains hidden.

---

## 2.4 Player

### Confirmed

Recovered functions directly relevant here include:

`Player::setControllingClient`  
`Player::packGMFlags`

Observed runtime behavior also shows that a `Player` can exist with:

- fallback/default datablock
- invalid or zero character ID
- world presence without valid full character activation

### Confirmed observed behavior

`Player::setControllingClient()` is clearly not just a trivial input-binding helper.

Observed messages include:

- `Player::setControllingClient() - invalid player_id`
- `Player::setControllingClient() -- can't find CharacterInfo for player %u`
- `Loaded player data from DB...`
- `can't load player`

### Inferred

`Player::setControllingClient()` appears to be one of the major activation gates where:

- identity is validated
- character-backed state is resolved
- gameplay-state loading proceeds
- the object becomes playable or fails

### Safe interpretation

A world `Player` object can exist without being a valid fully initialized character.

### Unknown

It is not proven whether the `Player` object stores all gameplay state itself or primarily acts as the world-side representation of character-backed state.

---

## 2.5 Inventory Manager

### Confirmed

Recovered callable functions include:

`CmPlayerManager::_loadObjectTypesFromDb`  
`CmPlayerManager::ItemMove`  
`CmPlayerManager::movePlayerInventoryTo`  
`CmPlayerManager::onDataLoaded`

Observed strings include:

- `can't load objects conversions`
- `empty object type ID`
- `can't load object types`
- duplicate object type ID validation
- `Equipment not found`
- `CmInventoryManager::ItemMove() - Can't replace item in equipment.`
- `CmInventoryManager::ItemMove() - Unknown item move`
- `CmInventoryManager::ItemMove() - Item limit in building container reached`
- `object root container must be empty`

### Confirmed observed behavior

Inventory-related logic clearly includes:

- object type loading
- move dispatch
- container restrictions
- equipment-dependent move paths

### Inferred

Inventory appears to be a dependent subsystem that expects valid character-bound container context.

### Safe interpretation

Inventory should not currently be documented as a fully proven early foundational stage of activation unless direct trace evidence is added.

### Unknown

The exact point where inventory becomes valid during character activation is not directly proven.

---

## 2.6 Equipment Manager

### Confirmed

Recovered callable functions include:

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

Observed strings include:

- `player_id is null`
- `SELECT Slot, ItemID, SkinID FROM equipment_slots WHERE CharacterID=%u`

### Confirmed observed behavior

Equipment clearly has both:

- database-backed per-character slot state
- data-driven/static equipment type configuration

### Inferred

Equipment appears to depend on valid character identity and valid character-bound container state.

### Safe interpretation

Equipment currently looks more character-driven and container-driven than connection-driven.

### Unknown

The exact load boundary between equipment initialization and inventory/CharacterInfo/LoadPlayer remains unproven.

---

## 2.7 CharacterTriggers

### Confirmed

Recovered callable functions include:

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

Observed strings include:

- `Can't find player inventory`
- `Can't find player root container`
- `Can't find player id=%u connection`
- `Bad connection for player is=%u`

### Confirmed observed behavior

Different trigger paths can require:

- valid inventory
- valid root container
- valid connection mapping

### Inferred

Triggers appear to be downstream consumers of already valid runtime state rather than foundational lifecycle systems.

### Safe interpretation

Some trigger paths are likely offline-safe while others are explicitly connection-dependent.

### Unknown

The exact boundary between offline-safe and online-only trigger behavior remains undocumented.

---

# 3. Full Recovered Inventory of Lifecycle-Relevant Callable Functions

This section groups the most relevant callable functions into a practical runtime graph.

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

# 4. Practical Online Player Lifecycle

This is a **practical runtime model**, not a source-level proof of exact internal call order.

## Stage 1: A live connection exists

A connection object is present.

At this point the client may still have:

- no valid runtime player
- no valid character-backed activation
- no fully loaded state

## Stage 2: Identity is resolved

Some player/character identity must be resolved.

If identity is bad here, later stages may still run and produce misleading secondary failures.

## Stage 3: Character-backed runtime state becomes available

Successful activation strongly appears to require valid CharacterInfo-backed resolution.

This is one of the strongest practical conclusions currently supported by logs and recovered errors.

## Stage 4: Character parameter loading begins

`CharacterParameters::LoadPlayer()` appears as part of successful activation and failure paths.

This suggests runtime gameplay state is loaded only after valid backing exists.

## Stage 5: Character simulation becomes active

Observed valid activation behavior includes:

- simulation start
- dependent systems such as wounds becoming active

This suggests simulation-related subsystems depend on successful activation progression.

## Stage 6: Initial client sync occurs

`CmCharacterInfo::sendFirstDataClient()` suggests that character state is pushed toward the client only after character-backed runtime state is valid enough to present.

## Stage 7: Runtime player activation completes

`Player::setControllingClient()` appears to be one of the final activation gates where loaded/runtime-valid character state becomes attached to the active world-side `Player`.

## Stage 8: World/control state and online behavior stabilize

Only after the previous stages succeed do later systems become safer:

- online visibility/state propagation
- connection-dependent triggers
- replication/packing paths
- GM/network flag behavior

---

# 5. Most Probable Offline / NPC Lifecycle

This section remains more tentative than the online lifecycle.

## Inferred sequence

A character-like entity may potentially follow a reduced path such as:

1. create or obtain runtime player-like object  
2. assign valid identity  
3. resolve character-backed state  
4. load character parameters  
5. resolve inventory/equipment if needed  
6. enter simulation  
7. appear in world  

## Safe conclusion

A character-like runtime entity may exist without a live playable online connection.

## Important limitation

This does **not** mean all player systems are safe for NPC/offline entities.

Recovered trigger errors strongly suggest that some systems explicitly require valid connection mapping.

---

# 6. Reconstructed Load / Set / Init / Spawn Graph

This graph is a **practical inferred dependency model**, not a source-level proof.

## Practical dependency graph

**Identity Resolution**  
→ **Character-Backed Runtime Resolution**  
→ **CharacterParameters::LoadPlayer**  
→ **Simulation Start**  
→ **Inventory/Equipment Validity**  
→ **Initial Client Sync**  
→ **Player::setControllingClient**  
→ **Control Object / Spawn Completion**  
→ **Connected Online State**  
→ **Connection-Dependent Triggers and Replication**

## Practical interpretation

If one early stage fails, later stages may still attempt to run and produce secondary errors.

That means:

- missing CharacterInfo may later look like a spawn bug
- invalid identity may later look like a trigger bug
- missing connection may later look like a replication bug
- missing equipment context may later look like an inventory bug

---

# 7. Error and Log Index

This section maps observed or recovered errors to their practical meaning.

## `no player info found`

### Inferred origin

Likely online registry / connected-player state behavior

### Safe interpretation

A system tried to operate on a player as if it were fully registered, but earlier activation/registration was incomplete.

### Unknown

Exact internal manager ownership remains unproven.

---

## `player not found (id=%u)`

### Inferred origin

Likely character-to-runtime-player resolution path

### Safe interpretation

Character-backed state expected a valid world-side player and could not resolve it.

---

## `CmCharacterInfo not init` / `CmCharacterInfo not inited`

### Confirmed practical meaning

CharacterInfo API is being accessed before valid initialization has completed.

### Safe interpretation

Character-backed runtime state is foundational enough that early access causes hard failure.

---

## `CharacterParameters::LoadPlayer() - empty cpData`

### Confirmed practical meaning

Runtime attempted to load character parameters from invalid or empty character parameter data.

### Safe interpretation

Activation/load was attempted without valid prepared input state.

---

## `no character info for player %u`

### Confirmed practical meaning

A load path attempted to proceed without valid CharacterInfo-backed resolution.

### Safe interpretation

This is one of the strongest visible failure signals in the lifecycle.

---

## `player_id is null`

### Confirmed practical meaning

An equipment-related path expected valid character identity and did not receive it.

---

## `Equipment not found`

### Confirmed practical meaning

An inventory/equipment-related path required valid equipment context and did not find it.

---

## `CmInventoryManager::ItemMove() - Can't replace item in equipment.`

### Confirmed practical meaning

An equipment replacement path failed because expected equipment/slot state was not valid for the requested operation.

---

## `CmInventoryManager::ItemMove() - Unknown item move`

### Confirmed practical meaning

Inventory move dispatch encountered an unsupported or invalid movement scenario.

---

## `CmInventoryManager::ItemMove() - Item limit in building container reached`

### Confirmed practical meaning

The move failed because of container capacity/limit rules.

---

## `Can't find player inventory`

### Confirmed practical meaning

An inventory-dependent trigger or runtime path could not resolve player inventory.

### Safe interpretation

Inventory is not universally safe at all lifecycle stages.

---

## `Can't find player root container`

### Confirmed practical meaning

A root-container-dependent path fired before valid container state was available.

---

## `Can't find player id=%u connection`

### Confirmed practical meaning

A trigger or runtime path required valid connection mapping and did not find it.

### Safe interpretation

Some character systems are explicitly connection-dependent.

---

## `Bad connection for player is=%u`

### Confirmed practical meaning

A connection reference existed but was invalid for the expected operation.

---

## `Player::setControllingClient() - invalid player_id`

### Confirmed practical meaning

Player activation/control binding was attempted with invalid identity.

---

## `Player::setControllingClient() -- can't find CharacterInfo for player %u`

### Confirmed practical meaning

Control binding could not proceed because valid CharacterInfo-backed resolution was missing.

### Safe interpretation

Control binding is part of the activation boundary, not merely a harmless helper.

---

## `Loaded player data from DB...`

### Confirmed practical meaning

A valid activation/load path succeeded far enough to report real data load completion.

---

## `can't load player`

### Confirmed practical meaning

Player activation/load was attempted but did not complete successfully.

---

## `object root container must be empty`

### Confirmed practical meaning

A transfer/container operation expected a clean destination root container and failed that requirement.

---

## `game connection already has a control object`

### Confirmed practical meaning

A new activation/spawn attempt was made while the connection still controlled another object.

---

## `Attempting to create a player for a client that already has one!`

### Confirmed practical meaning

Spawn was invoked while the client already had an active player.

### Practical implication

Any respawn, bridge, or swap experiment must account for prior player ownership.

---

## `Player::packGMFlags() -- missing GameConnection ...`

### Confirmed practical meaning

A replication/packing path expected a valid GameConnection and failed.

### Safe interpretation

A spawn that appears partially successful may still be network-invalid.

---

## `NetConnection have no GameConnection`

### Confirmed practical meaning

A gameplay-specific connection-dependent path received insufficient valid connection backing.

---

## `GameConnection have no Player`

### Confirmed practical meaning

A GameConnection existed but lacked an active Player object when gameplay logic expected one.

---

# 8. Spawn and Respawn Model

## Practical normal spawn model

A likely successful activation path includes:

1. valid connection state  
2. valid identity  
3. valid character-backed resolution  
4. character parameter load  
5. simulation start  
6. inventory/equipment becoming valid  
7. initial client sync  
8. controlling-client activation  
9. stable world/control state  
10. later online/trigger-safe behavior  

## Respawn dangers

Observed behavior strongly suggests respawn is highly sensitive to stale state, especially when:

- the connection already owns a player
- tracking state still exists
- simulation has already started
- replication observes half-valid objects

## Practical respawn rule

Do not attempt to create or bind a new active player for a connection until old control/tracking/simulation state is fully cleared.

---

# 9. Practical Modding Rules

## Rule 1

Do not treat connection existence as proof of valid character activation.

## Rule 2

Do not treat `Player` object existence as proof of valid playable character state.

## Rule 3

CharacterInfo-backed resolution is one of the most important currently visible lifecycle dependencies.

## Rule 4

Do not overstate inventory/equipment load order unless direct proof is available.

## Rule 5

Do not fire connection-dependent or inventory-dependent logic too early.

## Rule 6

Treat NPC/offline character validity separately from online/player validity.

## Rule 7

During respawn or character swap experiments, clear prior control/activation state before attempting new player creation.

---

# 10. Most Probable Final Architectural Conclusion

The safest current interpretation is that the recovered core behaves like a layered runtime model:

**Connection Layer**  
provides online presence, but not full character validity

**Identity Layer**  
determines which logical character is being targeted

**Character-Backed Runtime Layer**  
makes a character valid to activation logic

**Gameplay Load Layer**  
loads runtime gameplay state

**Inventory / Equipment Layer**  
attaches dependent item/slot/container state

**Player Runtime Layer**  
provides the live world object

**Online / Replication Layer**  
makes that object controllable and visible online

**Trigger Layer**  
becomes safe only after earlier dependencies are valid

The strongest practical rule currently supported by evidence is:

**valid identity must resolve to valid character-backed runtime state before a Player object can become a real fully initialized character**

If that step fails, the system may still continue producing objects, logs, and side effects, but many of them are secondary symptoms rather than the root cause.

---

# 11. Short Diagnostic Checklist

When debugging a broken player lifecycle, check in this order:

1. Does the player have a valid non-zero identity?  
2. Does valid CharacterInfo-backed resolution exist for that identity?  
3. Did `CharacterParameters::LoadPlayer` succeed?  
4. Did simulation actually start?  
5. Did inventory initialize or become valid where required?  
6. Did equipment/root-container-dependent state become valid where required?  
7. Did `sendFirstDataClient` run successfully?  
8. Did `Player::setControllingClient` succeed?  
9. Does the connection already control another player/object?  
10. Are trigger paths firing before connection-dependent state is valid?  
11. Is replication/GM packing observing stale or incomplete connection/player state?  

---

# 12. Final Summary

The recovered core is not best understood as:

**connection → spawn**

A more accurate practical model is:

**identity → character-backed runtime resolution → gameplay-state load → simulation → player activation → stable online state**

This document should therefore be read as a reverse-engineered runtime reference based on observable behavior, not as a full reconstruction of the original closed-core source architecture.

---

## Footnote

This document was assembled from reverse-engineering notes, runtime experiments, and edited technical drafting assistance. It should be judged by the included evidence and examples, not as official source-level documentation.
