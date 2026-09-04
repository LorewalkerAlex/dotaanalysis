# Bristleback - Hero Design Case

**Status:** First durable pass

**Current factual reference state:** Dota 2 7.41e. Bristleback received no hero-specific changes in 7.41d or 7.41e; his latest direct changes are from 7.41c, which reduced Warpath attack damage per stack to 12/16/20, increased Hairball cooldown to 15 seconds, and improved the level-25 Bristleback threshold talent from -25 to -30. Historical material below is organized by design branch rather than patch chronology.

## Design identity

Bristleback is a tank whose defining action is not simply standing with his back to the enemy. He repeatedly reads whether opponents are retreating or committing damage, manages enough distance to preserve both choices, and switches between an **offense-facing** pursuit stance and a **defense-facing** tanking stance. When enemies retreat, he turns toward them to apply Viscous Nasal Goo, chase with Warpath movement speed, and cash out Warpath attack damage through ordinary attacks. When enemies turn to fight, he can turn his rear toward the damage source, gaining directional reduction and converting qualifying rear damage into passive Quill Sprays and Warpath progression. Goo reduces enemy movement freedom, Warpath increases his own, and Quill Spray keeps meaningful pressure active while he is turned away. Sustained-contact escalation is therefore an outcome of successful facing and distance management, not the primary action by itself.

## Current combat chassis

| Property | Current value |
| --- | ---: |
| Primary attribute | Strength |
| Strength | 22 + 2.8 |
| Agility | 17 + 1.8 |
| Intelligence | 14 + 2.8 |
| Starting health | 604 |
| Starting health regeneration | 3.2/s total, including 1 base |
| Starting mana | 243 |
| Starting mana regeneration | 1.1/s total, including 0.4 base |
| Starting armor | 3.83 |
| Starting attack damage | 53-59 |
| Attack type / range | Melee / 150 |
| Base attack speed | 100 |
| Base attack time | 1.8 s |
| Attack animation | 0.3 + 0.3 s |
| Movement speed | 295 |
| Turn rate | 0.9; about 0.116 s for a 180-degree turn |
| Vision | 1800 / 800 |

### Compact note

The naked chassis is durable but not defined by an extreme static armor or health pool. The unusually important baseline number is the fast turn rate: Bristleback frequently changes which side of his body is exposed because facing directly changes incoming-damage rules and whether ordinary attacks can be delivered to a pursued target.

### Current source note - armor discrepancy

Current Liquipedia's Bristleback page and Hero Attributes Table both report **3.83 starting armor**, while current Dotabuff displays **3.38**. This case uses the two internally consistent Liquipedia current references and preserves the discrepancy rather than silently mixing the sources.

## Prickly

### Current factual baseline - Innate

- Passive Innate.
- Applies against enemy units in Prickly's rear-centered sector; its own rear angle is **110 degrees**, broader than Bristleback's 70-degree maximum-reduction rear cone.
- Grants outgoing damage amplification and debuff-duration amplification against those enemies.
- Current scaling is **4.5% + 0.5 percentage point per hero level** for both effects.
- The effect is defined by the enemy's position relative to Bristleback, not by the enemy's own facing.

### Core design branch: turning away remains offensively meaningful

Prickly means a defensive turn is not equivalent to leaving combat. When an enemy is positioned behind Bristleback, his damage and offensively applied debuff duration against that enemy are amplified even though he may not be able to right-click it normally at that instant.

**Compact design note:** the Innate reinforces the hero's defining spatial rule rather than adding an unrelated resource. A rear-facing tank stance gives up direct attack access but does not become a purely defensive state.

### Historical/current branch: Warpath Innate -> orientation Innate

In 7.36, Warpath temporarily became Bristleback's Innate. In 7.37, Warpath returned to the ultimate slot and **Prickly** became the Innate, initially granting a fixed 10% outgoing-damage amplification and 1.1 debuff-duration factor against enemies behind Bristleback. In 7.41, the fixed value was replaced with the current hero-level scaling.

**Compact design note:** the modern Innate identifies **relative position and facing** as the hero's always-on identity, while Warpath returns to being a progression payoff for repeated combat actions.

## Bristleback

### Current factual baseline

| Property | Value |
| --- | --- |
| Type | Passive; Scepter adds an active component |
| Rear angle | 70 degrees |
| Side angle | 110 degrees |
| Rear damage reduction | 16% / 24% / 32% / 40% |
| Side damage reduction | 8% / 12% / 16% / 20% |
| Passive Quill damage threshold | 275 / 250 / 225 / 200 qualifying rear damage after reductions |
| Minimum passive-release interval | 0.1 s |
| Level 15 talent | +8 percentage points rear reduction and +4 percentage points side reduction |
| Level 25 talent | -30 damage threshold |
| Break | Disables the ability's functional aspects while active; already accumulated counter damage is not deleted |

The directional test compares the incoming damage source's **current position** with Bristleback's **current facing** for every damage instance. Damage-over-time instances can therefore change whether they receive directional reduction as either the source or Bristleback changes position/facing between ticks.

The rear-damage counter has no ordinary time limit. When the threshold is reached it releases a Quill Spray of the current Quill level without paying Quill's mana cost or ordinary cooldown. Since 7.33, excess qualifying damage is preserved, so one sufficiently large rear damage instance can cross more than one threshold and cause multiple passive Quill releases. Each passive release also grants a Warpath stack.

### Core design branch: tanking is a facing decision, not a permanent stance

The ability creates two incompatible immediate advantages:

- **Face the opponent:** maintain direct pursuit, ordinary attacks, and easy target access, but give up directional reduction.
- **Turn the rear toward the opponent:** maximize mitigation and convert enemy damage into passive Quill/Warpath progression, but temporarily give up ordinary attack access against that target.

The player therefore benefits from reading the opponent's action rather than selecting one permanent orientation. If the enemy retreats, Bristleback wants to face and chase. If the enemy turns to commit damage, Bristleback can turn away and tank that commitment more efficiently. The side-reduction sector supplies a partial middle state during transitions.

### Distance as the enabling resource for facing switches

A full turn is only useful if Bristleback can recover contact afterward. Viscous Nasal Goo lowers enemy movement freedom and Warpath raises Bristleback's movement speed; together they create the positional slack that lets him spend brief periods facing away without automatically losing the target.

**Compact design note:** Goo and Warpath do not merely make a slow melee hero chase better. They buy the time and distance needed to alternate between offensive and defensive facing states.

### Historical/current branch: excess damage preservation and Warpath coupling

Before 7.33, excess damage over a Bristleback threshold could be discarded after one proc. In 7.33:

- Excess qualifying rear damage began carrying forward through the counter.
- A single large damage instance could trigger multiple passive Quills if it crossed multiple thresholds.
- Every passive Quill proc began granting a Warpath stack.

This made burst from the rear capable of accelerating the retaliation/progression loop rather than bypassing it simply by arriving in a single large packet.

## Viscous Nasal Goo

### Current factual baseline

| Property | Value |
| --- | --- |
| Cast | Enemy unit target |
| Cast range | 650; 900 with level 15 talent |
| Projectile speed | 1000 |
| Maximum stacks | 6 |
| Base armor reduction | 1.5 / 2 / 2.5 / 3 |
| Armor reduction per stack | 2 / 2.5 / 3 / 3.5 |
| Base movement slow | 12% |
| Movement slow per stack | 3% / 6% / 9% / 12% |
| Duration | 5 s; repeat applications stack and refresh the duration |
| Cooldown | 1.75 s |
| Mana cost | 12 / 16 / 20 / 24 |
| Warpath interaction | Grants 1 Warpath stack on cast, independent of projectile impact |

### Core design branch: maintain the working distance for a facing tank

Goo rewards continued target maintenance. Each cast both increases the debuff and refreshes the full Goo duration, progressively reducing the target's ability to disengage. The armor reduction also improves Quill Spray's physical damage and Bristleback's later ordinary attacks.

The movement component is especially important to the facing loop. When Bristleback turns his back to tank a retaliation window, Goo helps prevent the enemy from immediately converting that lost attack-facing time into a clean escape. If the enemy resumes retreating, Bristleback can turn back toward it and use Warpath movement speed to close again.

### Historical removed branch: Snot Rocket

The 7.36 **Snot Rocket** facet changed the output of Bristleback's rear-damage threshold:

- Threshold procs released Viscous Nasal Goo instead of Quill Spray.
- Goo stack limit increased by 2.
- Armor reduction per stack increased by 1 in the initial model.

The branch changed enemy damage from a direct retaliatory-damage input into a pursuit/vulnerability input: attacking Bristleback from behind made the attacker slower and easier to damage physically rather than immediately adding Quill history.

The extra armor-reduction bonus was reduced and then removed across 7.39c-7.40. In 7.41 Snot Rocket itself was removed, while base Goo max stacks increased from 4 to the current 6.

**Compact design note:** the experiment preserved a larger Goo buildup capacity but restored a clearer responsibility split - Bristleback's rear damage triggers Quill retaliation, while Goo is primarily maintained by the player's own pursuit actions.

## Quill Spray

### Current factual baseline

| Property | Value |
| --- | --- |
| Cast | No-target; optional autocast |
| Damage type | Physical spell damage |
| Radius | 700 |
| Base damage | 25 / 45 / 65 / 85 |
| Additional damage per existing Quill stack | 30 |
| Stack duration | 14 s per individual stack |
| Maximum damage per Quill | 500 |
| Cooldown | 3 s |
| Mana cost | 35 |
| Level 20 talent | +20 stack damage |
| Warpath interaction | Active/autocast Quill grants 1 stack on cast; Bristleback passive procs also grant 1 stack each |

Quill first checks how many recent Quill stacks an enemy already has, deals `base + stack damage x existing stacks` up to the cap, then adds the new stack. Each stack has its own duration; later hits do **not** refresh all previous stacks.

### Core design branch: rolling recent-contact memory

Quill does not create a permanently escalating target debuff. It records a rolling history of how many Quills have hit the target recently. Remaining near Bristleback allows recent hits to overlap and raises the damage of future sprays; genuinely leaving the engagement lets the oldest records decay independently.

This is the main reason the defensive facing stance can still threaten an opponent. Bristleback can turn away and stop ordinary right-clicking without becoming offensively inactive because active and passive Quills are radial and do not require him to face the target.

### Enemy pressure -> retaliation -> self progression

Current rear damage can produce the following chain:

```text
enemy commits damage into Bristleback's rear
    -> directional mitigation
    -> rear damage counter crosses threshold
    -> passive Quill Spray
    -> enemy recent-Quill history increases
    -> Bristleback gains a Warpath stack
```

Enemy damage therefore creates both an immediate area retaliation and a future self-buff payoff, provided the opponent supplies it through the relevant orientation and Bristleback survives the incoming pressure.

### 6.33 design boundary: random-duration spray -> recent-contact escalation

Before 6.33, Quill Spray was a 15-second-cooldown, 6-second effect that launched many small quills at randomly chosen nearby enemies, using different close/far damage values.

6.33 replaced it with the recognizable modern structure:

- Instant radial physical spray.
- 3-second cooldown.
- Fixed base damage plus **+30 damage for each recent Quill hit**.
- Independent per-hit history rather than one refreshed stack timer.
- Bristleback passive began automatically releasing the new Quill after sufficient rear damage.

This should be preserved together with the Warpath rework below as a whole-kit boundary rather than as an isolated balance change.

## Warpath

### Current factual baseline

| Property | Value |
| --- | --- |
| Type | Passive ultimate |
| Maximum stacks | 8 / 10 / 12 |
| Attack damage per stack | 12 / 16 / 20 |
| Movement speed per stack | 2% / 2.5% / 3% |
| Stack duration | 16 / 18 / 20 s; individual stacks have independent durations |
| Normal ability casts | +1 stack each where eligible |
| Passive Bristleback Quill proc | +1 stack per proc |
| Scepter Bristleback | Up to +5 stacks per active cast, one per released Quill |
| Break | Prevents new stack gain; existing stack bonuses remain |
| Level 25 talent | +18 attack damage per stack |

At current maximum stacks, untalented Warpath grants up to **96/160/240 bonus attack damage** and **16%/25%/36% movement speed**.

### Core design branch: repeated activity prepares the face-forward cash-out

Warpath turns repeated low-cooldown actions and passive retaliation into a progressively stronger body. The movement-speed component helps Bristleback recover distance after turning away to tank, while attack damage rewards the moment he turns back toward a retreating target and resumes ordinary attacks.

This resolves a basic tension in the hero: the passive encourages rear-facing defense, but the hero still needs a reason to face the enemy again. Warpath stores value during the contact and makes the eventual offensive-facing window increasingly threatening.

### 6.33 whole-kit boundary: attack proc -> spell-driven ramp

Before 6.33, Warpath was an attack-triggered random rampage:

- 10% / 20% / 30% proc chance per attack.
- +150 attack speed.
- +30% movement speed.
- 10-second duration.
- Could not retrigger while already active.

6.33 replaced it with a deterministic ability-cast stacking model. The first reworked branch granted movement speed and **attack speed** on repeated casts; 6.63 later replaced the attack-speed package with **attack damage**, establishing the lineage of the current payoff.

Combined with the simultaneous Quill rework, 6.33 moved Bristleback away from occasional attack-proc frenzy and random-duration quills toward a kit where repeated actions and sustained contact progressively change both enemy and self state.

### Removed facet branch: Berserk

The 7.36 **Berserk** facet changed Warpath's payoff toward attack frequency:

- Added attack speed per Warpath stack.
- Reduced Warpath attack damage to a low fixed value per stack.

In 7.37 the attack-speed bonus was rescaled to 10/15/20 per stack. The facet was removed in 7.38.

**Compact design note:** attack speed demanded longer face-forward right-click windows than flat attack damage. The branch therefore changed not only output magnitude but how strongly Warpath required Bristleback to abandon the rear-facing defensive stance and remain facing the target.

### Removed facet branch: Seeing Red

The 7.37 **Seeing Red** facet added an active Warpath commitment:

- Duration: **4 / 5 / 6 seconds**.
- Multiplied Warpath attack-damage and movement-speed bonuses by **1.5** during the active window.
- Reduced Bristleback's vision to a **90-degree front cone** initially.
- Cooldown: **45 seconds**.
- Mana: **55 / 65 / 75**.

In 7.38, that restricted vision was shared to the team while Bristleback himself stopped receiving the rest of his team's vision; 7.39 expanded the front cone to 110 degrees. Seeing Red was removed in 7.41.

**Compact design note:** the branch briefly priced a stronger offensive Warpath cash-out with an information/facing commitment. The player became stronger while looking forward but gave up normal omnidirectional team vision, intensifying the conflict between face-forward offense and rear-facing defense.

## Dynamic facing and tanking loop

The current kit can be reconstructed as a repeated opponent-response loop:

```text
opponent retreats
    -> Bristleback faces the target
    -> Goo / Warpath movement / ordinary attacks maintain pursuit

opponent turns to commit damage
    -> Bristleback turns side/rear toward the source
    -> directional reduction improves tanking efficiency
    -> rear damage can trigger passive Quill + Warpath

opponent stops attacking and resumes retreat
    -> Goo has reduced escape distance
    -> Warpath has increased Bristleback movement
    -> Bristleback turns forward again and resumes pursuit
```

The hero therefore tanks by making himself a threatening target and then changing how efficiently opponents can punish that threat. Ignoring him allows a face-forward chase and increasingly strong attacks; committing damage into his preferred angle improves his mitigation and can feed retaliation/progression.

### Tanking as behavior induction

Bristleback has no built-in forced-attack taunt. The kit instead creates pressure that makes ignoring him costly: repeated Quills, accumulating Goo, rising Warpath movement, and high Warpath attack damage. If opponents choose to answer that pressure by attacking him, the player can reactively switch to the body orientation that is best at receiving the response.

**Compact design note:** durability is not the entire tank mechanic. The hero first needs enough offensive threat to make being attacked a plausible opponent choice, then uses facing to improve the exchange once that choice is made.

## Aghanim's Scepter - active Bristleback

### Current factual baseline

| Property | Value |
| --- | --- |
| Targeting | Point target; global targeting for direction selection |
| Effect delay | 0.5 s |
| Quill instances | 5 |
| Interval | 0.4 s |
| Cone angle | 45 degrees |
| Self movement slow | 40% |
| Facing | Locked after rotation; cannot freely turn during the active sequence |
| Ordinary attacks | Self-disarmed during the sequence |
| Other Bristleback abilities | Can still be cast without ordinary facing requirements during the active state |
| Cooldown | 24 s |
| Mana cost | 125 |
| Warpath | Up to 5 stacks per full active cast |

The global cast range chooses a **direction**, not a globally distant damage location. Quills still originate from Bristleback's body and are released in a narrow cone behind him.

### Core design branch: trade the hero's most important control freedom for compressed buildup

The Scepter can rapidly seed five Quill instances and up to five Warpath stacks, but temporarily removes the ordinary facing dance by locking direction, disarming Bristleback, and slowing movement. The upgrade therefore buys compressed escalation with the exact control variable the base hero normally manages most actively: freedom to turn between offense and defense.

### Historical Scepter branch: Goo coverage -> active orientation weapon

From 7.31 until the 7.34 rework, Scepter upgraded Viscous Nasal Goo into a no-target area application that affected visible enemies around Bristleback and increased Goo stack capacity in later versions.

7.34 replaced that coverage upgrade with the recognizable active Bristleback design: point-targeted direction selection, delayed rotation, repeated rear cone Quills, facing lock, disarm, and movement slow. The initial version released 6 Quills at 0.35-second intervals; 7.36 increased the interval to 0.4 seconds and 7.37 reduced the count to the current 5.

**Compact design note:** the older answer expanded debuff coverage; the current answer gives active control over the hero-defining rear-facing mechanic, but charges a large temporary commitment in turn freedom and ordinary attacks.

## Hairball

### Current factual baseline - Aghanim's Shard

| Property | Value |
| --- | --- |
| Cast | Point target projectile |
| Cast range | 750 |
| Projectile speed | 1200 |
| Impact radius | 700 |
| Viscous Nasal Goo | Applies 2 stacks |
| Quill Spray | Applies 1 Quill instance |
| Cooldown | 15 s |
| Mana cost | 60 |
| Warpath | Hairball cast itself grants 1 stack |

### Design branch: seed the contact state before Bristleback's body arrives

Base Bristleback pressure is body-centered: Quill is radial around him, rear retaliation requires enemy damage into his body, and Goo normally requires a 650-range unit target. Hairball lets the player place two Goo stacks and one Quill hit at a distant location before full body contact.

The upgrade therefore reduces the **access friction** of starting the facing/tanking loop. It does not complete the entire escalation remotely; it creates a better initial state from which Bristleback can close distance and begin the ordinary chase/turn/chase cycle.

### Historical Shard branch: remote Quill pressure -> pursuit seeding

When Hairball appeared in 7.28, it had **1500 cast range** and applied **2 Quill Sprays**, emphasizing long-range Quill buildup. The 7.36 rework reduced it to 1 Quill but increased Goo to 2 stacks, reduced cost/cooldown, and made it more explicitly a pursuit-state seeding tool. Later versions tightened its access; current cast range is 750, mana cost 60, and 7.41c increased cooldown to 15 seconds.

## 7.36-7.41 experimental branches

The Facet/Innate period is worth preserving as a compact group because each branch changed what the same sustained-contact engine converted into.

### Snot Rocket - rear damage -> pursuit state

Rear damage threshold procs created Goo rather than Quill. Enemy pressure therefore produced slow/armor vulnerability instead of direct retaliatory Quill escalation.

### Berserk - Warpath -> attack frequency

Repeated ability activity shifted its payoff toward attack speed and away from attack damage, increasing the value of prolonged face-forward right-click windows.

### Seeing Red - accumulated Warpath -> information-priced burst

Existing Warpath stacks could be temporarily amplified at the cost of severely restricted personal vision, turning information and forward-facing commitment into part of the offensive cash-out.

### Prickly - orientation becomes the surviving Innate identity

Prickly persisted when Facets were removed in 7.41. Snot Rocket and Seeing Red were removed, while base Goo received a 6-stack ceiling and Prickly changed to hero-level scaling. The current design therefore recenters the hero around orientation, active pursuit with Goo, retaliation through Quill, and self progression through Warpath.

## Current talents

| Level | Left | Right |
| --- | --- | --- |
| 10 | +1.5 mana regeneration | +25 attack speed |
| 15 | +8% rear / +4% side Bristleback damage reduction | +250 Viscous Nasal Goo cast range |
| 20 | +20 Quill stack damage | +25 health regeneration |
| 25 | +18 Warpath attack damage per stack | -30 Bristleback damage threshold |

The most structurally relevant pairs reinforce existing choices rather than creating new subsystems:

- Level 15 improves either **tanking after contact** or **access before/while pursuing**.
- Level 25 improves either **payoff per accumulated Warpath stack** or **the rate at which enemy rear damage generates passive Quill/Warpath progression**.

## Kit relationships

- **Opponent retreats -> face forward -> Goo / Warpath movement / ordinary attacks:** pursuit requires exposing the weaker front in exchange for direct offensive access.
- **Opponent commits damage -> turn rear/side -> Bristleback mitigation:** orientation changes the efficiency with which the same incoming pressure is absorbed.
- **Rear damage -> passive Quill -> Warpath:** tanking the opponent's response can generate both area retaliation and self progression.
- **Quill -> recent-contact history -> higher future Quill damage:** enemies that remain nearby make the radial/off-facing damage state increasingly expensive.
- **Goo slow -> less enemy movement freedom; Warpath movement -> more Bristleback movement freedom:** both sides of the distance equation make repeated facing switches more sustainable.
- **Goo armor reduction -> Quill physical damage + ordinary attacks:** the pursuit debuff also prepares the physical damage channels used during both off-facing Quill pressure and face-forward attack cash-out.
- **Prickly -> rear-position offensive value:** turning away does not fully abandon offense because damage/debuff value against enemies behind Bristleback is amplified.
- **Hairball -> remote state seeding:** Shard reduces the spatial cost of beginning the loop.
- **Scepter -> forced rear-facing Quill burst:** Scepter reduces the time cost of buildup by temporarily surrendering free facing, attack access, and movement speed.

## Costs, failure modes, and counterplay

- **Facing read can be wrong:** if Bristleback turns forward to chase and the opponent immediately commits burst, the incoming damage bypasses his rear/side reduction. If he turns away while the opponent simply keeps retreating, he gives up direct attack access without receiving tanking value.
- **Distance can break the loop:** Goo and Warpath improve pursuit but do not provide a true base-kit dash. Sufficient separation prevents Quill history from staying dense and makes repeated facing switches irrelevant.
- **Disengagement attacks Quill memory:** Quill stack records expire independently after 14 seconds. Leaving long enough causes the recent-contact damage engine to decay without requiring a dispel.
- **Front-side damage attacks the defining defense:** damage delivered from outside the side/rear reduction sectors avoids the primary mitigation and does not advance the rear Quill threshold.
- **Break attacks the passive conversion chain:** Break disables Bristleback's passive functions and prevents new Warpath stack gain. Existing Warpath stacks remain, and already accumulated Bristleback counter damage is not deleted, so timing the Break still matters.
- **Rear burst is not an automatic bypass:** since 7.33, excess qualifying rear damage is preserved and one large instance can trigger multiple passive Quills. Reliable counterplay therefore comes more from direction, Break, distance, or ending the contact than from assuming one large rear hit avoids retaliation.
- **Scepter creates a commitment window:** the active sequence compresses buildup but locks facing, disarms Bristleback, and slows movement, temporarily removing the base hero's most important response freedom.

## Compact design conclusions

- A tank can make **orientation switching** an active defensive skill: facing the enemy grants direct pursuit/attack access, while turning away converts the same opponent response into more efficient tanking and retaliation.
- Movement control can support tanking without being pure mobility. Slowing the opponent and speeding the tank buy enough distance margin to spend time in a non-attacking defensive orientation and still recover contact afterward.
- A radial retaliation spell can preserve threat while the hero deliberately gives up ordinary attack facing, making defense a different offensive mode rather than a total pause in pressure.
- Independent recent-hit timers make prolonged proximity progressively dangerous while preserving a clean counterplay answer: fully disengage and allow the history to decay.
- Enemy damage can participate in a hero's progression loop when the conversion is gated by direction, survivability, and a damage threshold rather than being a free unconditional reward for being attacked.
- Upgrades can reduce different setup frictions without replacing the base loop: Hairball reduces **spatial access cost**, while Scepter reduces **time-to-escalation** at the price of facing/attack freedom.
- Short-lived Snot Rocket, Berserk, and Seeing Red branches show that the same sustained-contact structure can pay out as pursuit control, attack frequency, or information-priced burst; the current design instead recenters orientation as the stable defining identity.

These are case-supported observations, not yet cross-hero principles.

## Sources

Current and historical factual material was checked against:

- Liquipedia - Bristleback: https://liquipedia.net/dota2/Bristleback
- Liquipedia - Bristleback Changelogs: https://liquipedia.net/dota2/Bristleback/Changelogs
- Liquipedia - Bristleback Old Abilities: https://liquipedia.net/dota2/Bristleback/Old_Abilities
- Liquipedia - Hero Attributes Table: https://liquipedia.net/dota2/Table_of_hero_attributes
- Liquipedia - Version 6.33: https://liquipedia.net/dota2/Version_6.33
- Liquipedia - Version 7.36: https://liquipedia.net/dota2/Version_7.36
- Liquipedia - Version 7.37: https://liquipedia.net/dota2/Version_7.37
- Liquipedia - Version 7.38: https://liquipedia.net/dota2/Version_7.38
- Liquipedia - Version 7.41: https://liquipedia.net/dota2/Version_7.41
- Liquipedia - Version 7.41e: https://liquipedia.net/dota2/Version_7.41e
- Dotabuff - Bristleback abilities / current values: https://www.dotabuff.com/heroes/bristleback/abilities

Where a historical mechanic had many balance-only parameter changes, this document records representative or mature branch values rather than reproducing full patch chronology. The current armor-source discrepancy is preserved explicitly rather than hidden.
