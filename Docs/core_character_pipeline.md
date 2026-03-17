# Core Character Lifecycle Documentation

## Overview

This document describes the probable runtime behavior of the character core in a Torque3D-based multiplayer game server.

It is written as an architectural guide for:

- understanding the player lifecycle
- understanding how character data is loaded
- understanding how inventory and equipment are attached
- understanding how the world spawn pipeline works
- understanding what can fail during modding, NPC work, or connection handling

This document is intentionally written as a clean system description, not as a source recovery report.

---

## Core Design Philosophy

The core appears to be **character-state driven**, not purely connection-driven.

The most likely dependency chain is:

**playerId → CharacterInfo → character parameters → inventory/equipment → runtime player object → world**

A network connection is important for online player control and client synchronization, but it does not appear to be the true source of gameplay state.

The central source of gameplay state is most likely **CharacterInfo**.

---

## Main Runtime Components

## ConnectedPlayersManager

### Purpose

This system appears to manage the set of active connected players visible to the server and to other clients.

### Probable responsibilities

- track which players are currently registered as connected
- map active player identity to connection-related runtime state
- notify other players when a player appears or disappears
- propagate status changes such as connect, disconnect, GM state, or visibility state

### Important behavioral clue

The manager clearly expects valid player registration before it can broadcast state. If it cannot find player info, it fails with a hard assertion-style error.

### Probable role in the lifecycle

This is **not** the system that creates a character.  
It looks more like the system that assumes the character is already valid and then exposes that character to the rest of the online world.

### Practical meaning

If this manager reports missing player info, the failure usually happened earlier in the pipeline.

---

## CharacterInfo

### Purpose

CharacterInfo appears to be the central persistent/runtime bridge for a character.

### Probable responsibilities

- represent the identity of a character
- hold the active `playerId` / `charId`
- link the character to runtime player state
- own or resolve inventory and equipment context
- manage simulation state transitions
- send initial character state to the client
- serve as the bridge between data loaded from the database and the live player object in the world

### Strong lifecycle indicators

The character pipeline strongly suggests methods or stages equivalent to:

- stop simulation
- load player data
- start simulation
- initialize wounds or health systems
- send first data to the client
- continue into world control/spawn

### Practical meaning

CharacterInfo is likely the object that makes a character “real” to the server.  
Without it, the rest of the systems may still exist as objects, but they do not have valid gameplay identity.

---

## CharacterParameters

### Purpose

This system appears to load the actual gameplay parameter block for a character.

### Probable responsibilities

- load character values from database structures
- copy persistent values into the runtime player state
- initialize stats, flags, state fields, and derived runtime properties
- prepare the player to enter simulation

### Practical meaning

This looks like the real “load my character from DB” layer.

CharacterInfo likely resolves the character and world context, while CharacterParameters likely loads the actual gameplay values into the player runtime object.

### Important note

If CharacterParameters fails, the player object may exist, but the character is still not fully initialized.

---

## Player

### Purpose

The Player object appears to be the live in-world representation of a character.

### Probable responsibilities

- represent the active world entity
- bind to or unbind from a controlling connection
- load runtime state for the linked character
- participate in world replication and control
- respawn, update, and synchronize with the client

### Critical behavior

`setControllingClient()` appears to be much more than a simple input binding function.

It likely does all or most of the following:

- resolve the effective player identity from the connection
- verify that the player identity is valid
- resolve the linked CharacterInfo
- trigger character parameter loading
- finalize runtime initialization
- update inventory/equipment-related visual or runtime state
- make the object ready for network/world control

### Practical meaning

This function behaves like a **character activation gateway**.

If this stage fails, the world may have a Player object, but it will not behave like a fully loaded player character.

---

## Inventory Manager

### Purpose

This system appears to own the runtime logic for item movement and inventory interaction.

### Probable responsibilities

- load object type definitions from the database
- maintain item metadata and item type behavior
- move items between containers
- move items to or from equipment
- trigger gameplay events when items change
- support full inventory transfers between contexts

### Structural meaning

Inventory does not look isolated.  
It appears to depend on already valid character state.

The manager seems to assume that:

- the player identity is valid
- CharacterInfo is already resolved
- inventory containers already exist
- equipment root access is already possible

### Practical meaning

Inventory is not the first thing to initialize.  
It sits after character identity and character state become valid.

---

## Equipment Manager

### Purpose

This system appears to handle equipment containers and item attachment to the character.

### Probable responsibilities

- resolve the correct inventory container used as equipment root
- attach gear to the live character
- enforce slot logic and replacement logic
- interact with inventory during equip/unequip operations

### Important dependency

Equipment appears to be dependent on:

**charId → CharacterInfo → inventory/container → equipment root**

### Practical meaning

Equipment is not loaded directly from connection state and not directly from a naked Player object.  
It most likely depends on CharacterInfo being valid first.

---

## CharacterTriggers

### Purpose

This system appears to evaluate gameplay conditions and run logic in response to character-related signals.

### Probable responsibilities

- test conditions for gameplay triggers
- process player-dependent or signal-dependent state transitions
- react to events like item acquisition, status changes, or world activity

### Important dependency

This system appears to need a valid mapping from `playerId` to an active connection in at least some trigger paths.

### Practical meaning

A character may exist without a live connection, but not every trigger path can safely run in that state.

This is especially important for NPCs or offline-loaded characters.

---

## Probable Full Online Player Pipeline

The most likely full lifecycle for a normal online player is:

### Stage 1: Connection exists

A network client is accepted and a valid connection object is created.

At this stage, the player is connected, but not yet necessarily spawned or fully initialized as a character.

### Stage 2: Player identity is resolved

The system resolves the logical player identity, probably through `playerId`, `charId`, or both.

This is the first critical gate.

If identity is invalid here, later systems fail in confusing ways.

### Stage 3: CharacterInfo is resolved or created

The core resolves the character state object associated with that identity.

This is where the pipeline becomes character-driven instead of connection-driven.

### Stage 4: Character parameters are loaded

The gameplay parameter block is loaded into the runtime character/player object.

This likely includes:

- character data
- status values
- persistent configuration
- runtime flags
- simulation-relevant state

### Stage 5: Simulation state is prepared

The system appears to stop old simulation state if needed, then start fresh simulation state for the character.

This likely includes:

- resetting stale state
- binding runtime subsystems
- enabling wounds/health/other live systems

### Stage 6: Inventory and equipment become available

Once CharacterInfo and character parameters are valid, the runtime can safely resolve:

- inventory containers
- equipment root container
- equipped items
- item-driven runtime state

### Stage 7: Initial client data is sent

The system sends the first synchronized character state to the client.

This likely means the character is now considered sufficiently valid for online presentation.

### Stage 8: Control object is assigned

The connection is linked to the live Player object as its control object.

At this point, the player is effectively active in the world.

### Stage 9: Spawn completes

The player is spawned in the world and becomes visible/relevant for replication.

### Stage 10: ConnectedPlayersManager visibility/broadcast layer activates

Now that the character is truly active, online broadcast and registry systems can safely expose that player to other players.

### Stage 11: CharacterTriggers and dependent systems become safe

Only after the identity, CharacterInfo, and connection mapping are correct do connection-dependent trigger systems become safe to use.

---

## Probable Offline / NPC Pipeline

A second, distinct flow appears possible for NPC-like or server-only characters.

### Probable NPC flow

1. Create the Player runtime object  
2. Assign a valid character identity  
3. Resolve CharacterInfo  
4. Load character parameters  
5. Resolve inventory  
6. Attach equipment  
7. Enter simulation  
8. Spawn in world  

### Key difference from normal players

This flow may work **without a live client connection**.

### What still must be valid

Even without a connection, the following still likely must exist:

- valid `playerId` or `charId`
- valid CharacterInfo
- valid parameter load
- valid inventory/equipment resolution

### What may break without connection

The following systems may fail or behave incorrectly if they expect a live connection:

- connection-based trigger evaluation
- first-data-to-client paths
- connection-dependent replication logic
- any logic that expects a control object or active player registry entry

---

## Probable Spawn Logic

The logs strongly suggest that successful spawning is not a single step, but a chained sequence.

A correct spawn appears to look like this:

1. prevent duplicate active player creation  
2. prepare or replace runtime player object  
3. stop old simulation if necessary  
4. load character parameters  
5. start simulation  
6. initialize dependent character systems  
7. send initial data to client  
8. set control object  
9. confirm spawn in the world  

### Important modding implication

If you force a spawn too early, before CharacterInfo or character parameters are valid, you may get:

- default datablock fallback
- missing player info errors
- missing connection errors
- partially initialized world players
- broken trigger execution

---

## Probable Inventory and Equipment Lifecycle

Inventory and equipment appear to be loaded after character state is valid, not before.

### Likely order

1. character identity resolved  
2. CharacterInfo resolved  
3. character parameters loaded  
4. inventory manager resolves character inventory containers  
5. equipment manager resolves equipment root container  
6. equipped items become part of active runtime state  

### Important implication

If you are modding load order, do not treat equipment or inventory as an isolated early-stage system.

They appear to depend on previous successful character initialization.

---

## Error Interpretation Guide

## Error: `can't find CharacterInfo for player 0`

### Probable meaning

The runtime is trying to load or activate a player using an invalid identity.

### Most likely causes

- `playerId` was never initialized
- `playerId` was set too late
- CharacterInfo was never created or never registered
- character loading was attempted before identity resolution finished

### Consequences

- Player fallback behavior
- default datablock selection
- load failure in `setControllingClient()`
- inventory/equipment failure later in the chain

---

## Error: `Can't find player id=0 connection`

### Probable meaning

A system that expects an online player connection was executed for an invalid or connection-less player.

### Most likely causes

- trigger executed too early
- NPC path accidentally entered connection-dependent logic
- online registration never completed
- player identity is still zero

### Consequences

- repeated trigger failures
- invalid online-state logic
- broken client-specific gameplay paths

---

## Error: `no player info found`

### Probable meaning

The online broadcast/registry layer was asked to operate on a player that has not been correctly registered in active player state.

### Most likely causes

- ConnectedPlayersManager invoked too early
- incomplete player registration
- disconnect or notify path executed for a partially initialized character
- stale or duplicate state during respawn

### Consequences

- missing connect/disconnect visibility updates
- invalid online state propagation
- inconsistent “player exists but is not recognized” situations

---

## Error: `Equipment not found`

### Probable meaning

Inventory logic attempted to perform an operation that depends on equipment state, but the equipment root or context was not available.

### Most likely causes

- equipment manager not initialized
- root container not attached
- CharacterInfo resolved too late
- inventory action executed before equip context was ready

### Consequences

- equip/unequip failures
- invalid container moves
- item transfer failures involving gear

---

## Error: `game connection already has a control object`

### Probable meaning

The system attempted to spawn or activate a new player on a connection that is already controlling one.

### Most likely causes

- duplicate spawn request
- missing cleanup before respawn
- retry path executed without resetting the old runtime object

### Consequences

- duplicate spawn attempts
- stale state tracking
- possible mismatch between old and new world objects

---

## Error: `Attempting to create a player for a client that already has one!`

### Probable meaning

A new player creation path ran while the connection still owned an existing player object.

### Most likely causes

- mod script calling spawn twice
- respawn path overlapping with existing player lifecycle
- failure to stop or destroy the old player before creating the new one

### Consequences

- duplicate runtime state
- repeated tracking warnings
- connection/object mismatch
- later replication errors

---

## Error: `Player::packGMFlags() -- missing GameConnection ...`

### Probable meaning

The player or a related runtime object entered a network packing path that expected a valid connection context but did not find one.

### Most likely causes

- object ghosting before connection binding completed
- stale replicated object still tied to previous state
- spawn completed partially but network ownership is inconsistent

### Consequences

- bad replication state
- incorrect player visibility/state flags
- networking inconsistencies after spawn or respawn

---

## Modding Guidelines

## If you are spawning a normal player

Make sure this order is respected:

1. connection exists  
2. valid player identity exists  
3. CharacterInfo exists  
4. character parameters load successfully  
5. inventory/equipment resolve successfully  
6. initial client sync is sent  
7. control object is assigned  
8. only then allow trigger-heavy or network-heavy systems to rely on the player  

## If you are spawning an NPC or server-only character

Make sure this order is respected:

1. valid character identity exists  
2. CharacterInfo exists  
3. character parameters load successfully  
4. inventory/equipment resolve successfully  
5. character enters simulation  
6. world spawn occurs  

Avoid:

- connection-dependent triggers
- client-first-data logic
- code paths that assume an online control object

## If you are debugging a broken spawn

Check these in order:

1. is `playerId` valid and non-zero  
2. does CharacterInfo exist for that identity  
3. did character parameters actually load  
4. did simulation start  
5. did inventory/equipment initialize  
6. did first client data run successfully  
7. does the connection already have a control object  
8. is the player registered in connected player state  

---

## Most Probable Architectural Conclusion

The core appears to follow this model:

### Online player

**Connection → identity resolution → CharacterInfo → character parameter load → simulation start → inventory/equipment attach → first client sync → control binding → world spawn → trigger-safe online behavior**

### NPC / offline character

**Identity resolution → CharacterInfo → character parameter load → simulation start → inventory/equipment attach → world spawn**

This means the core is most likely designed around a strong separation between:

- persistent/character state
- live world entity state
- online connection state

That separation is why a character can probably exist without a connection, but many online systems cannot safely interact with that character until connection mapping is valid.

---

## Final Summary

The probable core rule is:

**Character state must be valid before world state can be trusted, and world state must be valid before online systems can safely interact with the player.**

The single most important dependency is:

**valid identity → valid CharacterInfo**

If that step fails, everything else becomes secondary error noise.

That includes:

- default datablock fallback
- missing connection lookups
- missing player info
- equipment failures
- broken trigger execution
- partial or duplicate spawn behavior

For practical modding, always treat CharacterInfo as the center of the player lifecycle and treat connection-specific logic as a later-stage layer, not the foundation of the character.
