---
_schema: child
layout: default
title: Dumps
nav_order:
nav_exclude: false
parent: Server Documentation
has_children: false
has_toc: true
last_modified_date: 2025-12-10T13:43:22Z
---
# Dumps from the engine

| Scope | Subscope | Variable | Default value | Comment |
|:--|:--|:--|:--|:--|
| $cm_config |  | AllowCharacterCreation | 1 | Allows players to create characters |
| $cm_config | Animals | AnimalMaxHeightHit | 2 | Max hit height for animals |
| $cm_config | Animals | SpawningAnimalsCount | 20 | Number of animals that can spawn |
| $cm_config |  | AprilFoolsDay | 0 | Enables April Fools mode |
| $cm_config | Building | IterationTime | 5000 | Time per building iteration (ms) |
| $cm_config | Building | MaxIterationQuantity | 100 | Max building iterations |
| $cm_config | Claims | GuildCellPrice | 1 | Cost of claim cells |
| $cm_config | Claims | guildLevel1MinSacrificeBasePrice | 1 | Base price for level 1 guild sacrifices |
| $cm_config | Claims | guildLevel1RadiusCountry | 20 | Radius for country-level guild claim L1 |
| $cm_config | Claims | guildLevel1RadiusTown | 20 | Radius for town-level claim L1 |
| $cm_config | Claims | guildLevel2MinSacrificeBasePrice | 10 | Base price for level 2 guild sacrifices |
| $cm_config | Claims | guildLevel2RadiusCountry | 30 | Radius for country-level claim L2 |
| $cm_config | Claims | guildLevel2RadiusTown | 30 | Radius for town-level claim L2 |
| $cm_config | Claims | guildLevel3MinSacrificeBasePrice | 50 | Base price for level 3 guild sacrifices |
| $cm_config | Claims | guildLevel3RadiusCountry | 50 | Radius for country-level claim L3 |
| $cm_config | Claims | guildLevel3RadiusTown | 50 | Radius for town-level claim L3 |
| $cm_config | Claims | guildLevel4MinSacrificeBasePrice | 100 | Base price for level 4 guild sacrifices |
| $cm_config | Claims | guildLevel4RadiusCountry | 100 | Radius for country-level claim L4 |
| $cm_config | Claims | guildLevel4RadiusTown | 100 | Radius for town-level claim L4 |
| $cm_config | Claims | MonumentGrowth | 0.05 | Monument growth multiplier |
| $cm_config | Criminals | DamagedSomeone | -2 | Alignment hit for damaging someone |
| $cm_config | Criminals | KilledSomeone | -10 | Alignment hit for killing someone |
| $cm_config | Criminals | KnockedOutSomeone | -3 | Alignment hit for knockouts |
| $cm_config | Criminals | LootedSomeone | -3 | Alignment loss for looting |
| $cm_config | Criminals | TrespassedSomething | -1 | Alignment loss for trespassing |
| $cm_config | DB::Connect | db_name | lif_1 | Database name |
| $cm_config | DB::Connect | password | ***** | Sensitive: masked password |
| $cm_config | DB::Connect | server | ************** | Sensitive: masked server address |
| $cm_config | DB::Connect | user | ***** | Sensitive: masked DB username |
| $cm_config | DB | disabled | <span style="color:red">0</span> | **Dangerous: disables the database** |
| $cm_config | DB | keepConnection | 1 | Keeps persistent DB connection |
| $cm_config | Decay | BaseObjectDecayRate | 500 | Base decay rate for objects |
| $cm_config | Decay | HorsesDecayTimeMinutes | 0 | Horse decay timer |
| $cm_config | DropPosition | AllowedPenetration | 0.05 | Allowed insertion depth for placement |
| $cm_config | DropPosition | LockedHeightOver | 0.2 | Height offset when locked |
| $cm_config |  | EvilHeadsCut | 0 | Enables cutting evil heads |
| $cm_config | FireAbility | FireTimeMinutes | 60 | Burn time for fire ability |
| $cm_config | Geo | HeavyTimberDecayValue | 1 | Decay value for heavy timber |
| $cm_config | Geo | HeavyTimberWidth | 0.4 | Width of heavy timber |
| $cm_config | Geo | LightTimberDecayValue | 1 | Decay value for light timber |
| $cm_config | Geo | LightTimberDefaultDecayResource | 10 | Default decay resource |
| $cm_config | Geo | LightTimberWidth | 0.3 | Width of light timber |
| $cm_config | Geo | QuantityDamagePerDig | 800 | Digging damage per action |
| $cm_config | Geo | QuantityDamagePerLower | 3000 | Damage per lowering |
| $cm_config | Geo | QuantityMass | 0.01 | Mass quantity |
| $cm_config | Geo | QuantityMassMining | 0.01 | Mass quantity for mining |
| $cm_config | Geo | QuantityPerLevel | 3000 | Quantity per level |
| $cm_config | Geo | TimberIntersectPercentForArm | 50 | Structure intersection percent |
| $cm_config | Geo | TunnelBaseDecayResource | 8 | Base resource for tunnel decay |
| $cm_config | Geo | TunnelDecayValue | 1 | Decay value for tunnels |
| $cm_config | Geo | TunnellingRockRatio | 0.5 | Rock ratio during tunneling |
| $cm_config |  | GlobalRegionId | Dev | Region identifier |
| $cm_config |  | GlobalWorldId | Dev-0 | World identifier |
| $cm_config | Guilds | HeraldryChangingCooldownSec | 86400 | Cooldown for heraldry changes |
| $cm_config |  | HomecomingDrop | 0 | Drop items on homecoming |
| $cm_config |  | HorseTrainingTimeSec | 300 | Horse training time |
| $cm_config |  | hungerIdleLossPerSecond | 0.0025 | Hunger decay per idle second |
| $cm_config | JudgementHour | headPrice | 100 | Price for head in Judgement Hour |
| $cm_config | Knockouts | yieldKnockoutInterval | 3 | Time between yield knockouts |
| $cm_config |  | localIpAddress | *********** | Sensitive: masked internal IP |
| $cm_config | ObserveTerrain | RadiusX | 11 | Observation radius X |
| $cm_config | ObserveTerrain | RadiusY | 11 | Observation radius Y |
| $cm_config |  | OutpostClaimDurationMin | 10 | Minimum outpost claim duration |
| $cm_config | patching | MinForestChangesCachingCount | 1000 | Forest caching minimum |
| $cm_config | patching | MinGeoChangesCachingCount | 100 | Geo changes caching |
| $cm_config | patching | MinObjectChangesCachingCount | 1000 | Object caching minimum |
| $cm_config | Potions | maxPoisonWeaponAmount | 3 | Max poison amount applied to weapons |
| $cm_config | Potions | maxPotionAmount | 3 | Max number of potions |
| $cm_config | Server | MaxServerID | 1 | Highest server ID |
| $cm_config | Server | ServerCount | 1 | Number of servers |
| $cm_config | Server | ServerSkipCount | <span style="color:red">0</span> | **Dangerous: server skipping may break cluster** |
| $cm_config | Server | ServerXCount | 1 | Servers in X axis |
| $cm_config | Server | ServerYCount | 1 | Servers in Y axis |
| $cm_config | Server | TerrainCountAtServer | 9 | Terrain count per server |
| $cm_config | Server | TerrainCountTotal | 9 | Total terrain count |
| $cm_config | Server | TerrainSkipCount | 441 | Skipped terrain count |
| $cm_config | Server | TerrainXCount | 3 | Terrain dimension X |
| $cm_config | Server | TerrainXCountTotal | 3 | Total terrain X |
| $cm_config | Server | TerrainYCount | 3 | Terrain dimension Y |
| $cm_config | Server | TerrainYCountTotal | 3 | Total terrain Y |
| $cm_config | SiegeDamage | destructible | 0.002 | Siege destructibility multiplier |
| $cm_config | SkillLoss | Bad | 1.5 | Skill loss in bad conditions |
| $cm_config | SkillLoss | Default | 1 | Default skill loss |
| $cm_config | SkillLoss | Evil | 6 | Skill loss when evil |
| $cm_config | SkillRaise | GlobalMult | 10 | Global skill raise multiplier |
| $cm_config | Terrain | AllowedTunnelNearness | 2 | Allowed nearness to tunnel |
| $cm_config | Terrain | ClaimRenderDistance | 800 | Claim render distance |
| $cm_config | Terrain | DigAdjust | 1 | Dig adjust factor |
| $cm_config | Terrain | DigTime | 1000 | Dig time |
| $cm_config | Terrain | FlattenTime | 1000 | Flatten time |
| $cm_config | Terrain | HeightAdjustLower | -0.2 | Lowering height adjust |
| $cm_config | Terrain | HeightAdjustRaise | 0.2 | Raising height adjust |
| $cm_config | Terrain | HeightLowerTime | 1000 | Lowering height time |
| $cm_config | Terrain | HeightRaiseTime | 1000 | Raising height time |
| $cm_config | Terrain | MaxAltitudeDiffBeforeFall | 8 | Max altitude difference before fall |
| $cm_config | Terrain | SlopeFlattenDiff | 1 | Allowed slope flatten difference |
| $cm_config | Terrain | SlopeFlattenTime | 1000 | Time to flatten slope |
| $cm_config | TrainingField | ProbabilityOfRoyalHorsePCT | 3 | Chance to train royal horse |
| $cm_config |  | WindMillChurnRate | 2 | Windmill churn rate |
| $cm_config |  | WorkingContainerBaseTimeMs | 3600000 | Container working time |
| $cm_config |  | worldID | 1 | World ID |
| $cm_config |  | WorldZoneType | Red | World zone type |
| $cm_config | Wounds | DurationMult | 1 | Wound duration multiplier |
| $CombatConstants |  | ArmorDurabilityDamageMultiplier | 0.1 | Multiplier for durability damage applied to armor |
| $CombatConstants |  | Chopping2ShieldDurabilityDamage | 3 | Shield durability damage from chopping attacks |
| $CombatConstants |  | combo_time_window_duration__relative | 1 | Relative combo timing window |
| $CombatConstants |  | combo_time_window_duration_seconds__max | 0.8 | Maximum combo timing window (seconds) |
| $CombatConstants |  | combo_time_window_duration_seconds__min | 0.8 | Minimum combo timing window (seconds) |
| $CombatConstants |  | FullBodyDamageMultiplier | 1.2 | Global damage multiplier for full-body hits |
| $CombatConstants |  | Melee2ShieldDurabilityDamage | 0.15 | Shield durability damage from melee hits |
| $CombatConstants |  | PeaceModeDamageMultiplier | 1.5 | Damage multiplier in peace mode |
| $CombatConstants |  | Piercing2ShieldDurabilityDamage | 1.2 | Shield durability damage from piercing hits |
| $CombatConstants |  | Range2ShieldDurabilityDamage | 0.05 | Shield durability damage from ranged attacks |
| $CombatConstants |  | ShieldPassive | 0.5 | Passive shield block modifier |
| $CombatConstants |  | ShieldPassiveBlockCoeff | 0.2 | Coefficient for passive shield blocking |
| $CombatConstants |  | ShieldPassiveOnActiveBlock | 0.7 | Shield block multiplier during active blocking |
| $CombatConstants |  | WeaponDurabilityDamage | 0.05 | Weapon durability damage per use |
| $CombatConstants |  | WeaponFractureMax_in_DurabilityDamage | 0.5 | Maximum durability loss from fractures |
| $CombatConstants |  | WeaponFractureMin_in_DurabilityDamage | 0.1 | Minimum durability loss from fractures |
