# Juggernaut - Hero Design Case

**Status:** First durable pass

**Current factual reference state:** Dota 2 7.41e. Juggernaut received no hero changes in 7.41e, so the latest Juggernaut-specific values come from the 7.41d-or-earlier changes reflected below. Historical material is organized by design branch rather than by patch chronology.

## Design identity

Juggernaut starts from a strong melee Agility attack chassis, then repeatedly enters temporary states that change how normal combat rules apply. His historical design repeatedly explores one question: **how much should Blade Fury and Omnislash remain separate from, partially share, or fully reuse the hero's ordinary attack growth?** Healing Ward adds a different pattern by externalizing powerful sustain into a movable object the opponent can directly destroy.

## Current combat chassis

| Property | Current value |
| --- | ---: |
| Primary attribute | Agility |
| Strength | 20 + 2.0 |
| Agility | 32 + 2.8 |
| Intelligence | 14 + 1.4 |
| Starting health | 560 |
| Starting health regeneration | 2.5/s total, including 0.5 base |
| Starting mana | 243 |
| Starting mana regeneration | 0.7/s |
| Starting armor | 5.33 |
| Starting attack damage | 54-56 |
| Attack type / range | Melee / 150 |
| Base attack speed | 110 |
| Base attack time | 1.4 s |
| Attack animation | 0.33 + 0.84 s |
| Movement speed | 305 |
| Turn rate | 0.6 |
| Vision | 1800 / 800 |

### Compact note

The **1.4 BAT**, above-default starting attack speed, high starting Agility, and Agility growth make the ordinary attack system a valuable part of the hero before any spell scaling is considered. That makes the relationship between special states and normal attacks a recurring design problem.

## Bladeform

### Current factual baseline - Innate

- Passive, breakable for new-stack generation.
- Gains one stack every **2 seconds** without taking damage.
- Maximum **10 stacks**.
- Each stack grants **2.5% + 0.1% x hero level** bonus base Agility and **1% movement speed**.
- On taking damage, the current bonus lingers for **2 seconds** before disappearing.
- Level 10 talent: **-1 second** stack-gain interval, reducing full preparation from 20 seconds to 10 seconds.

### Historical design branch: fixed pre-combat stacking

As a facet, Bladeform originally used a simpler fixed per-stack value: one stack every **2 seconds**, up to **10**, each giving about **3% base Agility** and **1% movement speed**, with the stacks disappearing after a short post-damage linger.

### Current design branch: hero-level-scaled preparation

The innate version keeps the pre-combat preparation loop but makes the Agility value itself scale with hero level.

**Compact design note:** Bladeform treats *not being damaged* as a resource-generating condition. Enemy poke can reduce future entry strength even when the immediate HP loss is small.

## Blade Fury

### Current factual baseline

| Property | Value |
| --- | --- |
| Cast | No target |
| Damage type | Magical |
| Damage per second | 85 / 115 / 145 / 175 |
| Damage interval | 0.2 s |
| Radius | 260 |
| Duration | 5 s |
| Cooldown | 30 / 26 / 22 / 18 s |
| Mana cost | 110 |
| Defensive state | Debuff immunity + 80% magic resistance |
| End effect | Strong dispel |
| Level 15 talent | +45 movement speed during Blade Fury |
| Level 20 talent | +120 DPS |

Juggernaut can still issue attacks during Blade Fury. Against units affected by Blade Fury, ordinary attack damage is suppressed; attacks can still damage targets not affected by the spin, such as structures and ward-type targets.

The 7.41 patch removed the **Bladestorm** component. Some third-party ability descriptions still mention Blade Dance critting Blade Fury; the patch record is treated as authoritative for this case, so Blade Fury crit interaction is recorded as historical rather than current.

### Design branch: fixed independent spell damage

The current form uses fixed spell DPS and a fixed **0.2 s** interval. Ordinary attack growth therefore does not directly increase Blade Fury DPS.

**Compact design note:** this preserves a strong mode switch: opening Blade Fury gains protection and fixed close-range magic damage but gives up much of the value of the normal physical attack mode against affected enemies.

### Historical design branch: attack speed scales spell ticks

Blade Fury was explored with a damage interval based on Juggernaut's current attack rate rather than a flat interval. The interval used the relationship between current BAT and total attack speed, effectively making higher attack speed generate more Blade Fury damage instances. A representative mature state used roughly **40/45/50/55 damage per tick**, with the tick interval calculated from the attack-rate formula rather than fixed at 0.2 seconds.

**Compact design note:** this is an intermediate integration model: the skill remains spell damage, but the public attack-speed growth system feeds it.

### Historical design branch: Shard reintegrates instant attacks

A former Aghanim's Shard branch:

- granted **+75 movement speed** during Blade Fury;
- performed an instant attack against a random nearby enemy every **1.4 seconds**;
- each instant attack dealt **75% attack damage** and could use normal attack modifiers/on-hit interactions.

Earlier tuning used a faster **1.2 s** attack interval and a larger movement-speed bonus before being reduced.

**Compact design note:** this branch directly reconnected physical carry growth to the defensive spin state, reducing the opportunity cost of entering Blade Fury late in the game.

### Historical design branch: Shard improves contact instead of attack scaling

A later Shard removed the instant attacks and instead:

- increased Blade Fury radius by **100**;
- applied a **35% movement slow** to enemies within the spin.

**Compact design note:** rather than increasing DPS directly, this branch increased the probability that enemies remain inside a sustained close-range damage zone.

### Historical design branch: Bladestorm partially integrates Blade Dance

The removed **Bladestorm** facet let Blade Fury proc Blade Dance according to Blade Dance's current level.

**Compact design note:** this is a partial-integration solution between fixed independent spell damage and full instant attacks: only the hero's signature critical-strike system crosses into the spin.

### Blade Fury design space summary

The historically realized branches form a useful continuum:

```text
fixed spell damage
    -> attack speed changes spell tick rate
    -> Blade Dance can enter the spin
    -> actual instant attacks occur during the spin
```

The continuum is reusable evidence for later study of how much of a normal attack economy should survive inside a special combat state.

## Healing Ward

### Current factual baseline

| Property | Value |
| --- | --- |
| Cast | Point target |
| Cast range | 350 |
| Ward movement speed | 325 |
| Heal | 2% / 3% / 4% / 5% max health per second |
| Radius | 400 |
| Duration | 18 / 20 / 22 / 24 s |
| Hits to destroy | 1 |
| Cooldown | 60 s |
| Mana cost | 120 |
| Level 10 talent | -12 s cooldown |
| Current Shard | +1.5 percentage points max-health heal per second and +1 hit to destroy |

The ward is controllable and multiple Healing Ward auras do not stack.

### Core design branch: powerful sustain on a destructible carrier

The base branch externalizes percentage healing into a movable unit that can be positioned, protected, chased, and killed. The opponent therefore has a direct action that shuts off a strong ongoing effect.

### Design branch: increase handling cost without deleting counterplay

The current Shard raises the heal to **3.5/4.5/5.5/6.5% max health per second** and increases hits to destroy from **1 to 2**.

Historical talents have also increased the Ward's hit count. The consistent idea is to increase the cost of removing the object rather than make it untargetable.

### Historical geometry branch

Healing Ward has also existed with a larger **500 radius** and a flat **25-second** duration. Later designs use a smaller **400 radius** and duration that scales by level.

**Compact design note:** Ward radius and movement are not merely convenience parameters; they determine how much positional risk the healer and opponent must take to preserve or remove the effect.

## Blade Dance

### Current factual baseline

| Property | Value |
| --- | --- |
| Type | Passive, breakable |
| Critical chance | 35% at all levels |
| Critical damage | 140% / 160% / 180% / 200% |
| Level 20 talent | +15 percentage points critical damage |
| Level 25 talent | +40% Blade Dance lifesteal |

### Historical design branch: level scaling through proc chance

A mature historical form used:

- **20% / 25% / 30% / 35%** critical chance;
- a flat **190%** critical damage multiplier.

### Current design branch: level scaling through proc magnitude

The current form holds chance at **35%** and increases the critical multiplier from **140% to 200%**.

**Compact design note:** both branches increase expected attack damage, but one progresses by making the event more reliable and the other by making each event more valuable.

### Historical/current sustain branch: lifesteal tied to the crit event

Talent designs have alternated between ordinary lifesteal and lifesteal specifically on Blade Dance procs. The current level 25 branch gives **40% lifesteal on Blade Dance**.

**Compact design note:** proc-linked lifesteal aligns survival spikes with damage spikes; ordinary lifesteal smooths sustain over every attack.

## Omnislash

### Current factual baseline

| Property | Value |
| --- | --- |
| Cast | Unit target |
| Cast range | 450 |
| Search / jump radius | 425 |
| Damage mechanism | Instant attacks / physical |
| Attack-rate divisor | 1.4 |
| Bonus attack damage | 25 / 30 / 35 |
| Bonus attack speed | 40 |
| Duration | 3 / 3.25 / 3.5 s |
| Cooldown | 120 s |
| Mana cost | 200 / 275 / 350 |
| Defensive state | Invulnerable and untargetable during the sequence |
| Cast effect | Basic dispel |
| Level 15 talent | -15 s cooldown |
| Level 25 talent | +1 s duration |

Each slash performs an instant attack, so normal attack damage, attack modifiers, and critical strikes can participate. Slash interval updates with current attack speed. If no valid target is found within the search rules, Omnislash can end early.

### Historical design branch: independent fixed slash damage

The classic pre-rework Omnislash used its own damage system:

- Cast range: **350**.
- Search radius: **425**.
- Slash interval: **0.4 s**.
- Number of slashes: **3 / 6 / 9**.
- Damage per slash: **200-225 physical**.
- Cooldown: **130 / 120 / 110 s**.
- Mana cost: **200 / 275 / 350**.
- Aghanim's Scepter could raise slash count to **6 / 9 / 12** and lower cooldown to **70 s**.

Juggernaut could still perform ordinary attacks between fixed slashes when his attack time was low enough, but the core slash damage itself was an independent spell-like budget.

### Current design branch: Omnislash re-executes the attack system

The modern branch replaced fixed slash count and fixed slash damage with a **duration** and repeated **instant attacks** whose rate depends on Juggernaut's attack speed.

**Compact design note:** attack damage, attack speed, Blade Dance, and attack modifiers now strengthen both normal combat and the ultimate rather than growing along parallel damage systems.

### Core targeting branch: target density controls concentration

Omnislash can jump among valid enemies within **425**. A lone legal target receives concentrated slash volume; nearby heroes, creeps, or summons can distribute the sequence. Fogged, hidden, or otherwise invalid targets cannot be selected by the search.

**Compact design note:** battlefield target density becomes an input to ultimate damage concentration, creating positioning counterplay without directly reducing the ability's numbers.

## Swiftslash

**Current - Scepter-granted separate ability**

| Property | Value |
| --- | --- |
| Cast range | 450 |
| Duration | 1 s |
| Cooldown | 25 s |
| Mana cost | 150 |
| Rules | Uses the short Omnislash execution model |

### Design branch: lower-commitment copy of the core ultimate

Swiftslash does not create a new damage formula. It provides a short, frequent use of the same attack-execution state.

**Compact design note:** an advanced upgrade can add a new decision scale - low-commitment/high-frequency versus high-commitment/low-frequency - instead of merely increasing one ultimate's peak numbers.

## Duelist [Historical / Removed]

A historical innate amplified Juggernaut's outgoing damage against enemies facing him.

Representative defining rules:

- Base damage amplification: **12%**.
- Enemy facing-angle check: about **55 degrees**.
- The damage amplification applied unconditionally during Omnislash-based abilities regardless of facing.
- A talent could add another **4 percentage points**.

### Compact design note

Duelist tried to add a front-facing "sword duel" relationship to the hero. It reinforced face-to-face combat thematically, but its behavioral effect was subtler than the explicit state changes created by Blade Fury or Omnislash.

## Current talents

| Level | Left | Right |
| --- | --- | --- |
| 10 | -1 s Bladeform stack-gain interval | -12 s Healing Ward cooldown |
| 15 | +45 movement speed during Blade Fury | -15 s Omnislash cooldown |
| 20 | +120 Blade Fury DPS | +15% Blade Dance critical damage |
| 25 | +40% Blade Dance lifesteal | +1 s Omnislash duration |

## Kit relationships

- **Attack chassis -> Blade Dance -> Omnislash:** the normal physical attack economy is amplified by crit and then re-executed at high density by the ultimate.
- **Blade Fury versus normal attacks:** historical branches repeatedly move the boundary between an independent protected magic-damage mode and the normal attack economy.
- **Healing Ward -> extended fight duration:** percentage sustain supports repeated normal attacks and repeated use of Juggernaut's temporary combat states, but the sustain source is exposed as a killable object.
- **Bladeform -> entry quality:** avoiding pre-fight damage increases Agility and movement speed before the main attack or special-state window begins.

## Compact design conclusions

- A normal-attack carry's special abilities need an explicit relationship to the public attack-growth system; they can exclude it, share selected parameters, or fully reuse it.
- A special combat state can create meaningful decisions simply by changing which parts of the normal combat rules are temporarily active.
- Strong sustain can preserve counterplay by being attached to a movable, destructible world object.
- A scalable carry ultimate can remain relevant by changing **how existing attacks are executed** rather than introducing an unrelated late-game damage formula.
- A high-level upgrade can increase flexibility by adding a low-commitment version of the same core state rather than only making one cast stronger.

These are case-supported observations, not yet cross-hero principles.

## Sources

Current and historical factual material was checked against:

- Liquipedia - Juggernaut: https://liquipedia.net/dota2/Juggernaut
- Liquipedia - Juggernaut Changelogs: https://liquipedia.net/dota2/Juggernaut/Changelogs
- Liquipedia - Juggernaut Old Abilities: https://liquipedia.net/dota2/Juggernaut/Old_Abilities
- Liquipedia - archived Juggernaut page: https://liquipedia.net/dota2/Archive:Juggernaut
- Liquipedia - Hero Attributes Table: https://liquipedia.net/dota2/Table_of_hero_attributes

A current-source inconsistency exists around Blade Dance text: some third-party ability descriptions still say Blade Dance affects Blade Fury, while the 7.41 patch explicitly removed the Bladestorm Blade Fury component. This case follows the patch record and treats Blade Fury critical integration as historical.

Where a historical mechanic had many balance-only parameter changes, this document records a representative or mature parameter set rather than reproducing the full patch chronology.
