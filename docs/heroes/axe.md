# Axe - Hero Design Case

**Status:** First durable pass

**Current factual reference state:** Dota 2 7.41e. The 7.41e patch reduced Axe's base Agility from 20 to 18 and Battle Hunger DPS from 12/18/24/30 to 12/16/20/24. Historical material below is organized by design branch rather than by patch chronology.

## Design identity

Axe is built around changing the value of enemy attacks. Berserker's Call can replace enemy intent with an order to attack Axe; Counter Helix converts those attacks into damage generation; Culling Blade changes the normal death rule once an enemy enters a low-health region. Secondary and historical branches repeatedly strengthen, connect, or extend those three ideas.

## Current combat chassis

| Property | Current value |
| --- | ---: |
| Primary attribute | Strength |
| Strength | 25 + 2.7 |
| Agility | 18 + 1.7 |
| Intelligence | 18 + 1.6 |
| Starting health | 670 |
| Starting health regeneration | 4.5/s total, including 2 base |
| Starting mana | 291 |
| Starting mana regeneration | 0.9/s |
| Starting armor | 3 |
| Starting attack damage | 56-60 |
| Attack type / range | Melee / 150 |
| Base attack speed | 100 |
| Base attack time | 1.7 s |
| Attack animation | 0.4 + 0.5 s |
| Movement speed | 315 |
| Turn rate | 0.6 |
| Vision | 1800 / 800 |

### Compact note

The chassis is durable but does not by itself explain Axe's willingness to stand inside multiple attackers. That behavior is produced mainly by Call, Helix, and armor-based progression rather than by unusually extreme base armor.

## One Man Army

**Current - Innate**

- Passive, breakable.
- Axe gains Strength equal to **50% of his current Armor** while no allied hero is within **700** range.
- The effect fades over **3 seconds** after an allied hero enters the radius.
- Temporary armor can therefore also temporarily increase the Strength conversion while the isolation condition is satisfied.

### Design branch: armor as a cross-system resource

This turns Armor from pure mitigation into a source of Strength. The ally-distance condition makes the conversion spatial rather than unconditional: the strongest version of the effect rewards Axe for being relatively isolated from allied heroes.

## Berserker's Call

### Current factual baseline

| Property | Value |
| --- | --- |
| Cast | No target |
| Radius | 315 |
| Bonus armor | 12 / 13 / 14 / 15 |
| Taunt duration | 2.1 / 2.4 / 2.7 / 3 s |
| Cooldown | 18 / 16 / 14 / 12 s |
| Mana cost | 90 / 100 / 110 / 120 |
| Debuff immunity | Taunt pierces debuff immunity |
| Level 15 talent | +10 Call armor |
| Level 25 talent | +85 Call radius |
| Current Shard | Applies Battle Hunger to affected units; repeated Hunger applications become independent instances |

The taunt replaces current enemy orders and forces affected units to attack Axe for the duration, subject to ordinary disabling and pathing rules.

### Design branch: direct taunt

The core branch is simple: control does not merely stop enemy action; it substitutes a specific action - **attack Axe**. That substituted action is the input Counter Helix wants.

### Historical design branch: Call Out

A historical facet strengthened Call by increasing Axe's Call armor and giving taunted enemies **+45 attack speed** for the taunt duration. The armor increase was initially +5 and later reached +6 before the branch was removed.

**Compact design note:** the same modifier increases Axe's danger and his Helix input rate. It is a clean example of risk and reward sharing one input.

### Design branch: Call distributes Battle Hunger

The current Shard applies Battle Hunger to all affected units. A historical Scepter explored the same connection while also reducing Call cooldown and coupling Hunger to armor manipulation.

**Compact design note:** an upgrade can deepen a kit without adding a new button by attaching a secondary mechanic to the hero's existing core action.

## Battle Hunger

### Current factual baseline

| Property | Value |
| --- | --- |
| Cast | Unit target |
| Damage type | Pure |
| Cast range | 600 / 700 / 800 / 900 |
| Damage per second | 12 / 16 / 20 / 24 |
| Duration | 12 s |
| Movement slow | 18% / 22% / 26% / 30% |
| Slow condition | Target is facing away from Axe |
| Cooldown | 20 / 15 / 10 / 5 s |
| Mana cost | 50 / 60 / 70 / 80 |
| Early termination | Ends when the affected unit kills another unit |
| Level 10 talent | +8% Axe move speed per active Battle Hunger |
| Level 15 talent | +8 DPS |
| Shard interaction | Independent stacked instances are possible when reapplied through the upgrade |

### Design branch: task-based debuff escape

The target can end Hunger early by killing another unit. The debuff therefore creates an explicit action goal rather than asking the target only to wait out a duration or spend a dispel.

### Design branch: facing-dependent pursuit pressure

The slow applies only while the target faces away from Axe. This changes the movement choice rather than only the movement number: turning to flee activates stronger pursuit pressure.

### Historical design branch: debuff count becomes Axe movement

A historical form gave Axe movement speed for each enemy affected by Battle Hunger; one mature state used **12/13/14/15%** enemy slow and the same per-target self movement-speed bonus. The current level 10 talent preserves a lighter version of this idea at **+8% movement speed per active Hunger**.

### Historical design branch: Armor-scaled physical Hunger

Battle Hunger was also explored as a physical-damage ability with damage of **10/15/20/25 + 1 x Axe's Armor** per second. In that branch the old self movement-speed component was removed and the facing-away slow became part of the base design. A high-level talent later explored a **2x armor multiplier**.

**Compact design note:** this branch made Armor simultaneously a defensive stat and an offensive scaling resource, directly linking Call's temporary armor to Hunger damage.

### Historical design branch: area suppression

An Aghanim branch turned Hunger into a **400-radius area-targeted** effect and applied about **30% outgoing damage reduction** to affected enemies. Another Scepter branch connected Call to Hunger and made Hunger reduce enemy armor by **7**, while granting Axe **7 armor per affected enemy hero** and **3.5 per creep**.

**Compact design note:** the same base debuff was explored as lane pressure, pursuit pressure, group damage suppression, and armor transfer. Those are meaningfully different roles rather than minor balance variants.

## Counter Helix

### Current factual baseline

| Property | Value |
| --- | --- |
| Type | Passive |
| Damage type | Pure |
| Radius | 275 |
| Damage | 100 / 120 / 140 / 160 |
| Incoming attacks required | 7 / 6 / 5 / 4 |
| Base cooldown | 0.3 s |
| Level 20 talent | +40 damage |

**Current Scepter**

- Axe's own successful attacks also advance a separate required-attack tally using the same **7/6/5/4** requirement; outgoing and incoming tallies operate simultaneously.
- Removes the **0.3 s** Helix cooldown.
- Helix applies a **6 s** debuff causing the affected enemy to deal **12% less total outgoing attack damage to Axe per stack**, up to **5 stacks** (**60%** maximum).

### Design branch: probability-based retaliation

A mature historical version used pseudo-random proc chance rather than deterministic accumulation:

- Proc chance: **17% / 18% / 19% / 20%**.
- Representative damage: **60 / 100 / 140 / 180**.
- Representative radius: **300**.
- Cooldown: **0.3 s**.

Each incoming attack was an independent chance to create value. More attackers increased expected Helix frequency, but the exact result remained stochastic.

### Current design branch: deterministic incoming-attack accumulation

The current **7/6/5/4** trigger changes every valid incoming attack from a lottery ticket into deterministic progress toward the next Helix.

**Compact design note:** the hero fantasy is similar in both branches, but predictability and planning are materially different.

### Historical design branch: Axe attacks can directly proc Helix

An earlier Shard let Axe's normal attacks trigger Counter Helix using its proc chance, ignored the Helix internal cooldown for those attack procs, and granted attack speed. The attack-speed bonus began at **+20** and was later increased to **+35** before that branch was replaced.

The current Scepter revisits the same design question in deterministic form by letting Axe's attacks advance a Helix tally.

**Compact design note:** allowing safe or proactive actions to generate a resource that was originally supplied by enemy aggression increases agency but can dilute the identity of "benefiting from being attacked."

### Design branch: Helix reduces the future cost of being attacked

The attack-damage-reduction branch began as a Shard effect and later moved to Scepter. Historical versions explored **20% x 5 stacks** and **15% x 6 stacks**; the current state is **12% x 5 stacks**.

**Compact design note:** the payoff from the core retaliation mechanic also helps pay its future survival cost, allowing the "stand among attackers" behavior to remain viable against higher late-game attack damage.

## Culling Blade

### Current factual baseline

| Property | Value |
| --- | --- |
| Cast | Unit target |
| Cast range | 175 |
| Normal damage type | Pure |
| Damage / instant-kill threshold | 275 / 375 / 475 |
| Level 25 talent | +150 damage and kill threshold -> 425 / 525 / 625 |
| Cooldown on failed/nonlethal use | 80 / 75 / 70 s |
| Mana cost | 100 / 125 / 150 |
| Cooldown on successful hero execution | 0 |
| Kill-buff radius | 900 |
| Kill movement-speed bonus | 20% / 25% / 30% |
| Kill armor bonus | 10 / 15 / 20 |
| Kill-buff duration | 6 s |
| Level 10 talent | +3 s kill-buff duration |
| Permanent armor per hero killed by Culling | 1 / 1.5 / 2 |

When target current health satisfies the threshold, Culling uses an instant-kill rule rather than ordinary damage resolution. This allows it to defeat some survival mechanics that operate by preventing ordinary lethal damage or by making effective health much larger than current health.

### Design branch: separate damage and execution threshold

Historically the nonlethal damage and the current-health execution threshold were separate values. Later the ability was simplified so the damage value and kill threshold use the same number.

**Compact design note:** separating the two parameters lets a designer tune "failed cast value" independently from the size of the alternate death region; unifying them makes the ability easier to read and compare.

### Design branch: execution resets the ability

A successful hero execution sets the cooldown to **0**. Failure leaves the long ordinary cooldown. This creates a high contrast between correct threshold use and premature use.

### Design branch: successful execution starts the next fight phase

Successful executions have repeatedly granted team tempo rather than simply ending a target. Historical forms emphasized movement and attack speed; the current branch grants movement speed plus armor to nearby allies.

**Compact design note:** the execute can act as a chain-fight starter: successful use supplies movement, defense, and immediate ability reuse to find the next low-health target.

### Design branch: execution creates permanent growth

Current Culling kills grant **1/1.5/2 permanent armor**. This means correct execution of the ultimate permanently improves a stat that supports Axe's other defining behavior - surviving while enemies attack him.

### Historical design branch: Scepter directly expands execution power

Older Scepter designs directly increased Culling's kill thresholds and greatly reduced its cooldown. One classic upgraded threshold set was **300/450/625**, with an upgraded cooldown as low as **6 s** in later tuning of that branch.

**Compact design note:** this is a conventional peak-power upgrade compared with later Axe upgrades that instead connect or sustain the rest of the kit.

## Coat of Blood [Historical / Removed]

A historical innate gave Axe permanent armor for hero kills generally and a larger reward for Culling Blade kills.

Representative forms included:

- **+1 permanent armor per hero kill**, with Culling kills using a **2x** factor.
- A later scaling form of **0.4 / 0.6 / 0.8 / 1 armor per kill**, again with a **2x** Culling factor.

The ability was later removed and Culling Blade itself once again became the direct owner of the permanent-armor reward.

### Compact design note

This branch broadened the growth condition from "execute correctly" to "get hero kills," while still rewarding the signature execute more. The current design is stricter about tying permanent growth to the signature mechanic.

## Current talents

| Level | Left | Right |
| --- | --- | --- |
| 10 | +8% move speed per active Battle Hunger | +3 s Culling Blade kill-buff duration |
| 15 | +10 Berserker's Call armor | +8 Battle Hunger DPS |
| 20 | +40 Counter Helix damage | +15 Strength |
| 25 | +150 Culling Blade damage / kill threshold | +85 Berserker's Call radius |

## Kit relationships

- **Call -> forced attacks -> Helix:** one skill directly manufactures the event another skill values.
- **Call armor -> survival:** Call helps Axe survive the very attacks it forces.
- **Culling success -> permanent armor -> stronger survival / One Man Army conversion:** correct ultimate execution feeds the physical durability economy used elsewhere in the kit.
- **Shard Call -> Hunger:** a secondary spell can be distributed through the hero's core control action.
- **Scepter Helix -> attack-damage reduction:** successful retaliation reduces the future cost of continuing to be attacked.

## Compact design conclusions

- A character can gain identity by **revaluing an ordinarily negative event**: incoming attacks are both danger and a resource.
- Natural skill synergy can come from **one ability creating the world-state another ability needs**, rather than explicit combo multipliers.
- Risk and reward can share the same input, as the Call Out branch demonstrated with enemy attack speed.
- A rule-level ability such as Culling Blade can create stronger identity than simply increasing damage because it changes which defensive systems matter.
- Permanent growth is especially coherent when successful execution of the signature mechanic improves another core behavior rather than only amplifying itself.

These are case-supported observations, not yet cross-hero principles.

## Sources

Current and historical factual material was checked against:

- Liquipedia - Axe: https://liquipedia.net/dota2/Axe
- Liquipedia - Axe Changelogs: https://liquipedia.net/dota2/Axe/Changelogs
- Liquipedia - archived Axe changelog: https://liquipedia.net/dota2/Archive:Axe/Changelog
- Liquipedia - Hero Attributes Table: https://liquipedia.net/dota2/Table_of_hero_attributes
- Liquipedia - Version 7.41e: https://liquipedia.net/dota2/7.41e

Where a historical mechanic had many balance-only parameter changes, this document records a representative or mature parameter set rather than reproducing the full patch chronology.
