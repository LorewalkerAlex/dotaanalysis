# Alchemist - Hero Design Case

**Status:** First durable pass

**Current factual reference state:** Dota 2 7.41e. Alchemist received no hero-specific changes in 7.41d or 7.41e; his latest direct changes are from 7.41c, which standardized Acid Spray to a 21-second cooldown at all levels, reduced Chemical Rage health regeneration to 50/85/120, and reduced the Greevil's Greed gain per gifted Aghanim's Scepter to +3 base and +3 maximum bonus gold. Historical material below is organized by design branch rather than patch chronology.

## Design identity

Alchemist turns economic production rate into a hero ability. Greevil's Greed rewards continuous resource collection and lets equal match time produce unequal purchasing power; Acid Spray and Chemical Rage reduce the time and recovery friction involved in processing map resources, while the combat kit converts earlier item timings into a physical-contact advantage. Unstable Concoction is the main bridge into that contact: the player can voluntarily hold a visible self-destructing timer to buy stronger physical damage, stun duration, and Corrosive Weaponry preload before committing to the target. When personal gold becomes surplus, Aghanim's Scepter Synth lets Alchemist convert it into allied capability while feeding permanent damage and stronger future Greed back into himself.

## Current combat chassis

| Property | Current value |
| --- | ---: |
| Primary attribute | Strength |
| Strength | 23 + 2.7 |
| Agility | 19 + 1.5 |
| Intelligence | 25 + 1.8 |
| Starting health | 626 |
| Starting health regeneration | 2.55/s total, including 0.25 base |
| Starting mana | 375 |
| Starting mana regeneration | 1.25/s total, with 0 base mana regeneration |
| Starting armor | 3.17 |
| Starting attack damage | 50-56 |
| Attack type / range | Melee / 150 |
| Base attack speed | 110 |
| Base attack time | 1.7 s |
| Attack animation | 0.35 + 0.65 s |
| Movement speed | 290 |
| Turn rate | 0.6 |
| Vision | 1800 / 800 |

### Compact note

Alchemist's starting body is not where his defining power budget sits. Current 7.41a-7.41b changes even reduced movement speed to 290 and base Agility to 19. His unusual advantage is that the same elapsed match time can produce more purchased power, not that his naked chassis is intrinsically superior to other Strength heroes.

## Greevil's Greed

### Current factual baseline - Innate

| Property | Value |
| --- | --- |
| Type | Passive Innate |
| Base bonus gold | 2 |
| Bonus gold per stack | 2 |
| Maximum stacks | 8 |
| Maximum bonus gold per eligible kill | 16 |
| Recent-kill / stack window | 40 s |
| Bounty Rune self-gold multiplier | 2x |
| Break interaction | Prevents new Greed stack gain and disables the Bounty Rune multiplier; existing stacks remain |
| Level 15 talent | Converts Greed's current gold-bonus state into +3 flat attack damage per bonus unit; current baseline maximum is +48 attack damage |

The ordinary kill bonus is unreliable gold. The extra Bounty Rune gold is reliable gold.

### Core design branch: continuous production raises unit-time economic efficiency

Greevil's Greed does not grant a fixed passive GPM. Its highest output depends on repeatedly killing units that grant gold before the recent-kill state expires. The ability therefore rewards a continuous farming route rather than merely the total number of creeps killed over a long period.

**Compact design note:** the hero's defining resource advantage is not free combat magnitude. It is a higher rate at which available map resources can be converted into purchasing power, so interruptions to farming continuity directly attack the defining mechanic.

### Historical design branch: skill-point investment -> innate identity

Before 7.33, Greevil's Greed was a normal four-level ability. A representative late version scaled its maximum bonus gold and Bounty Rune multiplier with skill level, so investing skill points explicitly traded immediate combat/farming abilities against stronger future economic acceleration.

In 7.33, Greevil's Greed became an Innate and stopped competing for ordinary ability points. Corrosive Weaponry became the new third basic ability.

**Compact design note:** the old model made economic acceleration an optional progression investment; the current model makes economic acceleration a compulsory part of Alchemist's identity from the start of the match.

### Removed economy-timing branch: Seed Money

From 7.36 until 7.41, the **Seed Money** facet granted **250 bonus starting gold**.

This branch front-loaded the economic advantage before farming began. It answered a different timing question from Greevil's Greed: instead of increasing resource conversion after repeated kills, it increased starting purchasing power at time zero.

### Removed reinvestment branch: Dividends

From 7.38 until 7.41, the **Dividends** facet granted passive GPM for every Aghanim's Scepter Synth already given to an ally:

- Initial model: **75 GPM per gifted Scepter**.
- Mature 7.39 model: **70 GPM per gifted Scepter**.

The current design removed passive Dividends and instead makes gifted Scepters improve future Greevil's Greed production. The distinction is material: Dividends generated income automatically with time, whereas the current reward still requires Alchemist to keep finding and killing resources.

## Acid Spray

### Current factual baseline

| Property | Value |
| --- | --- |
| Cast | Point-targeted area / aura |
| Damage type | Physical |
| Cast range | 900 |
| Radius | 350 / 400 / 450 / 500 |
| Damage per second | 25 / 30 / 35 / 40 |
| Armor reduction | 3 / 4 / 5 / 6 |
| Duration | 15 s |
| Cooldown | 21 s |
| Mana cost | 120 |
| Corrosive Weaponry application | 1 stack per damage interval |
| Level 15 talent | +1 armor reduction |

### Design branch: farming throughput and physical-combat staging

Acid Spray processes multiple nearby creeps in parallel while reducing the armor of everything that remains inside. That shortens the time required to convert clustered map resources into gold and therefore supports Greevil's Greed continuity.

In combat, the same armor reduction benefits a wider physical chain than ordinary attacks alone: Acid Spray itself deals physical spell damage, Unstable Concoction deals physical spell damage, and Alchemist's follow-up attacks deal physical attack damage.

### Historical design branch: legacy Composite damage -> Physical damage

In 6.82, Acid Spray changed from the legacy Composite damage model to **Physical** damage. The modern branch therefore aligns the area's own damage with its armor-reduction effect and with the rest of Alchemist's physical conversion sequence.

### Current kit-integration branch: Acid Spray applies Corrosive Weaponry

Since the 7.38 Corrosive Weaponry rework, each Acid Spray damage interval also adds a Corrosive stack. The area is therefore not only a damage/farming zone; remaining inside it progressively preconditions enemies for the later pursuit and trading loop.

## Unstable Concoction

### Current factual baseline

| Property | Value |
| --- | --- |
| First cast | No target; begins brewing |
| Throw | Unit/area target on an enemy hero |
| Damage type | Physical spell damage |
| Cast range | 775 |
| Explosion radius | 250; 400 with level 10 talent |
| Maximum-power brew time | 5 s |
| Self-explosion deadline | 5.5 s |
| Movement-speed bonus while brewing | 4% / 8% / 12% / 16% |
| Minimum damage | 0 |
| Current maximum damage | 150 / 220 / 290 / 360 |
| Minimum stun | 0.25 s |
| Maximum stun | 1.7 / 2.2 / 2.7 / 3.2 s |
| Corrosive Weaponry preload | `ceil(brew time)` stacks, minimum 1 and maximum 6 |
| Cooldown | 17 s |
| Mana cost | 100 |
| Level 10 talent | +150 radius |
| Level 20 talent | +400 maximum damage |

While brewing, Alchemist can move, attack, cast abilities, and use items. The brew timer is visible to both teams. If the deadline is missed, or if Alchemist dies while brewing, the concoction explodes around Alchemist based on the accumulated brew time; the self-damage can deny him. The thrown projectile travels at 900 speed and cannot be disjointed.

### Core design branch: voluntary delay buys stronger control under a public deadline

Unstable Concoction turns control magnitude into a continuously chosen risk. Throwing early is safer but weaker. Waiting toward five seconds buys more physical damage, a longer stun, and more Corrosive Weaponry stacks, but leaves less margin before the 5.5-second self-explosion.

Because the countdown is public information, the opponent can react to the same deadline: repositioning, denying a clean target, forcing a poor throw, or extending the chase attacks the timing decision before the projectile is released.

### Whole-kit bridge: preparation -> contact

A long-brew Concoction can arrive after Acid Spray has already reduced armor and begun applying Corrosive stacks. On impact it adds another 1-6 stacks while stunning the target, giving Chemical Rage Alchemist a controlled window to enter melee and continue the stack loop with attacks.

**Compact design note:** Concoction is not merely an isolated stun. It is the main conversion from a still-mobile, not-yet-committed Alchemist into a favorable sustained-contact state.

### Historical design branch: target-first channel -> free-action brew and late target commitment

Before the 6.65 rework, Alchemist first selected the target and then channeled:

- Maximum channel: **2 / 3 / 4 / 5 seconds**.
- Damage gained: **60 magical damage per channeled second**.
- Stun gained: **1 second per channeled second**.
- Mana cost: **75**.
- Cooldown: **16 seconds**.

6.65 replaced that structure with the recognizable modern model: Alchemist could move and act freely while brewing, decide the target later through a separate Throw ability, and risk the effect exploding on himself if he failed to release it. The reworked spell also became physical damage and its projectile could not be disjointed.

6.80 then tightened the timing to the mature **5 seconds to maximum power / 5.5 seconds to self-explosion** model and stopped the effect from continuing to grow while the projectile was in flight.

### Historical information branch: hidden versus public countdown

- The 6.65 rework displayed the brew countdown publicly.
- 6.75 hid the countdown from enemies.
- 6.84 made the countdown visible to enemies again.

The current branch therefore deliberately exposes the risk timer as opponent-usable information rather than leaving it as a private execution challenge.

### Current source note

Current 7.41e-oriented ability data from Liquipedia and current Dotabuff both report **150/220/290/360 maximum damage** and a **17-second cooldown**. Liquipedia's changelog separately records a 7.07d increase from 150/220/290/360 to 160/240/320/400, but the consulted changelog does not surface the later transition back to the current values. This case records the current live-data agreement rather than inferring an undocumented patch step.

## Corrosive Weaponry

### Current factual baseline

| Property | Value |
| --- | --- |
| Type | Passive stacking debuff |
| Maximum stacks | 7 / 10 / 13 / 16 |
| Stacks per Alchemist attack | 2 |
| Movement slow per stack | 2.5% / 3% / 3.5% / 4% |
| Base attack damage reduction per stack | 2.5% / 3% / 3.5% / 4% |
| Debuff duration | 4 s; new applications refresh duration |
| Acid Spray | +1 stack per damage interval |
| Unstable Concoction | +1 stack per brewed second, rounded up; minimum 1, maximum 6 |
| Level 10 talent | +1 percentage point slow and base-damage reduction per stack |

At current maximum stacks, the untalented slow and base-attack-damage reduction are **17.5% / 30% / 45.5% / 64%** by ability level. Buildings are unaffected. Alchemist's normal attacks do not apply the passive to Roshan, although qualifying ability casts can apply stacks.

### Historical design branch: attack-only slow plus status-resistance reduction

Corrosive Weaponry was introduced in 7.33 as an attack-only stacking passive:

- **3% / 4% / 5% / 6%** movement slow per stack.
- The same amount of **status-resistance reduction** per stack.
- Maximum stacks: **5 / 7 / 9 / 11**.
- Duration: **3.5 seconds**.

That model made sustained attacks improve the effectiveness of later status effects.

### Historical/current branch: status-resistance reduction -> base-attack-damage reduction

In 7.36, the status-resistance component was removed and replaced by **base attack damage reduction**. The mechanic therefore shifted from improving subsequent disables/debuffs to directly improving extended melee pursuit and trading: the target becomes slower while its ordinary attack response becomes weaker.

### Historical/current branch: attack-only stacking -> whole offensive kit stacking

The 7.38 rework connected Corrosive Weaponry to the rest of Alchemist's offensive kit:

- Alchemist attacks began adding **2 stacks** instead of 1.
- Acid Spray began adding a stack each damage interval.
- Unstable Concoction began adding stacks according to brew time.
- The stack ceiling was expanded and later rescaled to the current 7/10/13/16 in 7.39.

7.41 increased the current per-stack slow and base-damage reduction to 2.5%/3%/3.5%/4%.

**Compact design note:** the debuff becomes a record of sustained offensive contact from the whole kit rather than from right-clicks alone. The accumulating slow then makes continued contact easier, while the attack-damage reduction improves the trade during that contact.

## Chemical Rage

### Current factual baseline

| Property | Value |
| --- | --- |
| Cast | No target; self transformation |
| Transformation time | 0.35 s |
| Set base attack time | 1.2 / 1.1 / 1.0 s |
| Health regeneration bonus | 50 / 85 / 120 per second |
| Movement-speed bonus | 20 / 30 / 40 |
| Duration | 30 s |
| Cooldown | 60 s |
| Mana cost | 50 / 75 / 100 |
| Level 20 talent | -0.1 s base attack time |
| Level 25 talents | +50 health regeneration or +50 movement speed |

Casting Chemical Rage applies a basic dispel. The 0.35-second transformation briefly disables Alchemist but cannot be interrupted and disjoints incoming projectiles before the Rage state begins.

### Core design branch: body throughput for both farming and purchased-power conversion

Chemical Rage changes three frictions at once:

- Lower BAT increases attacks completed per unit time.
- Higher movement speed reduces travel time between resources and improves pursuit.
- Extreme health regeneration reduces the downtime and attrition cost of farming or remaining in prolonged combat.

Because much of Alchemist's combat strength is purchased from the common item system, lowering BAT also increases how frequently attack damage, attack speed, and attack-linked item value can be realized during a fixed combat window.

### Historical durability branch: bonus health -> extreme regeneration

A mature pre-6.79 Chemical Rage granted **250/500/750 bonus health** in addition to its other effects. In 6.79, the bonus-health component was removed and the health-regeneration bonus was increased from 15/30/60 to **50/75/100**.

**Compact design note:** the old branch primarily increased burst capacity by enlarging the health pool; the regeneration branch instead rewards surviving the opponent's immediate damage and remaining in the fight long enough to recover.

### Historical resource branch: mana regeneration [Removed]

Chemical Rage also granted substantial mana regeneration for several years. A representative late model granted **4/10/16 mana regeneration**; the entire mana-regeneration component was removed in 7.22g.

Removing it narrowed Rage away from being a broad self-sufficiency state and left health, movement, and attack throughput as its defining current benefits.

### Removed facet branch: Mixologist

From 7.36 to 7.40, **Mixologist** made Chemical Rage a cooldown-economy state in addition to a body transformation. The mature branch reduced:

- Unstable Concoction cooldown by **35%** while Rage was active.
- Berserk Potion cooldown by **50%** while Rage was active.

7.41 removed Mixologist and its components. Current Chemical Rage therefore modifies the hero's body and recovery without also accelerating the cooldown loop of those two abilities.

## Berserk Potion

### Current factual baseline - Aghanim's Shard

| Property | Value |
| --- | --- |
| Cast | Allied unit target; double-tap self-cast |
| Cast range | 800 |
| Basic dispel | Applied on impact |
| Attack-speed bonus | 50 |
| Movement-speed bonus | 30 |
| Health-regeneration bonus | 40 |
| Duration | 15 s |
| Cooldown | 35 s |
| Mana cost | 100 |
| Projectile | 900 speed; cannot be disjointed; self-cast uses no projectile |

### Design branch: export a reduced Chemical Rage-like package

Berserk Potion transfers three familiar parts of Alchemist's own transformation identity - faster attacks, faster movement, and health regeneration - to another allied unit, and adds a basic dispel. It does not copy Chemical Rage's BAT replacement or its extreme regeneration, so it exports the action-throughput/sustain direction without duplicating the entire transformation.

### Historical Shard branch: sustain/attack buff -> broader action-throughput buff

When Berserk Potion first appeared as the 7.28 Shard, it granted:

- +50 attack speed.
- +40 health regeneration.
- 10-second duration.
- 45-second cooldown.
- 125 mana cost.

7.28b reduced the cooldown to 35 seconds, 7.30 added **+30 movement speed**, 7.31d reduced the mana cost to 100, and 7.37b extended the duration to the current 15 seconds.

The movement addition is the meaningful capability change: the Potion stopped being only a sustain/attack-rate buff and began helping the target maintain or break contact as well.

## Aghanim's Scepter Synth

### Current factual baseline

Alchemist can melt down an Aghanim's Scepter in his inventory and apply it to an allied hero at **global cast range**.

The targeted ally permanently receives:

- The hero's Aghanim's Scepter upgrades.
- The Scepter stat package: **+10 all attributes, +175 health, +175 mana**.

For every Scepter granted to an ally, Alchemist permanently gains:

- **+15 flat attack damage**.
- Greevil's Greed **base bonus gold +3**.
- Greevil's Greed **maximum bonus gold +3**.

If the target already owns an eligible Scepter/Blessing state, the corresponding item value can instead be refunded as unreliable gold while the permanent upgrade is applied.

### Core design branch: personal surplus -> allied capability + self reinvestment

Scepter Synth gives excess personal gold a team-facing outlet. Alchemist can convert a large personal purchase into a permanent new capability on another hero rather than continuing only to increase his own six-slot inventory.

The current reward is not pure donation: every gifted Scepter simultaneously increases Alchemist's attack damage and makes future active farming through Greevil's Greed more productive.

### Historical design branch: pure transfer -> personal combat reward

When Scepter gifting was introduced in 6.84, the defining mechanic was simply the permanent transfer of the Aghanim upgrade to an ally.

In 7.22, gifting began granting Alchemist **+30 attack damage and +6% spell amplification per gifted Scepter**. The values were later reduced; the spell-amplification component was ultimately removed in 7.38b. This branch made generosity feed back into personal combat scaling even before Greed itself was connected to gifting.

### Removed Dividends branch: passive investment return

The 7.38 Dividends facet added passive GPM per gifted Scepter, later settling at **70 GPM** per Scepter before removal in 7.41.

7.41 replaced that passive-income answer with a new one: gifted Scepters increased Greevil's Greed's base and maximum gold bonus. The initial +6/+6 was reduced in 7.41c to the current **+3/+3**, while 7.41a set the current self attack-damage reward to **+15 per gifted Scepter**.

**Compact design note:** the modern reinvestment loop still requires Alchemist to perform the defining activity - acquiring map resources - instead of granting him an automatic interest stream after the investment.

## Current talents

| Level | Left | Right |
| --- | --- | --- |
| 10 | +150 Unstable Concoction radius | +1 percentage point Corrosive Weaponry slow / base-damage reduction per stack |
| 15 | Greevil's Greed provides +3 attack damage per bonus unit | +1 Acid Spray armor reduction |
| 20 | +400 Unstable Concoction maximum damage | -0.1 s Chemical Rage base attack time |
| 25 | +50 Chemical Rage health regeneration | +50 Chemical Rage movement speed |

The tree largely reinforces two existing axes: preparation/entry through Concoction and Spray, or sustained body/contact throughput through Corrosive Weaponry and Chemical Rage. The level-15 Greed talent is especially direct: the current economic-production state becomes an immediate attack-damage state instead of needing to pass entirely through item purchases first.

## Kit relationships

- **Acid Spray -> farming throughput -> Greevil's Greed continuity:** area processing reduces time spent clearing a cluster and helps preserve the recent-kill production state while moving through a route.
- **Greevil's Greed -> earlier purchased power -> Chemical Rage:** Greed changes when common item power is acquired; Rage's BAT, movement, and regeneration help realize that purchased power repeatedly during farming and combat.
- **Acid Spray armor reduction -> physical Concoction + physical attacks:** the same zone improves the later burst and sustained physical conversion chain.
- **Acid Spray / Concoction -> Corrosive preload -> Chemical Rage attacks:** spells create the opening stack state, then lower BAT and repeated attacks continue the debuff.
- **Corrosive slow -> continued contact; Corrosive base-damage reduction -> safer trading:** accumulating the passive makes its own future accumulation easier and weakens ordinary attack retaliation.
- **Unstable Concoction timer -> initiation risk:** waiting purchases damage, stun, and stack preload, but a visible 5.5-second deadline gives the opponent time-based counterplay and can turn the spell against Alchemist.
- **Berserk Potion -> export part of the transformation package:** Shard lets Alchemist lend attack throughput, movement, regeneration, and a basic dispel to an ally without copying Chemical Rage wholesale.
- **Personal surplus -> Scepter Synth -> team capability + permanent self feedback:** excess gold can leave Alchemist's own inventory while still increasing future farming and attack power.

## Costs, failure modes, and counterplay

- **Production interruption:** denying safe waves/camps, contesting Bounty Runes, invading routes, or forcing repeated low-value movement reduces the time Greed can spend in a high-throughput state.
- **Timing decay:** a net-worth lead is partly valuable because it arrives earlier. If that lead does not secure objectives, map control, or further acceleration before opponents acquire comparable purchased power, its time advantage narrows.
- **Concoction deadline:** the opponent can see the brew timer and play against target availability and positioning before the throw. Failure can self-stun, self-damage, and even self-deny Alchemist.
- **Sustained-contact dependence:** kiting, displacement, hard control, burst, and disengagement attack the Corrosive/Rage loop by denying the repeated attacks that turn economic lead into melee pressure.
- **Regeneration dependence:** Chemical Rage is strongest when Alchemist survives long enough to use its regeneration; burst and health-restoration suppression reduce that branch of durability more directly than they would reduce an equivalent chunk of permanent bonus health.
- **Break against the economic engine:** Break prevents new Greevil's Greed stack gain and removes the Bounty Rune multiplier while active, directly attacking production rather than only combat output.

## Compact design conclusions

- An economy mechanic can allocate hero power through **earlier access to a shared item system** rather than through unique direct combat magnitude.
- Rewarding recent continuous resource collection makes route continuity itself part of the hero's power and gives opponents an economic counterplay surface beyond simply killing the hero.
- A control spell can let the player **voluntarily buy magnitude with delay** while exposing the same deadline to opponents, turning execution time into a shared risk/counterplay resource.
- An area armor-reduction spell can bridge farming, physical spell burst, and ordinary attacks when the rest of the kit uses the same mitigation system.
- A transformation that changes BAT, movement, and regeneration can increase both resource-processing throughput and the rate at which purchased combat power is realized.
- A stacking debuff shared across attacks and spells can make the kit remember **how long offensive contact has been maintained**, with the resulting slow feeding back into future contact.
- A surplus-economy hero benefits from an outlet that converts excess personal wealth into allied capability; tying the return to future active production preserves the hero's defining gameplay better than a fully passive income stream.

These are case-supported observations, not yet cross-hero principles.

## Sources

Current and historical factual material was checked against:

- Liquipedia - Alchemist: https://liquipedia.net/dota2/Alchemist
- Liquipedia - Alchemist Changelogs: https://liquipedia.net/dota2/Alchemist/Changelogs
- Liquipedia - Alchemist Archive / old ability details: https://liquipedia.net/dota2/Archive%3AAlchemist
- Liquipedia - Version 6.79: https://liquipedia.net/dota2/Version_6.79
- Liquipedia - Version 7.36: https://liquipedia.net/dota2/Version_7.36
- Liquipedia - Version 7.37e: https://liquipedia.net/dota2/Version_7.37e
- Liquipedia - Version 7.38: https://liquipedia.net/dota2/Version_7.38
- Liquipedia - Version 7.39: https://liquipedia.net/dota2/Version_7.39
- Liquipedia - Version 7.41: https://liquipedia.net/dota2/Version_7.41
- Liquipedia - Version 7.41a: https://liquipedia.net/dota2/Version_7.41a
- Liquipedia - Version 7.41c: https://liquipedia.net/dota2/Version_7.41c
- Dotabuff - Alchemist current abilities: https://www.dotabuff.com/heroes/alchemist/abilities
- DotaCoach - Alchemist current 7.41e stats and abilities: https://dotacoach.gg/en/heroes/alchemist

Where a historical mechanic had many balance-only parameter changes, this document records a representative or mature parameter set rather than reproducing the full patch chronology. The current Unstable Concoction source discrepancy is preserved explicitly rather than resolved by inventing a missing balance patch.
