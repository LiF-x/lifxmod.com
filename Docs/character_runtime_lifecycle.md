# Core Character Lifecycle Documentation

## Overview

This document describes the **externally observable** character lifecycle in the closed-core Life is Feudal server runtime.

It is intended as a **reverse-engineering reference for modding**, not as an authoritative source-code description of the internal engine architecture.

The content below is based on:

- runtime logs
- exposed script hooks
- console/class dumps
- practical modding experiments
- known Torque3D object and networking patterns

Because the core is closed, this document distinguishes between what is directly visible and what is only inferred.

---

## Evidence Model

### Confirmed

Behavior directly observed in logs, dumps, exposed scripting interfaces, or runtime experiments.

### Inferred

Behavior strongly suggested by repeated runtime observations and known Torque3D patterns, but not directly visible in source.

### Unknown

Internal implementation details that remain hidden and must not be presented as established fact.

---

## Scope Limitation

This document does **not** claim full knowledge of:

- internal manager ownership
- hidden data structures
- class boundaries inside the closed C++ core
- whether visible functions are primary implementations or wrappers/facades

Where those details are not directly visible, they are marked as inferred or unknown.

---

## Confirmed Runtime Surface

## Connection and client registry

### Confirmed

A live client exists as a `GameConnection`-like runtime object and active clients are stored under `ClientGroup`, which is a real `SimGroup` object in the runtime object hierarchy.

### Practical meaning

There is a real connection registry layer in the server runtime, and player-facing lifecycle actions happen relative to a live client object rather than purely in isolation.

### Unknown

It is not confirmed whether higher-level internal managers mirror or wrap `ClientGroup`.

---

## World/network object base

### Confirmed

Torque3D object hierarchy is present:

`SimObject -> NetObject -> SceneObject -> Player`

Observed dumps confirm:

- `NetObject` supports ghosting and scope control
- `SceneObject` provides transform/world presence
- `Player` is a networked world object

### Practical meaning

A player is not just character data. It is also a real world/network object that must exist inside Torque3D runtime object and replication systems.

### Unknown

Exact internal coupling between `Player` and hidden character-state containers is not directly visible.

---

## Exposed modding hook surface

### Confirmed

LiFx exposes event-style callbacks such as:

- `onConnectCallbacks`
- `onSpawnCallbacks`
- `onDisconnectCallbacks`

### Practical meaning

The modding layer exposes lifecycle observation and extension points, but this does **not** prove ownership of the actual internal spawn pipeline.

### Unknown

Whether these callbacks run before, during, or strictly after all internal manager work is not fully documented by the closed core.

---

## Character-Related Runtime Functions

## CharacterInfo

### Confirmed

The following functions are directly visible in runtime logs:

- `CmCharacterInfo::stopSim(charId)`
- `CmCharacterInfo::startSim(charId)`
- `CmCharacterInfo::sendFirstDataClient()`

### Confirmed role

`CmCharacterInfo` is definitely involved in:

- simulation state transitions
- client-facing initialization data
- character-linked runtime activation

### Inferred role

`CmCharacterInfo` likely acts as a bridge between persistent character identity/state and the active runtime entity.

### Unknown

It is not directly proven whether `CmCharacterInfo` owns inventory, equipment, or all gameplay state itself, or whether it coordinates multiple hidden subsystems.

---

## CharacterParameters

### Confirmed

The following function is directly visible in logs:

- `CharacterParameters::LoadPlayer()`

It appears during player activation and again when control is restored to the original player.

### Confirmed role

`CharacterParameters::LoadPlayer()` is part of the real activation/load pipeline for a valid character.

### Inferred role

It likely performs the actual transfer of persistent character data into runtime state.

### Unknown

The exact boundaries between `CharacterParameters`, `CmCharacterInfo`, and the runtime `Player` object are not visible.

---

## Player

### Confirmed

A `Player` object is a real runtime object with:

- a datablock
- a transform/world position
- a controlling client relationship
- a character ID getter surface

Observed experiments show that a newly spawned `Player` can exist with:

- `DefaultPlayerData`
- `getCharacterId() = 0`

if the expected character backing is not present.

### Practical meaning

A `Player` object can be created even when character activation is not valid.

This is extremely important:

**world object creation does not by itself prove valid character initialization**

### Unknown

It is not proven that `Player` itself owns character state; it may instead be a world-side representation attached to hidden character systems.

---

## Practical Confirmed Spawn Sequence

The following order is directly supported by logs from successful and failed runtime experiments.

## Confirmed sequence during a normal valid character rebind

Observed order:

1. `CharacterParameters::LoadPlayer()`
2. `CmCharacterInfo::startSim(charId)`
3. `CmCharacterWounds::onSimStarted()`
4. `CmCharacterInfo::sendFirstDataClient()`
5. control object binding is finalized

This sequence appears when control is restored to the original valid player.

## Confirmed sequence during failed bridge attempt

Observed order:

1. connection character ID fields are overwritten
2. `spawnPlayer(connection)` is called
3. duplicate-player warning appears
4. `Player::getPlayerDatablock() -- can't find CharacterInfo for player 2`
5. fallback to default datablock occurs
6. a new `Player` is created with `DefaultPlayerData`
7. `Player::setControllingClient() -- can't find CharacterInfo for player 2`
8. spawned target has `getCharacterId() = 0`
9. target is judged invalid and deleted
10. original player control is restored

### Confirmed conclusion

Simply changing connection-side character ID fields is **not sufficient** to produce a valid CharacterInfo-backed player.

A valid character activation requires something more than just connection identity overwrite.

---

## What the bridge experiment actually proves

## Confirmed

A live connection for character 1 was captured successfully.

The connection initially reported:

- `charId=1`
- `getCharacterId()=1`
- valid live `player`
- valid live `control object`

After overwriting the connection fields to character 2 and calling `spawnPlayer(connection)`, the runtime produced:

- duplicate creation warning
- missing `CharacterInfo` for player 2
- default datablock fallback
- spawned `Player` with character ID `0`

### Confirmed meaning

The connection object alone is not the authoritative source of valid character runtime state.

### Strong inference

There must be an additional internal registration or backing-state lookup that resolves whether a character is valid for full activation.

That backing state is very likely related to `CharacterInfo`.

### Unknown

The exact internal lookup path and ownership chain remain hidden.

---

## Character Lifecycle Model

## Confirmed minimum model

A valid online character requires at least three things to line up:

1. a live connection object
2. a valid character-backed runtime resolution path
3. a valid world `Player` object bound to that state

## Inferred interpretation

The runtime is not purely connection-driven and not purely player-object-driven.

A more accurate practical model is:

**connection context + hidden character backing + world player object**

rather than:

**connection only**
or
**player object only**

---

## What can be stated safely about CharacterInfo

## Confirmed

`CharacterInfo`-related functions appear exactly at the point where real character activation succeeds.

When backing is missing, the runtime explicitly reports:

- `can't find CharacterInfo for player 2`

### Safe conclusion

`CharacterInfo` is not just cosmetic naming. It is part of the validation/activation path for a real playable character.

### What should no longer be overstated

It is too strong to claim, without qualification, that `CharacterInfo` is the sole center of all gameplay state.

A safer phrasing is:

**CharacterInfo appears to be a required part of valid character activation and simulation lifecycle.**

---

## Inventory and Equipment

## Confirmed

This document currently has **no direct proof** showing the exact load point of inventory and equipment within the activation sequence.

## Inferred

Inventory and equipment likely depend on successful character-backed initialization, because failed character activation falls back to a default player shell rather than a fully initialized target.

## Unknown

The following are not currently proven:

- whether inventory is owned by `CharacterInfo`
- whether equipment is attached before or after simulation start
- whether inventory/equipment are loaded inside `LoadPlayer()` or by separate hidden managers

### Practical documentation rule

Until direct proof is collected, inventory/equipment should be documented as **dependent subsystems with unresolved load boundaries**.

---

## CharacterTriggers

## Confirmed

This document does not currently include direct trace evidence for trigger manager ownership or exact trigger execution order.

## Inferred

Some trigger paths likely depend on valid online connection mapping, because invalid player identity or missing backing state causes downstream failures in runtime behavior.

## Unknown

The exact boundary between offline-safe character logic and connection-dependent trigger logic remains unverified.

---

## ConnectedPlayersManager

## Confirmed

This document does not yet provide direct public API proof for `ConnectedPlayersManager`.

The current understanding comes from error interpretation and runtime behavior patterns, not direct implementation visibility.

## Inferred

It likely participates in active-player registration and online visibility/broadcast state.

## Unknown

Its real ownership, timing, and relationship to connection and character activation remain hidden.

### Documentation rule

Until direct trace evidence is added, this system should not be described as if its internal responsibility were fully known.

---

## Revised Practical Spawn Model

## What is directly supported by evidence

For a valid character activation path, the runtime can be observed performing:

- player/control reassignment work
- `CharacterParameters::LoadPlayer()`
- `CmCharacterInfo::startSim()`
- `CmCharacterWounds::onSimStarted()`
- `CmCharacterInfo::sendFirstDataClient()`

For an invalid target character, the runtime can instead produce:

- missing `CharacterInfo`
- default datablock fallback
- invalid `Player` shell with character ID `0`

## Safe practical conclusion

A correct spawn/activation path is not merely:

**create player -> assign connection**

It also requires:

**successful hidden character-backed resolution**

---

## Error Interpretation Guide

## Error: `can't find CharacterInfo for player X`

### Confirmed meaning

The runtime attempted to resolve a character-backed activation path for a player identity and failed.

### Confirmed consequence

The system may fall back to a default datablock and create an invalid player shell.

### Safe conclusion

This is one of the strongest currently visible indicators that character backing and world player creation are separate concerns.

---

## Error: `Player::getPlayerDatablock() -- can't find CharacterInfo ... Returning default datablock`

### Confirmed meaning

Datablock selection for a spawned player can depend on successful character backing resolution.

### Confirmed consequence

Failure produces `DefaultPlayerData` instead of the expected real character datablock.

---

## Error: `Player::setControllingClient() -- can't find CharacterInfo for player X`

### Confirmed meaning

Control binding alone is not enough to validate the player.

The control-binding path still attempts to resolve character backing.

### Confirmed consequence

A control-bound player object may still be invalid as a real character.

---

## Error: `Attempting to create a player for a client that already has one!`

### Confirmed meaning

The spawn path was called while the client still had an active player object.

### Practical meaning

Any experiment that tries to bridge or swap characters through a live connection must account for the fact that the connection already owns a player.

---

## Error: `Simulation has already started (playerId X)`

### Confirmed meaning

Restoring or re-running activation logic on an already active valid character can cause duplicate simulation-start attempts.

### Practical meaning

The simulation lifecycle is stateful and not safely idempotent.

---

## Modding Guidance

## Safe claims

Modders can safely assume:

- a live connection does not automatically imply valid character activation
- a spawned `Player` object does not automatically imply valid character backing
- `CharacterInfo` resolution matters in practice
- `LoadPlayer()`, `startSim()`, and `sendFirstDataClient()` are part of the real activation path

## Unsafe claims

Modders should avoid claiming, without proof, that:

- `CharacterInfo` owns all gameplay state
- inventory always loads after `LoadPlayer()`
- equipment always depends directly on `CharacterInfo`
- a specific hidden manager owns player registration unless direct trace evidence is shown

---

## Practical Example

## Example: bridge-spawn attempt through a live connection

A practical experiment attempted to:

1. capture a live client connected as character 1
2. overwrite the connection-side character ID to 2
3. call `spawnPlayer(connection)`
4. inspect the resulting target player
5. restore original control

### Result

The bridge failed.

Observed outcome:

- runtime could not find `CharacterInfo` for player 2
- default datablock fallback occurred
- spawned target had `getCharacterId() = 0`
- target had to be deleted
- restoring original control to character 1 re-ran the normal valid activation path

### Why this example matters

This is a concrete runtime demonstration that the visible connection fields are not enough to impersonate or fully activate another character through the same live connection.

---

## Architectural Conclusion

The safest current interpretation is:

### Confirmed practical model

A valid playable character requires:

- connection context
- character-backed runtime resolution
- world player object
- simulation/client sync activation steps

### Strong inference

The core separates at least part of:

- online connection state
- hidden character backing/state
- world entity state

### Unknown

The exact internal ownership boundaries between these layers are still not visible.

---

## Final Summary

The old version of this document overstated some architectural conclusions.

A more accurate and evidence-based summary is:

**A live connection, a world Player object, and valid character-backed runtime resolution are separate concerns.**

The strongest currently confirmed rule is:

**if CharacterInfo-backed resolution fails, the runtime may still create a Player object, but that object is not a valid fully initialized character.**

That is directly supported by practical experiments showing:

- missing `CharacterInfo`
- default datablock fallback
- invalid target player with character ID `0`
- successful reactivation only when returning to the original valid character

This document should therefore be read as a reverse-engineered field guide based on observable behavior, not as a full reconstruction of the closed-core architecture.

---

## Footnote

This document was assembled from reverse-engineering notes, runtime experiments, and edited technical drafting assistance. It should be evaluated by the evidence and examples included, not as an official source-code document.
