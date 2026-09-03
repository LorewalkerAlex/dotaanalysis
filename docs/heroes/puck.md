# Puck - Hero Design Case

**Status:** First durable pass

**Current factual reference state:** Dota 2 7.41e. The general Puck page is still marked 7.41d, so the 7.41e Illusory Orb cooldown change is applied separately below. Historical material is organized by design branch rather than by patch chronology.

## Design identity

Puck is a fragile ranged spellcaster whose survival and control come primarily from changing position or temporarily leaving ordinary interaction rather than from a durable combat chassis. Illusory Orb creates a moving future position, Waning Rift supplies immediate short-range relocation plus silence, Phase Shift avoids interaction without moving, and Dream Coil constrains enemy movement by making departure costly. Puckish turns successful projectile avoidance into health and mana, reinforcing repeated use of those evasive tools.

## Current combat chassis

| Property | Current value |
| --- | ---: |
| Primary attribute | Intelligence |
| Strength | 17 + 2.4 |
| Agility | 14 + 2.1 |
| Intelligence | 23 + 3.8 |
| Starting health | 494 |
| Starting health regeneration | 2.2/s total, including 0.5 base |
| Starting mana | 351 |
| Starting mana regeneration | 1.65/s total, including 0.5 base |
| Starting armor | 2.33 |
| Starting attack damage | 45-53 |
| Attack type / range | Ranged / 550 |
| Projectile speed | 900 |
| Base attack speed | 100 |
| Base attack time | 1.7 s |
| Attack animation | 0.5 + 0.8 s |
| Movement speed | 290 |
| Turn rate | 0.9 |
| Vision | 1800 / 800 |

### Compact note

The base chassis does not provide the survival pattern associated with Puck. Low starting health, modest armor, and ordinary movement speed leave the hero vulnerable when its active avoidance and relocation tools are unavailable or disabled.

## Puckish

### Current factual baseline - Innate

- Passive and breakable.
- Disjointing an incoming attack projectile restores **3% of Puck's maximum health** and **3% of maximum mana**.
- Disjointing an incoming spell projectile uses a **3x** restore factor, for **9% max health and mana** before talent modification.
- Missed attacks and Tower attacks do not count.
- Level 15 talent adds **2 percentage points** to the base health and mana restore, producing 5% base restoration before the spell-projectile factor.

### Design branch: successful avoidance becomes a resource source

The innate changes a successful defensive action from only preventing loss into creating future casting resources. Because Puck's other abilities can disjoint projectiles, avoidance and spell availability can reinforce one another.

### Historical design branch: fixed plus percentage restoration

Puckish originally used **2% max health and mana** per qualifying attack projectile with a **3x** spell-projectile factor. The spell factor later reached **4x**. A later branch added a flat restoration floor on top of the 2% value: first **20 + 2%**, later **15 + 2%**, and then **10 + 2%** before 7.41 returned the ability to pure percentage scaling at 3%.

**Compact design note:** a flat component makes the same successful dodge relatively more valuable on a low-health early-game chassis, while pure percentage scaling preserves proportional value as the hero grows.

## Illusory Orb

### Current factual baseline

| Property | Value |
| --- | --- |
| Cast | Point / vector target |
| Damage type | Magical |
| Travel distance | 1950 |
| Damage radius | 225 |
| Projectile speed | 750 |
| Impact damage | 70 / 140 / 210 / 280 |
| Additional damage | 3% of Orb spell damage every 0.5 s within the radius |
| Cooldown | 12 / 11 / 10 / 9 s |
| Mana cost | 90 / 100 / 110 / 120 |
| Vision | 450-radius flying vision, lingering 2.5 s |
| Level 10 talent | +35 impact damage |

The normal cast is vector-targeted and can curve. Alt-Cast launches a straight Orb instead.

### Ethereal Jaunt

- Becomes available while an Illusory Orb exists.
- Teleports Puck to the current location of the active Orb.
- Disjoints incoming projectiles on use.
- Root disables Ethereal Jaunt.

### Historical design branch: straight committed trajectory

For most of Puck's history, Illusory Orb traveled on a straight line. A representative mature geometry used the same **1950** travel distance and **225** radius, with **550** projectile speed immediately before Curveball became available.

**Compact design note:** the visible moving projectile publishes a future location that Puck may choose to occupy. The destination is optional, but the available route is created in advance rather than chosen at the instant of escape.

### Historical design branch: Curveball facet

Curveball added vector targeting so the Orb could travel on a curved path, increased projectile speed to **750**, and used a **2x duration factor**. The branch later added repeated damage inside the Orb radius, first at **5%** of spell damage per 0.5-second interval and later **3%**.

### Current design branch: optional branch absorbed into the base ability

When Facets were removed in 7.41, Curveball as a separate component disappeared but its defining geometry became the base Orb: curved vector targeting is standard, straight travel is retained through Alt-Cast, speed remains 750, and the 3% interval damage remains.

**Compact design note:** the current version increases route ambiguity without removing the precommitted moving-anchor structure. The opponent sees the Orb and can reason about its changing path, while Puck still must decide whether to consume that prepared position.

## Waning Rift

### Current factual baseline

| Property | Value |
| --- | --- |
| Cast | Area target |
| Damage type | Magical |
| Max teleport distance | 350 |
| Effect radius | 400 |
| Damage | 60 / 120 / 180 / 240 |
| Silence duration | 2 / 2.5 / 3 / 3.5 s |
| Cooldown | 16 / 15 / 14 / 13 s |
| Mana cost | 100 / 110 / 120 / 130 |
| Level 10 talent | +1.25 s silence duration |
| Level 15 talent | +60 damage |
| Level 20 talent | -2.5 s cooldown |
| Level 25 talent | +350 radius and max teleport distance |

Puck teleports first and applies the damage and silence around the destination. Root prevents the teleport component.

### Historical design branch: stationary self-centered silence

Waning Rift was originally a no-target area spell centered on Puck rather than a movement ability. Its long-running core was still a **400-radius** magical damage plus silence effect, but reaching the desired control position had to be solved by another action.

### Current design branch: control also supplies access

Since the area-target rework, the ability can move Puck a short distance before producing its control area. The spell therefore both solves access to the desired location and commits Puck to that location.

**Compact design note:** attaching movement to a local control spell changes the access cost. Puck no longer needs a separate movement action to place the silence, but casting the silence also changes Puck's own position and exposure.

### Historical design branch: knockback and True Sight upgrade

A Shard branch added **70 bonus damage**, pushed enemies **250** distance from the center over **0.4 s**, and applied a **5 s** True Sight debuff. A later Scepter version expanded Waning Rift to **550 radius** and **550 max distance**, increased the displacement to **400**, and retained the 5-second reveal.

**Compact design note:** this branch turned a silence into a stronger geometry-management tool and information tool rather than only increasing its damage.

### Historical design branch: Jostling Rift

The removed Jostling Rift facet added short forced movement to Waning Rift:

- Default mode pushed enemies **75 / 100 / 125 / 150** distance over **0.3 s**.
- Alt-Cast switched the direction and pulled enemies toward Puck by the same distance.
- The displacement did not interrupt channeling abilities or enemy orders.

**Compact design note:** push/pull choice changed relative positioning without converting the spell into a hard displacement interrupt. The branch was removed when Facets were removed in 7.41.

## Phase Shift

### Current factual baseline

| Property | Value |
| --- | --- |
| Cast | No target / channeled |
| Max duration | 1 / 1.75 / 2.5 / 3.25 s |
| Cooldown | 8 / 7.5 / 7 / 6.5 s |
| Mana cost | 0 |
| Cast point | 0.01 s |

On cast, Phase Shift disjoints incoming projectiles. During the channel Puck is hidden, invulnerable, unselectable, and out of game. Issuing another action ends the channel. Root does not disable Phase Shift.

### Design branch: active temporary exit from interaction

Unlike Illusory Orb or Waning Rift, Phase Shift does not solve danger by moving Puck. It instead creates a bounded period in which ordinary targeting and damage interaction cannot reach the hero.

**Compact design note:** Puck has multiple defensive tools that fail differently. Root can close the teleport components of Jaunt and Waning Rift while leaving Phase Shift available; waiting out Phase Shift can preserve the opponent's ability to punish Puck when it returns.

### Historical design branch: automatic defensive response

Early Phase Shift supported Autocast and cost **50 / 40 / 30 / 20 mana**. In 6.74 Autocast was removed, mana cost became 0, and the level-4 duration reached **3.25 s**.

**Compact design note:** removing Autocast moved avoidance reliability from a system response toward player timing. The ability became cheaper to activate but more dependent on recognizing and responding to threats correctly.

### Design branch: instant attacks attached to the defensive action

Instant attacks during Phase Shift first appeared as a talent. The effect later moved to Aghanim's Shard, initially attacking enemies within Puck's attack range plus a **200** buffer. The buffer was later removed.

**Current Shard**

- Casting Phase Shift performs an instant attack on each valid enemy within Puck's current attack range.
- Puck's successful attacks gain **20 bonus magical damage**.
- The instant attacks can use normal attack modifiers and on-attack effects.

**Compact design note:** the upgrade lets a defensive exit action also spend the hero's attack economy. It adds offensive value to successful defensive timing without replacing the core Phase Shift behavior.

## Dream Coil

### Current factual baseline

| Property | Value |
| --- | --- |
| Cast | Point target |
| Cast range | 750 |
| Latch radius | 375 |
| Initial damage | 175 / 250 / 325 magical |
| Coil duration | 5 / 5.5 / 6 s |
| Link break distance | 600 |
| Link break damage | 200 / 300 / 400 magical |
| Link break stun | 1.5 / 2 / 2.5 s |
| Cooldown | 75 s |
| Mana cost | 125 / 175 / 225 |
| Debuff immunity | Does not pierce in the current base state |
| Level 20 talent | +200 initial and link-break damage |
| Level 25 talent | -30 s cooldown |

The cast leashes enemy heroes within the initial radius. The leash prevents affected heroes from using many teleportation and mobility abilities. An enemy may remain inside the allowed distance or move far enough away to snap the Coil and take the additional damage and stun.

### Design branch: movement remains available but becomes costly

Dream Coil does not simply immobilize the target for its full duration. It preserves movement inside a bounded region and allows the target to leave by accepting a known break penalty.

**Compact design note:** the control creates a movement decision rather than deleting movement altogether. Enemy priorities, incoming danger, and available defensive resources determine whether remaining constrained or deliberately breaking is preferable.

### Historical design branch: immediate interrupt on attachment

Dream Coil historically applied a **0.5 s** stun on cast in addition to its leash and break behavior. That initial stun was removed in 7.30.

**Compact design note:** removing the immediate stun makes the ability less of an instant interrupt and places more of its control value on the continuing spatial rule.

### Historical design branch: damage concentrated on breaking the boundary

A 7.07-era branch removed the **100 / 150 / 200** initial damage and raised link-break damage to **300 / 400 / 500**. Initial damage was later restored, beginning at 100/150/200 in the 7.23 rework and eventually reaching the current split.

**Compact design note:** concentrating more of the damage on link break increases the price difference between obeying and violating the spatial constraint. Splitting damage between attachment and break gives the cast reliable immediate value even when no enemy snaps the Coil.

### Historical Aghanim branch: stronger boundary enforcement

A mature older Scepter branch made Dream Coil a stricter version of the same control rule:

- Coil duration increased to **8 s**.
- Link-break damage reached **300 / 450 / 600**.
- Link-break stun reached **2 / 3 / 4 s**.
- Link-break damage and stun could pierce spell immunity.

### Current Aghanim branch: Coil reuses Puck's attack system

The current Scepter makes Dream Coil perform repeated instant attacks against affected enemy heroes. The branch began with a fixed **0.6 s** attack interval, then changed to use Puck's current attack rate. The current attack-rate divisor is **0.9**, and attacks continue against enemies during the break stun.

The attacks are sourced to Puck, use the normal attack system and modifiers, and do not require Puck to remain near the Coil.

**Compact design note:** the upgrade transforms a spatial control state into an attack-delivery window. Attack damage, attack speed, and attack modifiers can therefore gain value inside a hero whose base kit is otherwise dominated by spells and movement.

## Current talents

| Level | Left | Right |
| --- | --- | --- |
| 10 | +1.25 s Waning Rift silence duration | +35 Illusory Orb damage |
| 15 | +60 Waning Rift damage | +2% Puckish max health/mana restore |
| 20 | +200 Dream Coil initial/break damage | -2.5 s Waning Rift cooldown |
| 25 | +350 Waning Rift radius/max distance | -30 s Dream Coil cooldown |

## Kit relationships

- **Illusory Orb -> Ethereal Jaunt:** Puck creates a visible moving future position before deciding whether to occupy it.
- **Waning Rift -> access plus control:** short relocation and local silence are one committed action rather than two separate actions.
- **Phase Shift -> Puckish:** a correctly timed defensive disjoint can both prevent damage and restore resources for later spells.
- **Different escape failure modes:** Root disables Jaunt and the teleport component of Waning Rift but does not disable Phase Shift, so one status does not erase every defensive tool in the same way.
- **Dream Coil -> movement pressure:** the enemy retains movement but must decide whether leaving the allowed region is worth damage and stun.
- **Shard/Scepter -> attack integration:** Phase Shift and Dream Coil upgrades both reuse Puck's ordinary attacks inside spell-defined states.

## Compact design conclusions

- A fragile chassis can remain playable through **active, differently constrained avoidance tools** rather than passive durability.
- Mobility can carry meaningful commitment when the player creates a future destination before deciding to use it; route flexibility can increase uncertainty without removing that commitment.
- Strong spatial control does not have to forbid movement. Dream Coil creates decisions by allowing movement while attaching an explicit cost to crossing a boundary.
- Successful avoidance can be made part of a resource loop, so defensive skill directly supports future offensive or evasive actions.
- Optional upgrades can connect an attack system to spell-defined states without making ordinary attacks the base kit's primary identity.

These are case-supported observations, not yet cross-hero principles. Later cases should test whether the distinctions between delayed movement, immediate displacement, and temporary non-interaction remain useful outside Puck.

## Sources

Current and historical factual material was checked against:

- Liquipedia - Puck: https://liquipedia.net/dota2/Puck
- Liquipedia - Puck Changelogs: https://liquipedia.net/dota2/Puck/Changelogs
- Liquipedia - Hero Attributes Table: https://liquipedia.net/dota2/Table_of_hero_attributes
- Liquipedia - Version 7.41e: https://liquipedia.net/dota2/7.41e
- Liquipedia - Version 7.39c: https://liquipedia.net/dota2/7.39c
- Liquipedia - Version 7.36: https://liquipedia.net/dota2/7.36

The current Puck overview is marked 7.41d and still shows two stale values. The 7.41e patch increased Illusory Orb cooldown from 11/10/9/8 to **12/11/10/9**. The overview also displays **25** magical attack damage for the Phase Shift Shard, while the 7.39c changelog explicitly reduced that value from 35 to **20** and no later Puck change restores it through 7.41e. This case therefore records 12/11/10/9 for Orb cooldown and 20 for the Shard attack bonus.

Where a historical mechanic had many balance-only parameter changes, this document records a representative or mature parameter set rather than reproducing the full patch chronology.
