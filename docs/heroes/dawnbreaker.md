# Dawnbreaker - Hero Design Case

**Status:** First durable pass

**Current factual reference state:** Dota 2 7.41e. Dawnbreaker received no direct 7.41e change; the latest direct changes are 7.41d Starbreaker mana cost 100 -> 110, 7.41c base attack damage and Solar Guardian landing-stun reductions, and 7.41b Break of Dawn max-power base value 10% -> 8%.

## Design identity

Dawnbreaker links a local attack-driven sustain loop to global allied reinforcement. Starbreaker rapidly produces attack instances for Luminosity, Celestial Hammer supplies local access, and Solar Guardian lets Dawnbreaker deploy that melee/healing package to an allied fight anywhere on the map. The current Break of Dawn Innate makes Solar Guardian-created daytime a short offensive and healing power window.

## Current combat chassis

| Property | Current value |
| --- | ---: |
| Primary attribute | Strength |
| Strength | 25 + 3.4 |
| Agility | 14 + 1.7 |
| Intelligence | 20 + 2.0 |
| Starting health | 670 |
| Starting health regeneration | 3.0/s |
| Starting mana | 315 |
| Starting mana regeneration | 1.0/s |
| Starting armor | about 4.33 |
| Starting attack damage | 55-59 |
| Attack type / range | Melee / 150 |
| Base attack speed | 100 |
| Base attack time | 1.7 s |
| Attack point | 0.46 s |
| Movement speed | 300 |
| Turn rate | 0.6 |
| Vision | 1800 / 800 |

The current attack value follows the 7.41c reduction from 31-35 base damage to 30-34 base damage, producing 55-59 starting attack damage with 25 Strength.

**Current-source note:** Liquipedia/Table of Hero Attributes currently gives about 4.33 starting armor, while Dotabuff displays 3.96. The comparison baseline uses about 4.33 and preserves the display discrepancy for later roster-wide refresh.

## Break of Dawn - Innate

### Current factual baseline

Break of Dawn grants Dawnbreaker bonus base attack damage and day vision during daytime.

- Max base attack damage bonus: **8% + 1% per hero level**.
- Max day-vision bonus: **20%**.
- During ordinary daytime, the bonuses decrease through the day until reaching 0 at night.
- Solar Guardian creates Dawnbreaker's own daytime for **6 seconds**.
- During Dawnbreaker-created daytime, Break of Dawn remains at its current maximum power for the full duration.
- With Aghanim's Scepter, the current maximum Break of Dawn damage bonus also becomes heal amplification at a 1:1 factor.

**Compact design note:** the current Innate connects the global ultimate to the local attack/healing kit. Solar Guardian both moves Dawnbreaker to an allied fight and starts a six-second maximum-power window for base attack damage; Scepter extends the same scaling value into healing.

### Historical branches

**7.36-7.38c map-reveal Innate:** Break of Dawn originally revealed the map progressively over 4 seconds whenever the sun rose, with a 20000 maximum reveal radius and short vision/fog-return linger. It was primarily a global information mechanic.

**7.39 daytime combat scaling:** the Innate was reworked to grant up to 25% base attack damage and 20% vision during daytime, decaying toward zero by night.

**7.41 current linkage:** the damage bonus became level-scaled, Solar Guardian began creating six seconds of Dawnbreaker daytime, and self-created daytime keeps Break of Dawn at maximum power. 7.41b reduced the base term from 10% to the current 8%.

## Starbreaker

### Current factual baseline

| Property | Current value |
| --- | --- |
| Damage type | Physical / instant attacks |
| Total attack instances | 3 |
| Combo duration | 1.1 s |
| Interval | 0.55 s |
| Swipe / smash radius | 300 |
| Bonus damage per attack | 25 / 40 / 55 / 70 |
| Final-smash stun | 0.6 / 0.8 / 1.0 / 1.2 s |
| Self-stun after smash | 0.2 s |
| Cooldown | 17 / 15 / 13 / 11 s |
| Mana cost | 110 |

The sequence is two swipe attacks followed by one smash attack. Each component is a full instant-attack instance and can proc normal attack modifiers except cleave. Each Starbreaker attack grants **one Luminosity tally instance**, regardless of how many enemy units that swing hits. The instant attacks have True Strike.

Starbreaker is unavailable while Brightmaul is away after Celestial Hammer and while Dawnbreaker is channeling Solar Guardian.

**Compact design note:** Starbreaker compresses three attack events into a fixed 1.1-second action, directly accelerating Luminosity rather than only adding spell damage.

### Aghanim's Shard

Current Shard changes Starbreaker execution rather than directly increasing its damage:

- grants Debuff Immunity for the combo;
- grants **+50% magic resistance** during the combo;
- removes the base forced-forward movement and allows player-directed movement;
- applies a **35% movement-speed slow** while active;
- sets minimum movement speed to **215**;
- grants unobstructed/no-unit-collision movement for the sequence.

Historical Shard development:

- **7.30:** introduced as magic immunity during Starbreaker.
- **7.31-7.32:** moved toward free/player-directed movement during the combo.
- **7.32c:** added the movement-speed penalty and 215 minimum speed.
- **7.33:** the modern Debuff Immunity / magic-resistance form replaced the older magic-immunity model.
- **7.38:** self movement-speed slow increased from 25% to the current 35%.

## Celestial Hammer and Converge

### Current factual baseline

| Property | Current value |
| --- | --- |
| Max throw distance | 700 / 900 / 1100 / 1300 |
| Hammer speed | 1600 |
| Contact damage radius | 200 |
| Contact damage | 50 / 80 / 110 / 140 |
| Fire-trail radius | 200 |
| Fire-trail damage per second | 20 / 30 / 40 / 50 |
| Fire-trail slow | 24% / 28% / 32% / 36% |
| Fire-trail duration | 2.5 / 3 / 3.5 / 4 s |
| Hammer pause duration | 2 s |
| Converge speed | 1600 |
| Cooldown | 18 / 16 / 14 / 12 s |
| Mana cost | 100 / 110 / 120 / 130 |

Brightmaul damages enemies along its route and creates a damaging, slowing fire trail. While the hammer is away, Converge replaces Celestial Hammer. Converge pulls Dawnbreaker and Brightmaul toward each other so they meet in the middle, with both sides creating fire trail during the movement.

Starbreaker is inactive until Brightmaul returns/converges. Solar Guardian is inactive while Brightmaul is still traveling outward. Once Converge is available, casting Solar Guardian immediately recalls the hammer.

Current level-10 talent makes the fire trail grant allied units movement speed equal to the trail's **24/28/32/36%** movement modifier. Level 15 can instead multiply Hammer contact and fire-trail damage by **1.4**. Level 25 can multiply Hammer max distance and speed by **1.8**.

### Historical team-utility branches

**Gleaming Hammer (7.36-7.37):** increased hammer pause duration by 2 seconds and made the grounded hammer emit a 200-radius Solar Guardian aura at a 0.5 value factor.

**Trailblazer (7.38-7.40):** fire-trail cells granted allied movement speed, initially 10/15/20/25% with a 1-second linger. 7.41 removed the component from the base/Facet system, while an allied-movement version survives as the current level-10 talent.

## Luminosity

### Current factual baseline

| Property | Current value |
| --- | --- |
| Full attack cycle | 4 attacks (3 with level-20 talent) |
| Critical strike | 125% / 150% / 175% / 200% |
| Self heal from powered attack | 35% / 40% / 45% / 50% |
| Ally-heal radius | 650 |
| Ally heal | 50% of Dawnbreaker's Luminosity heal |
| Creep/neutral heal factor | 0.6 |

The first three successful attack events fill the base tally; the next successful attack is the powered Luminosity attack. The level-20 talent reduces the full cycle from four attacks to three. Dotabuff labels the base requirement as 3 because it counts only the charge-building attacks, while Liquipedia displays the complete powered-attack cycle as 4; the underlying sequence is the same.

The powered attack is a guaranteed critical strike. Dawnbreaker's heal is based on the powered attack's post-reduction damage, and nearby allied heroes receive half of that healing amount. Each Starbreaker instant attack advances the tally once.

Break disables new tally gain and the healing component, but existing tally progress is not removed.

**Compact design note:** attack damage, attack-event frequency, and access to targets jointly control both Dawnbreaker's offensive output and her local sustain.

### Historical branch: Solar Charged

Added in 7.36, Solar Charged reduced all Dawnbreaker ability cooldowns by **1 second** whenever Luminosity's powered attack occurred; 7.39d reduced the amount to **0.8 seconds**. It did not affect item abilities. The component was removed in 7.41.

This branch created a direct loop from successful attack cycles back into ability frequency; the current kit no longer keeps that cooldown-acceleration layer.

## Solar Guardian

### Current factual baseline

| Property | Current value |
| --- | --- |
| Targeting | Global area near an allied hero |
| Allied-hero search distance from chosen point | 1400 |
| Max landing offset from chosen allied hero | 350 |
| Effect / landing radius | 500 |
| Pulse interval | 0.5 s |
| Base pulse count before landing | 5 |
| Damage per pulse | 30 / 50 / 70 |
| Heal per pulse | 45 / 70 / 95 |
| Landing damage | 130 / 160 / 190 |
| Channel time | 1.7 s |
| Flight duration | 0.8 s |
| Landing stun | 1.2 / 1.4 / 1.6 s |
| Cooldown | 110 / 100 / 90 s |
| Mana cost | 150 / 200 / 250 |
| Dawnbreaker daytime created | 6 s |

Solar Guardian requires a valid allied hero near the selected map point. The landing location can be placed up to 350 units from that allied hero. Once selected, the landing point is fixed and does **not** follow the allied hero.

The aura begins pulsing immediately during channel/flight, before Dawnbreaker arrives. After the channel succeeds, Dawnbreaker becomes hidden/unselectable and travels to the locked landing point; on arrival she damages and stuns enemies in the landing area.

The spell creates six seconds of Dawnbreaker daytime from cast start, keeping Break of Dawn at full power during that period.

**Compact design note:** Solar Guardian is global reinforcement rather than free global teleport: allied presence authorizes the destination, the 2.5-second channel-plus-flight delay telegraphs the response, and the destination is committed before the fight finishes evolving.

### Aghanim's Scepter - current branch

Current Scepter:

- grants heal amplification equal to Break of Dawn's current maximum bonus value;
- makes Solar Guardian's aura follow Dawnbreaker for **2 seconds after landing**;
- adds **4 post-landing pulse instances** at the normal 0.5-second interval.

### Historical Scepter branches

**7.30 initial Scepter:** reduced channel time to 1 second, increased heal per pulse to 60/90/120, added 60% ally evasion while Dawnbreaker was airborne, increased airborne duration by 3.5 seconds, and allowed early landing.

**7.32 movable landing point:** Solar Guardian Land allowed the landing area to be moved at 200 speed while airborne.

**7.38 arrival-oriented rework:** removed the movable landing point, early-landing sub-ability, ally evasion, and long airborne extension. The Scepter instead shortened channel/flight time, retained a smaller heal bonus, and made the aura follow Dawnbreaker for 3 seconds after landing.

**7.39e-7.41 current direction:** post-landing aura linger fell to 2 seconds; 7.40 removed the channel/flight reductions; 7.41 removed direct per-pulse heal bonus and tied Scepter heal amplification to Break of Dawn instead.

## Removed 7.38-7.41 secondary components

### Starsurge

Added to Starbreaker in 7.38. After the final smash, nearby allies within 700 received attack-speed bonuses and Dawnbreaker received a larger self attack-speed bonus for 4 seconds. It was removed in 7.41.

### Trailblazer

Added to Celestial Hammer in 7.38. Fire trail granted allied movement speed with a 1-second linger. It was removed as a component in 7.41; allied fire-trail movement speed remains available through the current level-10 talent.

### Solar Charged

Added to Luminosity in 7.36. Powered Luminosity attacks reduced Dawnbreaker's ability cooldowns. It was removed in 7.41.

The 7.41 rework removed these separate Q/W/E secondary layers while making Solar Guardian directly create the maximum-power Break of Dawn state.

## Current talents

| Level | Option A | Option B |
| --- | --- | --- |
| 10 | Celestial Hammer grants allies move speed | +25% Luminosity Critical Damage |
| 15 | -20 s Solar Guardian Cooldown | x1.4 Celestial Hammer Contact Damage / Damage per Second |
| 20 | -1 Luminosity Attacks Required | +150 Solar Guardian Radius |
| 25 | x1.8 Celestial Hammer Max Distance / Speed | -4 s Starbreaker Cooldown |

The level-20 Solar Guardian radius talent increases the effect radius from 500 to 650. The level-20 Luminosity talent changes the full powered-attack cycle from four successful attacks to three.

## Whole-kit relationships

- **Celestial Hammer -> local access:** creates a ranged anchor, slow zone, and midpoint movement into melee range.
- **Starbreaker -> attack-event compression:** three instant attacks advance Luminosity rapidly.
- **Luminosity -> attack-to-sustain conversion:** the powered attack converts successful physical damage into self healing and nearby ally healing.
- **Solar Guardian -> global reinforcement:** an allied hero supplies the destination condition; pulses begin before Dawnbreaker's body arrives.
- **Solar Guardian -> Break of Dawn:** the ultimate creates six seconds of personal daytime, fixing the Innate at maximum power for the landing fight.
- **Scepter -> shared scaling:** Break of Dawn's maximum attack-damage bonus also becomes heal amplification.

## Main costs and counterplay

- **Melee access remains necessary:** Luminosity sustain depends on successful attack events; kiting and displacement reduce both damage and healing throughput.
- **Starbreaker is a committed sequence:** without Shard, forced movement/facing and disable interactions can prevent all three attack instances from being realized.
- **Break cuts the sustain loop:** it stops new Luminosity tally gain and removes Luminosity healing while active.
- **Celestial Hammer creates a temporary weapon-state restriction:** Starbreaker cannot be used while Brightmaul is away, so ranged hammer use can delay the main melee combo until Converge/return.
- **Solar Guardian is delayed and destination-locked:** global range is balanced by a 1.7-second channel, 0.8-second flight, visible target area, allied-anchor requirement, and a landing point that does not track moving allies.
- **Global access is reinforcement rather than independence:** without an allied hero near the chosen location, Solar Guardian cannot establish a destination.

## Compact case close

### Design identity

Dawnbreaker uses attacks as both offense and sustain, then uses Solar Guardian to deploy that local melee/healing package into allied fights across the map. The current Break of Dawn structure makes Solar Guardian-created daytime the bridge between global reinforcement and the post-landing attack/heal loop.

### Case-level candidate observations

- Attack-count passives can be accelerated by active abilities that generate real attack events rather than special-case stack grants.
- Healing derived from attack damage can let offensive scaling and sustain scaling share one numerical input.
- Global mobility can retain prediction and counterplay through allied destination requirements, visible delay, and a fixed landing point.

These remain Dawnbreaker-specific observations until roster-wide comparison tests them against other heroes.

## Sources

Current mechanics and values:

- https://liquipedia.net/dota2/Dawnbreaker
- https://liquipedia.net/dota2/Table_of_hero_attributes
- https://www.dotabuff.com/heroes/dawnbreaker/abilities
- https://dotacoach.gg/en/heroes/dawnbreaker
- https://liquipedia.net/dota2/7.41

Historical branches:

- https://liquipedia.net/dota2/Dawnbreaker/Changelogs
- https://liquipedia.net/dota2/Dawnbreaker/Old_Abilities
- https://liquipedia.net/dota2/Version_7.30
- https://liquipedia.net/dota2/Version_7.32
- https://liquipedia.net/dota2/Version_7.36
- https://liquipedia.net/dota2/Version_7.38
- https://liquipedia.net/dota2/Version_7.41
