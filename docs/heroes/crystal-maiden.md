# Crystal Maiden - Hero Design Case

**Status:** First durable pass

**Current factual reference state:** Dota 2 7.41e. Crystal Maiden's last hero-specific change in the 7.41 series was 7.41b, which increased Crystal Clone cooldown from 10 to 12 seconds. Historical material below is organized by design branch rather than by patch chronology.

## Design identity

Crystal Maiden is a fragile ranged Intelligence support whose baseline mobility and durability are deliberately modest relative to the area, control, and team-resource value of her spells. Arcane Aura changes allied mana economy across the map, Crystal Nova and Frostbite restrict enemy movement and attacks, and Freezing Field asks a low-durability hero to maintain presence inside a dangerous area. Modern and historical upgrades repeatedly explore how spellcasting itself can pay part of that positional risk without removing the underlying weakness.

## Current combat chassis

| Property | Current value |
| --- | ---: |
| Primary attribute | Intelligence |
| Strength | 17 + 2.2 |
| Agility | 16 + 1.8 |
| Intelligence | 20 + 3.3 |
| Starting health | 494 |
| Starting health regeneration | 1.95/s total, including 0.25 base |
| Starting mana | 315 |
| Starting mana regeneration | 1/s |
| Starting armor | 2.67 |
| Starting attack damage | 48-54 |
| Attack type / range | Ranged / 600 |
| Projectile speed | 900 |
| Base attack speed | 100 |
| Base attack time | 1.7 s |
| Attack animation | 0.45 + 0 s |
| Movement speed | 280 |
| Turn rate | 0.6 |
| Vision | 1800 / 800 |

### Compact note

The chassis supplies range but little margin for positional error. Crystal Maiden's survivability is therefore strongly dependent on controlling enemy access, choosing where to commit, and using upgrades that partially pay for the danger created by her own spellcasting pattern.

## Glacial Guard

### Current factual baseline - Innate

- Passive.
- Each ability cast grants an **8-second physical damage barrier** after mana is actually spent.
- Barrier value is `Current mana cost x (0.30 + 0.02 x hero level)`.
- Multiple barrier instances add together, while each instance keeps its own duration.
- Level 20 talent adds **0.20** to the mana-cost-to-barrier factor.

### Current design branch: spending mana creates temporary physical survival

Glacial Guard does not reduce spell cost. Mana is still consumed, but the same resource expenditure creates a short-lived physical barrier.

**Compact design note:** the hero gains survivability by doing the action the kit already wants - casting spells - rather than through an independent defensive button. Because the barrier is physical-only and temporary, it does not erase Crystal Maiden's vulnerability to magic damage, control, silence, or mana depletion.

### Historical design branch: Blueheart Floe regeneration innate

The removed **Blueheart Floe** innate instead increased Crystal Maiden's own mana regeneration. A mature branch scaled at **25% / 50% / 75% / 100%** with Freezing Field levels before Innate scaling rules changed and the ability was removed in 7.41.

**Compact design note:** Blueheart Floe improved the rate at which Crystal Maiden recovered future casting resources. Glacial Guard instead makes current resource expenditure generate immediate defensive value.

## Crystal Nova

### Current factual baseline

| Property | Value |
| --- | --- |
| Cast | Area target |
| Damage type | Magical |
| Cast range | 700 |
| Radius | 425 |
| Damage | 110 / 160 / 210 / 260 |
| Movement slow | 20% / 30% / 40% / 50% |
| Attack-speed slow | 30 / 45 / 60 / 75 |
| Slow duration | 4 s |
| Cooldown | 11 / 10 / 9 / 8 s |
| Mana cost | 115 / 135 / 155 / 175 |
| Vision | 900-radius vision for 6 s at the target area |
| Level 15 talent | -4.5 s cooldown |
| Level 25 talent | +300 damage |

### Historical design branch: Frost Nova requires an enemy anchor

Before Crystal Nova, **Frost Nova** targeted an enemy unit and then affected an area around that unit. A representative late Frost Nova state used **600 cast range**, **200 radius**, separate primary and area damage values, 30% movement slow, 20 attack-speed slow, and 4-second slow duration.

### Current design branch: point-target control of space

Crystal Nova replaced the unit target with a point target and expanded the usable geometry. The current spell can be placed where an enemy is expected to move even when no target unit occupies that exact point, and it also provides temporary ground vision.

**Compact design note:** changing the targeting requirement changes what can be controlled. A unit-anchored area follows the existence of a target; a point-target area can contest empty space, paths, fogged terrain, or future movement.

### Historical design branch: Glacial Guard facet distributes barriers through Nova

A removed **Glacial Guard** facet increased Crystal Nova radius by **100** and gave allied heroes hit by the Nova a **4-second physical barrier** of **40 / 70 / 100 / 130**, with a **2x** self-barrier factor for Crystal Maiden.

**Compact design note:** this branch tied protection to Nova placement and ally positioning. The current Innate instead ties protection to Crystal Maiden's own mana spending, removing the need for Nova to double as a friendly defensive placement tool.

## Frostbite

### Current factual baseline

| Property | Value |
| --- | --- |
| Cast | Unit target |
| Damage type | Magical |
| Cast range | 600 |
| Damage per second | 100 |
| Hero duration | 1.5 / 2 / 2.5 / 3 s |
| Creep damage factor | 4x |
| Cooldown | 9 / 8 / 7 / 6 s |
| Mana cost | 125 / 135 / 145 / 155 |
| Status | Root + disarm + True Sight |
| Level 15 talent | +100 cast range |
| Level 25 talent | +1 s duration |

### Historical design branch: long-duration creep disable

For many years Frostbite lasted **10 seconds** on ordinary creeps, giving the same spell a much longer PvE control duration than its hero-control duration.

In 7.36, creep duration was reduced to the same **1.5 / 2 / 2.5 / 3 s** progression used on heroes and a **4x creep damage factor** was added instead.

**Compact design note:** the spell retained strong non-hero utility, but the special PvE advantage moved from extreme control duration to faster damage. The branch changes whether the tool solves a creep problem by disabling it for a long time or by killing it more efficiently.

### Historical upgrade branch: self-Frostbite for defensive commitment

The 7.28 Aghanim's Shard allowed Crystal Maiden to double-tap Frostbite on herself:

- applied Frostbite's root and disarm to Crystal Maiden;
- granted **70% incoming damage reduction**;
- had instant cast time while Crystal Maiden was channeling, so it could be used during Freezing Field without interrupting the channel;
- also reduced Frostbite cooldown by 1 second.

**Compact design note:** this branch paid for Freezing Field survival by making Crystal Maiden even less able to act. The hero accepted stronger commitment in exchange for much higher durability.

## Arcane Aura

### Current factual baseline

| Property | Value |
| --- | --- |
| Type | Passive aura |
| Global mana regeneration | 0.4 / 0.6 / 0.8 / 1 |
| Proximity radius | 1200 |
| Proximity factor | 3x base aura value |
| Mana regen within 1200 | 1.2 / 1.8 / 2.4 / 3 |
| Self mana-regeneration amplification | 20% / 40% / 60% / 80% |

The global and proximity layers make the ability valuable both when Crystal Maiden is elsewhere on the map and when allies are fighting near her.

### Historical design branch: local aura becomes global support

Arcane Aura originally had a limited radius; an early major branch increased its radius from **400 to global**. This changed the ability from local formation support into a persistent team-wide resource modifier.

### Historical design branch: casting triggers discrete team mana restoration

A 7.31 branch made every Crystal Maiden ability cast replenish **6 / 12 / 18 / 24 mana** to allies within **1200**. In 7.32 that cast-triggered restoration was removed and replaced by stronger continuous proximity regeneration layered on top of the global aura.

**Compact design note:** continuous regeneration changes the team's long-run spell budget with little timing dependence; cast-triggered restoration makes Crystal Maiden's own spell cadence an explicit input to allied resources.

### Historical design branch: Cold Comfort converts her casts into ally mana

The removed **Cold Comfort** facet revisited cast-triggered support. Each Crystal Maiden spell cast restored nearby allies by a fraction of that ability's mana cost: **10% / 15% / 20% / 25%** within 1200.

### Historical design branch: Arcane Overflow deliberately increases personal cost

The removed **Arcane Overflow** facet added an active state:

- **10-second** duration and **30-second** cooldown;
- Crystal Maiden gained **35% outgoing spell damage amplification**;
- her ability mana costs were multiplied by **1.5**;
- spent mana was converted into mana restoration for allied heroes within **1200**.

A later version changed the exact restoration calculation, but the defining branch remained that higher personal spell expenditure could create team resources.

**Compact design note:** Arcane Overflow turned resource inefficiency for the caster into a team-support output. It is a stronger trade-off model than passive Aura because the player deliberately accepts higher personal depletion for a temporary offensive and team-economy payoff.

## Freezing Field

### Current factual baseline

| Property | Value |
| --- | --- |
| Cast | No target / channeled |
| Damage type | Magical |
| Maximum duration | 10 s |
| Field / slow radius | 810 |
| Explosion spawn radius | 195-785 |
| Explosion damage radius | 320 |
| Explosion interval | 0.1 s |
| Damage per explosion | 110 / 180 / 250 |
| Movement slow | 40% |
| Attack-speed slow | 80 / 120 / 160 |
| Slow linger | 1 s |
| Cooldown | 100 / 95 / 90 s |
| Mana cost | 200 / 400 / 600 |
| Level 20 talent | +50 explosion damage |

The movement and attack-speed slow apply across the field independently of whether a random explosion hits a particular enemy. Current explosion placement cycles through four sectors and remains random within each sector; average explosion damage is roughly stable near the center and decreases toward the outer edge.

### Historical design branch: control depends on random explosion hits

An early Freezing Field model slowed enemies only when an explosion hit them. A later branch changed the spell so all enemies within the field were slowed regardless of which random explosions connected.

**Compact design note:** separating reliable area control from stochastic damage lets the ultimate create a predictable positional rule while retaining uncertainty in exact damage output.

### Historical design branch: channel survival through bonus armor

Before 7.36, Freezing Field granted Crystal Maiden **20 bonus armor** while active.

**Compact design note:** this branch directly compensated for the physical danger of standing still near enemies without changing the channeling requirement itself.

### Historical design branch: action freedom replaces stronger immobility

The 7.29 Shard replaced the self-Frostbite defensive branch with a different solution:

- Freezing Field no longer prevented Crystal Maiden from moving, attacking, or casting abilities;
- Crystal Maiden suffered **75% self movement slow**;
- the Field followed her movement;
- enemy interruptions and silences could still end the spell.

This action-freedom model later moved from Shard to Aghanim's Scepter.

**Compact design note:** the two branches solve the same survival problem in opposite ways. Self-Frostbite deepened immobility in exchange for damage reduction; the movement branch restores actions while preserving commitment through severe movement slow and enemy interruptibility.

### Current Aghanim's Scepter branch

Current Scepter:

- removes Freezing Field's ordinary channeling restriction so Crystal Maiden may move, attack, and cast;
- applies **75% self movement slow** during the effect;
- keeps enemy interruption possible;
- increases explosion count/frequency by a **1.2 factor**, producing about **0.083 s** between explosions;
- applies Frostbite to enemies that remain in the Field for **2 seconds**;
- grants Stop Freezing Field to end the effect manually.

**Compact design note:** the upgrade does not merely increase ultimate magnitude. It changes the action budget during the commitment window, letting Crystal Maiden continue using the rest of her kit while the opponent retains ways to interrupt or leave the danger zone.

## Crystal Clone

**Current - Aghanim's Shard ability**

| Property | Value |
| --- | --- |
| Cast | Area/directional target |
| Movement distance | 275 |
| Movement duration | 0.3 s |
| Frostbite radius | 450 |
| Clone damage threshold | 150 |
| Clone lifetime | 5 s |
| Cooldown | 12 s |
| Mana cost | 150 |

On cast, Crystal Maiden slides in the chosen direction and disjoints incoming projectiles, leaving a clone at the starting position. When the clone reaches its damage threshold or expires, it applies Crystal Maiden's current Frostbite to enemies within 450. Crystal Nova and Freezing Field can also damage and shatter the clone.

### Historical design branch: fixed retreat

The first Crystal Clone branch always slid Crystal Maiden **backwards 275** and used a smaller **300-radius** Frostbite trigger.

### Current design branch: player-selected micro-reposition

The ability later became area/direction targeted, allowing the 275-distance movement to be chosen rather than always retreating directly backward. The Frostbite radius ultimately reached **450**.

**Compact design note:** the ability is not only an escape. It moves Crystal Maiden a short distance while converting her old position into a delayed control threat that the enemy can trigger, avoid, or destroy.

## Current talents

| Level | Left | Right |
| --- | --- | --- |
| 10 | +12 Intelligence | +200 Health |
| 15 | -4.5 s Crystal Nova cooldown | +100 Frostbite cast range |
| 20 | +50 Freezing Field damage | +0.2 Glacial Guard mana-cost-to-barrier factor |
| 25 | +300 Crystal Nova damage | +1 s Frostbite duration |

## Kit relationships

- **Arcane Aura -> team spell budget:** Crystal Maiden changes allied mana availability even when she is not the unit casting the eventual spells.
- **Arcane Aura -> own spell cadence -> Glacial Guard:** stronger personal mana regeneration supports more spell use, while each mana expenditure produces temporary physical protection.
- **Crystal Nova / Frostbite -> Freezing Field:** movement slow and root can increase the time enemies remain in the ultimate's dangerous area.
- **Freezing Field -> defensive upgrade pressure:** historical armor, self-Frostbite damage reduction, current Glacial Guard, and current Scepter all address the risk of a fragile hero maintaining a close-range sustained threat through different mechanisms.
- **Crystal Clone -> reposition plus residual control:** movement away from danger leaves a Frostbite threat at the original position instead of simply deleting spatial pressure.

## Compact design conclusions

- A support ability can change **team resource economy** rather than only adding direct combat magnitude; Arcane Aura changes how frequently allies can afford to use their own kits.
- A fragile chassis can support a high-commitment ultimate when defensive compensation preserves the commitment instead of erasing it. Crystal Maiden's history explores armor, self-disable plus damage reduction, mana-spend barriers, and restricted action freedom as different solutions.
- Resource spending can create a secondary short-term resource: Glacial Guard turns mana expenditure into temporary physical durability without making the spells cheaper.
- A control spell can preserve distinct PvP and PvE functions by changing the special-case output rather than simply extending the same disable duration.
- Restoring movement or actions during an ultimate is a capability change, not merely a numerical buff; the 75% self slow and enemy interruptibility preserve meaningful cost after the action space expands.

These are case-supported observations, not yet cross-hero principles.

## Sources

Current and historical factual material was checked against:

- Liquipedia - Crystal Maiden: https://liquipedia.net/dota2/Crystal_Maiden
- Liquipedia - Crystal Maiden Changelogs: https://liquipedia.net/dota2/Crystal_Maiden/Changelogs
- Liquipedia - archived Crystal Maiden page: https://liquipedia.net/dota2/Archive:Crystal_Maiden
- Liquipedia - Hero Attributes Table: https://liquipedia.net/dota2/Table_of_hero_attributes
- Liquipedia - Version 7.41: https://liquipedia.net/dota2/7.41
- Liquipedia - Version 7.41b: https://liquipedia.net/dota2/Version_7.41b
- Liquipedia - Version 7.36: https://liquipedia.net/dota2/Version_7.36
- Liquipedia - Version 7.34: https://liquipedia.net/dota2/Version_7.34
- Liquipedia - Version 7.29: https://liquipedia.net/dota2/Version_7.29
- Liquipedia - Version 7.28: https://liquipedia.net/dota2/Version_7.28

Where a historical mechanic had many balance-only parameter changes, this document records representative values sufficient to distinguish the design branch rather than reproducing a patch chronology.
