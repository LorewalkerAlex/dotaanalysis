# Clockwerk - Hero Design Case

**Status:** First durable pass

**Current factual reference state:** Dota 2 7.41e. The latest direct changes are to Power Cogs: Mana Shock mana burn is 40/75/110/145, Clockwerk's self-attack push distance is 850/900/950/1000, and cogs no longer block neutral creep camps.

## Design identity

Clockwerk links global information, long-range self-deployment, and extremely local space control. Rocket Flare finds or checks distant areas, Hookshot deploys Clockwerk onto a unit from long range, Power Cogs reshapes the immediate battlefield, and Battery Assault is strongest when only a small number of enemies remain inside its short radius.

## Current combat chassis

| Property | Current value |
| --- | ---: |
| Primary attribute | Strength |
| Strength | 26 + 3.2 |
| Agility | 13 + 2.3 |
| Intelligence | 18 + 1.7 |
| Starting health | 692 |
| Starting health regeneration | 3.1/s |
| Starting mana | 291 |
| Starting mana regeneration | 0.9/s |
| Starting armor | about 3.17 |
| Starting attack damage | 50-52 |
| Attack type / range | Melee / 150 |
| Base attack speed | 100 |
| Base attack time | 1.7 s |
| Attack point | 0.33 s |
| Movement speed | 310 |
| Turn rate | 0.6 |
| Vision | 1800 / 800 |

**Current-source note:** DotaCoach's 7.41e stat table rounds starting armor to 3.2. Dotabuff currently displays 2.82. The comparison baseline here uses about 3.17, consistent with 1 base armor plus the current 13 Agility contribution.

Clockwerk was made Universal in 7.33 and returned to Strength in 7.38. The current 26 + 3.2 Strength chassis comes from that 7.38 rescaling.

## Armor Power - Innate

Current Armor Power grants **0.25% outgoing damage amplification per point of armor**.

Clockwerk can also consume Chainmail to permanently gain its +4 armor bonus. The effect stacks. In 7.41, the former Chainmeal Facet was folded into the Innate; each consumed Chainmail also increases model size by 3%, capped at +150% model size.

**Compact design note:** armor is a coupled defensive/offensive stat for Clockwerk. Permanent armor investment raises physical durability and also scales all outgoing damage through the Innate.

### Historical branch: Armor Power and Chainmail growth

- 7.36 introduced Armor Power at 0.3% outgoing damage per armor.
- 7.37 reduced the factor to the current 0.25%.
- 7.39 added the Chainmeal Facet, allowing Chainmail consumption for permanent armor.
- 7.41 removed the Facet system component and made Chainmail consumption part of Armor Power itself.

## Battery Assault

### Current factual baseline

| Property | Current value |
| --- | --- |
| Targeting | No target |
| Damage type | Magical |
| Radius | 275 |
| Duration | 10.5 s |
| Discharge interval | 0.7 s |
| Damage per discharge | 20 / 45 / 70 / 95 |
| Cooldown | 24 / 22 / 20 / 18 s |
| Mana cost | 75 / 80 / 85 / 90 |

Each discharge selects a random nearby enemy unit, deals damage, and applies a ministun. Battery Assault continues operating if Clockwerk himself is disabled and cannot be dispelled.

**Compact design note:** nearby enemy-unit count is part of the spell's effective output distribution. Isolating one target makes the random target selection much more concentrated; additional creeps, summons, illusions, or heroes can split the base spell's discharges.

### Current progression

- Level 15 talent: +25 Battery Assault damage per discharge.
- Level 25 talent: -0.25 s Battery Assault interval.
- Overclocking: radius becomes 330 and each discharge affects all enemies in range instead of one random target.

These upgrades separately modify per-event magnitude, event frequency, and targets-per-event.

## Power Cogs

### Current factual baseline

| Property | Current value |
| --- | --- |
| Targeting | No target |
| Formation radius | 215 |
| Duration | 5 / 6 / 7 / 8 s |
| Mana Shock damage | 55 / 110 / 165 / 220 |
| Mana burn | 40 / 75 / 110 / 145 |
| Extra damage | 50% of mana actually burned |
| Enemy attacks to destroy a cog | 2 |
| Clockwerk self-attack push distance | 850 / 900 / 950 / 1000 |
| Cooldown | 21 / 19 / 17 / 15 s |
| Mana cost | 75 |

Power Cogs forms a ring around Clockwerk. Cogs can shock invisible enemies. Since 7.41d, units without mana can still be damaged and pushed even though no mana can be burned.

Clockwerk can attack a cog once to push it outward. Since 7.41, he can also move freely through his own cogs; crossing one sinks that cog, and other units can then use the opened passage.

**Compact design note:** the ability creates temporary terrain-like objects rather than only applying a status effect. The ring can contain units, exclude units approaching from outside, be destroyed by enemy attacks, or be edited by Clockwerk through movement and self-attacks.

### Historical geometry and ownership branches

- 6.86 changed the formation from a rectangle to a circle.
- 7.33 made Cogs grant allied units inside a 50/100/150/200 magical damage barrier.
- 7.36 removed that ally barrier and changed Clockwerk's own cog attacks from destroying the cog to pushing it up to 1000 distance.
- 7.36 also introduced Expanded Armature, a Facet that enlarged the formation and could push enemies inside toward the center.
- 7.41 removed Expanded Armature and instead gave Clockwerk free movement through his own cogs, with crossed cogs sinking to open a path.

These branches change who benefits from the enclosed space and how much control Clockwerk has over the boundary after casting it.

## Rocket Flare

### Current factual baseline

| Property | Current value |
| --- | --- |
| Targeting | Global point target |
| Damage type | Magical |
| Impact radius | 600 |
| Damage | 80 / 120 / 160 / 200 |
| Movement slow | 100% for 0.4 s |
| Impact vision duration | 6 s |
| Cooldown | 20 / 18 / 16 / 14 s |
| Mana cost | 35 / 40 / 45 / 50 |

Rocket Flare gives Clockwerk a global information and chip-damage tool despite the rest of his base combat kit being extremely short-ranged.

Current talents extend the information role:

- Level 20: Rocket Flare grants True Sight.
- Level 25: Rocket Flare gains 3 charges.

## Hookshot

### Current factual baseline

| Property | Current value |
| --- | --- |
| Targeting | Point target projectile |
| Cast / travel range | 2000 / 2500 / 3000 |
| Hook speed | 4000 / 5000 / 6000 |
| Hook latch radius | 125 |
| Damage / stun radius | 175 |
| Damage | 75 / 175 / 275 |
| Stun duration | 1.2 / 1.4 / 1.6 s |
| Cooldown | 60 / 45 / 30 s |
| Mana cost | 100 / 125 / 150 |

Hookshot pierces debuff immunity. It can latch allied units and move Clockwerk to them without damaging or stunning the ally. Enemy units hit by the hook or by Clockwerk during travel can be stunned and damaged.

**Compact design note:** Hookshot solves access by moving Clockwerk's body to the fight rather than moving the enemy toward him. Because the projectile can latch units along its line, long range creates strong access but does not guarantee a target-locked destination.

### Historical Scepter branch: Hookshot-specific access

- 6.60 first added a Hookshot Scepter: it could latch allies and its cooldown became 20 seconds.
- 6.76 moved ally latching into the base ability and reduced the Scepter-upgraded cooldown to 12 seconds.
- 7.23 removed the Hookshot-specific Scepter in favor of Overclocking, shifting the major upgrade from one ability's access frequency to a whole-kit temporary state.

## Aghanim's Shard - Jetpack

Current Jetpack grants:

- 20% bonus movement speed;
- flying movement and flying vision;
- 6-second duration;
- 16-second cooldown;
- 75 mana cost;
- severely limited turning;
- inability to attack while active.

Since 7.40, Jetpack can be toggled on and off during its active window, with a 1-second toggle downtime. Current Jetpack also lets Clockwerk use targeted abilities and items without first facing the target location; a successful enemy Hookshot latch ends Jetpack.

Overclocking increases Jetpack's movement bonus to 40%.

## Aghanim's Scepter - Overclocking

### Current 7.41 branch

| Property | Current value |
| --- | --- |
| Duration | 18 s |
| Cooldown | 50 s |
| Mana cost | 90 |
| Post-buff penalty | 100% movement-speed and attack-speed slow for 3 s |

While active:

- **Battery Assault:** radius becomes 330 and all enemies in range are affected by each discharge.
- **Power Cogs:** effect radius becomes 330; Clockwerk's armor is multiplied by 1.25 while near a cog.
- **Rocket Flare:** fires two additional flares; damage, slow duration, and flying vision are multiplied by 1.35.
- **Hookshot:** effect radius and stun duration are multiplied by 1.5.
- **Jetpack:** movement bonus becomes 40%.

The Cogs armor increase also raises Armor Power's outgoing-damage amplification because the Innate reads current armor.

### Historical branch: generic overclock -> kit-specific overclock

**7.23 Overclocking:** the original Scepter replacement reset all ability cooldowns, gave +40% movement speed and +200 attack speed for 8 seconds, then stunned Clockwerk for 4 seconds.

**7.32 rework:** removed the cooldown reset and generic movement/attack-speed bonuses. The buff became 13 seconds and upgraded each Clockwerk ability separately: Battery Assault hit all enemies, Cogs granted +250 attack speed, Rocket Flare fired 3 rockets with a 3-second cooldown, and Hookshot gained +50% radius and stun duration. The post-buff self-stun was 3 seconds.

**7.35:** replaced the self-stun with a 3-second 100% movement-speed and attack-speed slow.

**7.41:** extended duration to 18 seconds, added the 330 Battery Assault radius, replaced the Cogs attack-speed bonus with the current 1.25 armor factor, and removed Rocket Flare's forced short cooldown in favor of +35% damage, slow duration, and flying vision.

The major historical change is from a generic temporary stat/reset mode to an ability-specific supermode whose bonuses alter the normal constraints of Clockwerk's kit.

## Current talents

| Level | Option A | Option B |
| --- | --- | --- |
| 10 | +75 Hookshot Damage | +1.5 Mana Regen |
| 15 | +25 Battery Assault Damage | -8 s Hookshot Cooldown |
| 20 | +80 Power Cogs Mana Burn | Rocket Flare True Sight |
| 25 | -0.25 s Battery Assault Interval | 3 Rocket Flare Charges |

The level-20 Cogs talent also indirectly increases Mana Shock damage when sufficient mana is available because shock damage includes 50% of mana actually burned.

## Removed 7.36-7.41 Facet branches

### Expanded Armature

Added in 7.36 for Power Cogs. It enlarged the cog formation and allowed the inner side of cogs to affect enemies, initially pushing caught enemies toward the center. Removed in 7.41.

### Hookup

Added in 7.36 for Hookshot. It specialized allied-unit Hookshots through a much shorter allied-use cooldown and larger local effect radius; later revisions added ally protection/armor and changed the exact trigger conditions. Removed in 7.41.

These Facets tested stronger specialization of Cogs as an arena and Hookshot as an ally-oriented movement/protection tool. The current 7.41 kit no longer keeps either branch.

## Whole-kit relationships

- **Rocket Flare -> information:** checks distant areas and supplies temporary vision.
- **Hookshot -> deployment:** moves a very short-range hero directly into a distant local fight.
- **Power Cogs -> local geometry:** creates and edits a temporary boundary around the deployment point.
- **Power Cogs -> Battery Assault:** isolation reduces the base spell's random-target dilution.
- **Armor Power -> commitment support:** armor investment simultaneously improves physical durability and outgoing damage.
- **Overclocking -> density reversal:** Battery Assault stops caring about target dilution and instead affects every enemy inside the enlarged local area.

## Main costs and counterplay

- **Hookshot path dependence:** the hook can latch another unit along its path rather than functioning as guaranteed target lock.
- **High commitment:** a successful Hookshot moves Clockwerk himself into the engagement; access is not the same as safety.
- **Battery Assault dilution:** without Overclocking, nearby extra enemy units split random discharges away from the preferred target.
- **Cogs are attackable:** enemies can spend two attacks to destroy a cog and open the boundary.
- **Cogs can be spatially bypassed or displaced around:** movement effects and the current sinking-cog rule mean the ring is temporary control, not an absolute prison.
- **Jetpack trades offense for movement:** flying repositioning disables normal attacks and limits turning.
- **Overclocking has a recovery window:** the 18-second supermode ends with a 3-second movement/attack-speed collapse.

## Compact case close

### Design identity

Clockwerk connects global information, long-range self-deployment, and very small-scale space control. His base fight pattern is strongest when he can isolate a target near himself; current Overclocking temporarily changes that rule by making Battery Assault affect every nearby enemy.

### Core mechanical relationships

- Rocket Flare -> find/check distant space.
- Hookshot -> deploy Clockwerk into that space.
- Power Cogs -> create a temporary local boundary.
- Fewer nearby enemies -> more concentrated base Battery Assault discharges.
- Armor -> durability + Armor Power outgoing damage.
- Overclocking -> larger local coverage and fewer base-kit restrictions.

### Case-level candidate lessons

- A random-nearby-target ability can make local unit density an important numerical input, letting space control change damage reliability without directly modifying damage values.
- Temporary terrain-like objects create counterplay through attacks, pathing, and forced movement rather than only through dispels.
- A major upgrade can change power allocation from frequency or generic stats into ability-specific coverage, reliability, and local rule changes.

These remain Clockwerk-specific observations until roster-wide comparison tests them against other designs.

## Sources

Current mechanics and values:

- https://www.dotabuff.com/heroes/clockwerk/abilities
- https://dotacoach.gg/en/heroes/clockwerk
- https://dotacoach.gg/en/heroes/stats
- https://liquipedia.net/dota2/Clockwerk
- https://liquipedia.net/dota2/7.41e

Historical branches:

- https://liquipedia.net/dota2/Clockwerk/Changelogs
- https://liquipedia.net/dota2/Clockwerk/Old_Abilities
- https://liquipedia.net/dota2/Version_6.76
- https://liquipedia.net/dota2/Version_6.86
- https://liquipedia.net/dota2/Version_7.23
- https://liquipedia.net/dota2/Version_7.32
- https://liquipedia.net/dota2/Version_7.33
- https://liquipedia.net/dota2/Version_7.36
- https://liquipedia.net/dota2/Version_7.41
