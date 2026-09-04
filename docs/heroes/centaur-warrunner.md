# Centaur Warrunner - Hero Design Case

**Status:** First durable pass

**Current factual reference state:** Dota 2 7.41e. The latest direct Centaur changes in this reference state reduced Retaliate's Strength scaling to 14%/21%/28%/35% and reduced the Aghanim's Shard Double Edge Strength-buff duration to 12 seconds.

## Design identity

Centaur Warrunner turns a large Strength-built body into a multi-purpose combat resource. Strength increases his ordinary health and attack damage, but also feeds Horsepower movement speed, Double Edge damage, Retaliate damage, and Stampede damage. His kit then asks the player to move that body into valuable positions: Hoof Stomp converts body placement into control, Double Edge actively spends health margin for damage, and Retaliate makes attack-based attempts to remove that health pay an extra price.

The compact design idea is not simply "high HP tank." Centaur is strongest when a large health body is delivered to the right place and then consumed efficiently by either side.

## Current combat chassis

| Property | Current value |
| --- | ---: |
| Primary attribute | Strength |
| Strength | 28 + 4.3 |
| Agility | 15 + 1.0 |
| Intelligence | 15 + 1.6 |
| Starting health | 736 |
| Starting mana | 255 |
| Starting health regeneration | 5.8/s |
| Starting mana regeneration | 0.75/s |
| Starting armor | 0.5 |
| Starting attack damage | 64-66 |
| Attack type / range | Melee / 150 |
| Base attack speed | 90 |
| Base attack time | 1.7 s |
| Attack animation | 0.3 + 0.3 s |
| Movement speed | 300 |
| Turn rate | 0.6 |
| Vision | 1800 / 800 |

**Source note:** current DotaCoach and Liquipedia data support 0.5 starting armor; current Dotabuff displays 0.1. This case uses 0.5 and records the disagreement rather than treating all current sources as identical.

## Core numerical design - Strength as a common input

Centaur adds several hero-specific conversions on top of normal Strength benefits:

| System | Current Strength relationship |
| --- | --- |
| Horsepower | +0.4 flat movement speed per Strength; does not stack with Boots-of-Speed-based movement bonus |
| Double Edge | +60% / 90% / 120% / 150% current Strength as magical damage |
| Retaliate | +14% / 21% / 28% / 35% Strength as physical return damage |
| Stampede | 2 / 2.5 / 3 x Centaur Strength as magical trample damage |

This makes Strength a shared numerical input for durability, movement access, active burst, retaliation, and team initiation damage instead of merely being a defensive stat.

## Body placement and control

### Hoof Stomp

| Property | Current value |
| --- | --- |
| Radius | 325 |
| Damage | 70 / 140 / 210 / 280 magical |
| Stun | 1.6 / 1.8 / 2 / 2.2 s |
| Windup | 0.5 s |
| Cooldown | 18 / 16 / 14 / 12 s |
| Mana | 100 / 110 / 120 / 130 |

Centaur can move during the 0.5-second windup but is disarmed. The key design consequence is that hard control remains tied to where Centaur's body actually arrives: the player gets a short correction window, while the opponent gets a visible response window.

The 7.34 rework replaced an ordinary 0.5-second cast point with the current delayed stomp model, making movement during commitment part of the spell rather than requiring Centaur to stand still before the effect.

## Health as an active resource

### Double Edge

| Property | Current value |
| --- | --- |
| Cast range | 175 |
| Damage radius | 220 |
| Base damage | 120 / 180 / 240 / 300 |
| Strength damage | 60% / 90% / 120% / 150% current Strength |
| Damage type | Magical |
| Cooldown | 3.5 s |
| Mana | 0 |
| Self-damage | Equal magical self-damage; non-lethal |

Double Edge makes Centaur's health pool an active budget. More Strength both raises the damage and increases the health/regen capacity available to absorb repeated self-damage. The cost remains real even though Double Edge cannot directly kill Centaur: spending too much health lowers the amount of enemy pressure he can safely absorb afterward.

### Aghanim's Shard - enlarge the whole Strength system

Current Shard adds a 25% movement slow for 2 seconds and grants a temporary percentage Strength bonus for each enemy hero hit, stacking up to five times; the buff lasts 12 seconds and refreshes as stacks are added.

**Current-source discrepancy:** Liquipedia's 7.36b changelog explicitly reduced the Strength gain from 15% to **12% per enemy hero**, and no later reversion was found. Some current tooltip pages still display 15%. This case therefore uses **12% per hero, up to +60% at five stacks**, while preserving the discrepancy for future refresh.

The large-design idea is more important than the exact temporary percentage: successful multi-hero contact temporarily enlarges the same Strength input that already feeds Centaur's health, movement, Double Edge, Retaliate, Stampede, and attacks.

## Making attack-based tanking costly

### Retaliate

| Property | Current value |
| --- | --- |
| Trigger | Successful attacks against Centaur |
| Base return damage | 15 / 25 / 35 / 45 |
| Strength scaling | 14% / 21% / 28% / 35% Strength |
| Damage type | Physical reflected damage |
| Buildings | Half damage |
| Break | Passive is breakable |

Retaliate does not reduce incoming damage and does not force enemies to attack Centaur. Instead, it taxes attack events used to remove his large health pool. This makes high health useful not only because Centaur survives longer, but because surviving more attack events gives the retaliation rule more opportunities to matter.

This also leaves clear counterplay: spell-heavy damage, kiting, displacement, or Break can reduce the value of the attack-tax model without needing to defeat Centaur at his preferred exchange.

## Moving the body - from personal access to team access

### Horsepower - Innate

Current Horsepower converts 40% of Centaur's Strength into flat movement speed and raises his maximum movement-speed ceiling to 575. The Boots-of-Speed-based movement bonus does not stack with this bonus.

The important structural role is simple: a short-range, body-centered kit needs a way to make its growing body easier to deliver. Horsepower lets the same Strength that makes Centaur larger also improve access.

### Stampede

| Property | Current value |
| --- | --- |
| Duration | 3.5 / 4 / 4.5 s |
| Ally movement | 550 haste-like movement and unit phasing |
| Trample damage | 2 / 2.5 / 3 x Centaur Strength |
| Trample slow | 100% movement slow for 3 s |
| Trample radius | 105 |
| Cooldown | 100 / 95 / 90 s |
| Mana | 150 / 200 / 250 |

Stampede turns Centaur's personal access problem into a team-wide movement capability. Allies still control their own movement, but Centaur supplies the speed state; the collision damage continues to read Centaur's Strength, keeping the ultimate attached to his numerical identity.

The same ability supports engagement, chase, retreat, and repositioning, so using it defensively also spends the next opportunity to force a fight.

## Aghanim's Scepter - body as a transport platform

Current Scepter grants **Work Horse**:

- Centaur creates a cart for 6 seconds and gains his current Stampede effect.
- Work Horse costs 75 mana and has a 35-second cooldown.
- During the cart window, **Hitch A Ride** can target an allied hero within 250 range.
- The rider becomes invulnerable and untargetable, can still attack and cast, but cannot move independently.
- Melee riders gain +200 attack range.

The upgrade takes the body/access theme literally: another hero can temporarily hand movement control to Centaur while keeping combat actions. The 7.32 Scepter first introduced Hitch A Ride as a direct transport ability; 7.34 reorganized it around Work Horse, making Centaur enter a temporary vehicle state before choosing a rider.

## Current talents

| Level | Option A | Option B |
| --- | --- | --- |
| 10 | +15 Movement Speed | +4 Health Regen |
| 15 | +30% Double Edge Strength Damage | +10 Strength |
| 20 | -25s Stampede Cooldown | +45 Retaliate Damage |
| 25 | +1s Hoof Stomp Duration | Gains Retaliate Aura |

The talent tree mostly reinforces existing numerical questions rather than creating separate subsystems: access versus recovery, stronger Strength conversion versus more Strength input, more frequent team access versus a higher attack tax, and stronger local control versus exporting Retaliate to allies.

## Meaningful historical design branches

### Insult -> Double Edge - forced aggro to self-funded threat

Before 5.58, **Insult** issued nearby enemies an attack order on Centaur. 5.58 replaced it with Double Edge, shifting the tanking model from directly asking enemies to attack the tank toward creating enough close-range threat that opponents must decide how to handle him.

### 6.63 - health becomes the main Double Edge payment

Early Double Edge had a mana cost and lethal self-damage. In 6.63 its mana cost was removed and the self-damage became non-lethal. This made health capacity, rather than mana, the defining repeat-use cost.

### Great Fortitude -> Stampede - self magnitude to team access

Before 6.76, **Great Fortitude** passively granted 15/30/45 Strength. 6.76 replaced it with Stampede. The old ultimate spent power budget on making Centaur himself numerically larger; the new ultimate converted Centaur's Strength identity into a team-wide spatial capability.

### Retaliate 7.20-7.27b - store tanking history, then cash it out

The 7.20 Retaliate rework accumulated charges when Centaur was attacked by heroes or towers. Centaur could consume those charges for a temporary percentage base-attack-damage bonus. 7.27b removed that active cash-out and returned Retaliate to the simpler current-style immediate retaliation model.

This historical branch tests a useful large design choice: should damage received by a tank become a stored player-controlled resource, or should each attack pay its cost immediately?

### 7.36-7.41 - three body-progression experiments

7.36 introduced three different ways to extend Centaur's body identity:

- **Rawhide:** permanent max-health growth with game time.
- **Counter-Strike:** recent incoming damage increased the next Double Edge.
- **Horsepower:** Strength converted into movement speed.

7.41 removed Rawhide and Counter-Strike and made Horsepower the Innate. The current structure therefore concentrates more of the hero around a single shared Strength axis rather than maintaining separate time-based HP growth or stored-damage conversion systems.

## Whole-kit behavior

The compact causal loop is:

```text
Strength
  -> large health body
  -> Horsepower / access
  -> body reaches valuable position
  -> Hoof Stomp establishes control
  -> Double Edge spends health for damage
  -> enemy attacks spend Centaur's health
  -> Retaliate taxes those attacks
```

Stampede extends access to the whole team. Shard rewards successful multi-hero contact by temporarily increasing Strength. Scepter lets Centaur directly carry another hero's position.

## Main costs and counterplay

- **Contact dependence:** Stomp, Double Edge, attacks, and much of Retaliate's practical value depend on Centaur reaching the fight rather than being kited or displaced away from it.
- **Health-budget competition:** Double Edge uses the same health margin Centaur needs for frontline survival.
- **Retaliate is a tax, not mitigation:** attack damage still removes Centaur's health; spell damage and Break can bypass or suppress the retaliation loop.
- **Position determines value:** a full-health Centaur outside the important part of a fight may contribute less than a damaged Centaur occupying the enemy's critical space.
- **Stampede opportunity cost:** using the team-wide movement state to escape delays the next opportunity to use it to force contact.

## Compact case close

### Design identity

Centaur makes a large Strength-built body into a shared numerical and spatial resource. Strength enlarges the body and also powers movement, active damage, retaliation, and team trample damage; the rest of the kit is largely about delivering that body into contact and deciding how its health capacity is spent.

### Core mechanical relationships

- Strength -> HP / attacks / Horsepower / Double Edge / Retaliate / Stampede.
- Horsepower + Stampede -> solve access for a short-range body-centered kit.
- Hoof Stomp -> body placement becomes hard control.
- Double Edge -> health margin becomes an active damage resource.
- Enemy attacks -> consume HP but pay Retaliate tax.
- Shard -> successful multi-hero contact temporarily increases the common Strength input.
- Scepter -> Centaur's movement can become another hero's movement platform.

### Case-level candidate lessons

- A single attribute can unify durability, damage, and access so progression reinforces one clear numerical identity.
- Self-damage can turn defensive capacity into an active resource and create a real offense-versus-survival trade-off.
- Tank pressure does not require forced aggro if occupying space and threatening nearby enemies makes ignoring the tank costly.
- A body-centered melee kit may need substantial movement budget because positioning determines whether the rest of the kit functions at all.
- Late upgrades can extend a personal spatial rule into team movement or movement delegation without changing the hero's core theme.

These remain Centaur-specific observations until roster-wide comparison tests them against other designs.

## Sources

Current mechanics and values:

- https://www.dotabuff.com/heroes/centaur-warrunner/abilities
- https://dotacoach.gg/en/heroes/centaur-warrunner
- https://liquipedia.net/dota2/Centaur_Warrunner
- https://liquipedia.net/dota2/7.41e

Historical branches:

- https://liquipedia.net/dota2/Centaur_Warrunner/Changelogs
- https://liquipedia.net/dota2/Centaur_Warrunner/Old_Abilities
- https://liquipedia.net/dota2/Version_6.63
- https://liquipedia.net/dota2/Version_7.36
- https://liquipedia.net/dota2/7.41
- https://liquipedia.net/dota2/Version_7.32
