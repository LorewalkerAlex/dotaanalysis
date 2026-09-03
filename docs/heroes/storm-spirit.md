# Storm Spirit - Hero Design Case

**Status:** First durable pass

**Current factual reference state:** Dota 2 7.41e. Storm Spirit received no hero changes in 7.41e; the latest Storm-specific balance changes are from 7.41d, which reduced base attack speed from 115 to 110 and reduced the level 25 Overload bounce damage factor from 65% to 50%. Historical material below is organized by design branch rather than patch chronology.

## Design identity

Storm Spirit converts mana into a continuously adjustable budget for movement, engagement depth, and combat tempo. Ball Lightning lets the player choose how far to move and therefore how much mana to spend; its repeated activation fee also makes one long movement different from many short movements. Overload then reconnects every spell cast to the normal attack system, while Electric Vortex converts Storm's chosen position into a control point. Galvanized makes successful participation improve the regeneration economy that sustains the loop without directly granting damage.

## Current combat chassis

| Property | Current value |
| --- | ---: |
| Primary attribute | Intelligence |
| Strength | 21 + 2.0 |
| Agility | 22 + 2.6 |
| Intelligence | 23 + 3.7 |
| Starting health | 582 |
| Starting health regeneration | 2.6/s total, including 0.5 base |
| Starting mana | 351 |
| Starting mana regeneration | 1.15/s total, with 0 base mana regeneration |
| Starting armor | 4.67 |
| Starting attack damage | 47-57 |
| Attack type / range | Ranged / 480 |
| Projectile speed | 1100 |
| Base attack speed | 110 |
| Base attack time | 1.6 s |
| Attack animation | 0.5 + 0.3 s |
| Movement speed | 285 |
| Turn rate | 0.8 |
| Vision | 1800 / 800 |

### Compact note

The chassis is not unusually fast on foot and currently has no base mana-regeneration allowance beyond Intelligence. Storm's extreme mobility and repeated combat access are therefore created by the ability/resource economy rather than by high ordinary movement speed or free baseline mana recovery.

## Galvanized

### Current factual baseline - Innate

- Passive; new kill-generated charges are disabled by Break.
- Gains **1 held charge** when Storm Spirit is credited with a hero kill or when an enemy hero dies within **1200** range.
- Gains another charge for each completed group of **3 hero levels**.
- Each held charge grants **+0.2 mana regeneration**.
- Every time a charge is gained, Storm also permanently gains **+0.1 mana regeneration**.
- Death removes **2 held charges** but does not remove the permanent regeneration already gained from acquiring them.

### Design branch: permanent growth plus losable current momentum

Each charge acquisition creates two layers of value: a permanent +0.1 regeneration increase and a +0.2 component that depends on retaining the held charge. Death can therefore reduce recent momentum without erasing the full history of successful participation.

### Historical design branch: ultimate-level regeneration spikes

When Galvanized was introduced, leveling Ball Lightning granted **5 charges** at once; that was quickly reduced to **3**. The branch was later removed, and current progression grants one charge every three hero levels instead.

**Compact design note:** the old model concentrated regeneration growth at ultimate-level milestones, while the current model smooths that growth across ordinary hero levels. Combat participation remains a separate acceleration source in both models.

## Static Remnant

### Current factual baseline

| Property | Value |
| --- | --- |
| Cast | Point target; Alt-Cast places it in place |
| Cast range | 800 |
| Remnant speed | 300 |
| Activation delay | 0.75 s |
| Maximum pre-activation travel | about 225 |
| Trigger radius | 235 |
| Damage radius | 300 |
| Damage | 100 / 160 / 220 / 280 magical |
| Duration | 12 s |
| Vision | 100 flying vision around the remnant |
| Cooldown | 3.5 s |
| Mana cost | 70 / 80 / 90 / 100 |
| Level 15 talent | +60 damage |
| Level 20 talent | -1.25 s cooldown |

The remnant is created at Storm Spirit's position and then moves toward the selected point. It begins checking for enemies after the activation delay; Alt-Cast preserves the older behavior of leaving it at Storm's current location.

### Design branch: self-positioned delayed trap

For most of modern Storm's history, Static Remnant was a no-target ability that placed the delayed trigger at Storm's own position. That made Storm's body the delivery mechanism: to put the trap somewhere dangerous, he first had to occupy that location.

### Historical/current design branch: Static Slide -> mobile base Remnant

The 7.36 **Static Slide** facet allowed vector-targeted Remnants to move from Storm toward a selected point. It began at **325 movement speed**, was reduced to **300**, and gained an Alt-Cast path to preserve stationary placement. In 7.41 the facet was removed, but its central movement behavior was absorbed into the base skill as the current point-targeted design.

**Compact design note:** the mobile branch reduces how much of the placement burden must be paid by Storm's own position. Because the remnant still spawns on Storm and is inactive for 0.75 seconds, it remains a prediction/placement tool rather than becoming an ordinary projectile nuke.

### Current source note

Liquipedia's current Storm overview displays Static Remnant damage as **100/160/240/280**, but its 7.36b changelog explicitly records the change **120/180/240/300 -> 100/160/220/280**, and current 7.41e data mirrors the latter set. This case therefore records **100/160/220/280**.

## Electric Vortex

### Current factual baseline

| Property | Value |
| --- | --- |
| Cast | Unit target |
| Cast range | 300 |
| Pull distance | 180 / 220 / 260 / 300 |
| Disable / pull duration | 1.1 / 1.4 / 1.7 / 2 s |
| Cooldown | 20 / 18 / 16 / 14 s |
| Mana cost | 60 / 70 / 80 / 90 |
| Dispel | Strong dispel |
| Level 20 talent | +0.2 s duration |

The target is pulled toward Storm Spirit, so Storm's own location determines the destination of the control.

### Historical design branch: control also commits Storm's movement

The 6.58 rework version applied a **50% movement-speed slow to Storm for 3 seconds** whenever he used Vortex. That self-slow remained part of the design for years and was removed in 7.21c.

**Compact design note:** the old branch made the act of pulling an enemy toward Storm simultaneously reduce Storm's ability to reposition afterward. Removing the self-slow made Vortex fit more freely into repeated Ball Lightning repositioning.

### Current Scepter branch: self-position becomes an area control center

Aghanim's Scepter changes Vortex into a non-unit-targeted effect on visible enemies within **475 radius** around Storm Spirit.

This branch dates to the first Storm Scepter design in 6.87 and changes the main decision from **which target to pull** to **where Storm should place himself before casting**. Ball Lightning supplies unusually flexible access to that control center.

### Historical / removed facet: Shock Collar

The 7.36 **Shock Collar** facet added a debuff to Vortex. Its first form caused an affected enemy's attack to trigger an Overload explosion on that enemy. In 7.37 the next offensive attack was instead redirected to the attacker itself while also triggering Overload. The facet was removed in 7.41.

**Compact design note:** normal Overload is generated by Storm's own spell-to-attack rhythm; Shock Collar briefly explored making the enemy's decision to attack feed or reverse that same mechanic.

## Overload

### Current factual baseline

| Property | Value |
| --- | --- |
| Type | Passive; Shard adds an active component |
| Trigger | Casting an ability |
| Storage | Ordinary spell-generated charges do not stack |
| Delivery | Storm's next attack |
| Damage | 25 / 50 / 75 / 100 magical |
| Radius | 300 |
| Movement slow | 80% |
| Attack-speed slow | 90 |
| Slow duration | 0.8 s |
| Level 10 talent | +25 percentage points movement slow and +25 attack-speed slow |
| Level 25 talent | 2 attack bounces; current bounce damage factor 50% |

Items do not generate ordinary Overload charges. Because a normal charge does not stack with another normal charge, efficient use rewards alternating spell casts and attacks rather than casting the whole kit before attacking.

### Historical design branch: attacks generate the empowered attack

Before the 6.58 rework, Overload accumulated from successful normal attacks. A mature pre-rework model required **8/7/6/5 attacks** to prepare the empowered attack and dealt **30/45/60/75** magical damage in a **350** radius.

### Current design branch: spells generate the empowered attack

The 6.58 rework inverted the resource flow: every ability cast prepares the next attack. That creates the modern repeating rhythm:

```text
spell / Ball Lightning
    -> Overload ready
    -> attack
    -> next spell
    -> Overload ready
    -> attack
```

**Compact design note:** the rework changed Overload from an attack system that periodically amplified itself into the bridge that repeatedly reconnects the spell system to ordinary attacks.

### Shard branch: pre-store and distribute the core attack payoff

Current Aghanim's Shard adds an active Overload cast:

- Radius: **750**.
- Gives Storm and nearby allied heroes **3 Overload charges**.
- Grants **+40 attack speed**.
- Duration: up to **12 seconds** or until the charges are consumed.
- Cooldown: **30 seconds**.
- Mana cost: **100**.

The design first appeared in 7.28 as a separate Shard-granted ability named **Electric Rave**, with the same three charges, 750 radius, +40 attack speed, 12-second duration, 30-second cooldown, and an initial 150 mana cost. In 7.29 it was merged into Overload as the current active component; the mana cost was later reduced to 100.

**Compact design note:** the Shard temporarily relaxes Overload's normal one-cast/one-next-attack rhythm by pre-storing three attacks and lets Storm export the payoff to allied heroes.

## Ball Lightning

### Current factual baseline

| Property | Value |
| --- | --- |
| Cast | Point target |
| Cast range | Global |
| Cooldown | 0 |
| Damage type | Magical |
| Damage radius | 200 |
| Damage per 100 distance | 6 / 10 / 14 |
| Travel speed | 1400 / 1850 / 2300 |
| Activation mana cost | 25 + 7.5% maximum mana |
| Mana cost per 100 distance | 10 + 0.65% maximum mana |
| Defensive state | Invulnerable while traveling |
| Other movement rules | Destroys trees; cannot be initiated while rooted |
| Actions during travel | Can use abilities and items |
| Level 25 talent | Creates a Static Remnant every 450 distance |

Ball Lightning stops when Storm reaches the selected point or depletes his mana.

### Core design branch: distance is a continuously purchased action

Ball Lightning has no ordinary cooldown and no fixed maximum travel range. Instead, every cast pays an activation fee plus a distance-dependent cost. The player therefore chooses not only whether to move, but **how much distance to purchase with the current mana pool**.

### Design branch: activation cost versus distance cost

The cost formula has two distinct levers:

- **activation cost** prices how often Storm can start a new Ball Lightning;
- **per-distance cost** prices how far each individual movement can travel.

Many short zips can create more repositioning windows and more Overload triggers than one long zip, but each short cast pays the activation fee again.

Representative historical models:

| Branch | Activation cost | Cost per 100 distance |
| --- | --- | --- |
| 6.58 initial Ball Lightning | 15 + 7% max mana | 10 + 1% max mana |
| After 6.82 distance-model change | 15 + 7% max mana | 12 + 0.7% max mana |
| After 6.85 activation increase | 30 + 8% max mana | 12 + 0.7% max mana |
| Current mature model | 25 + 7.5% max mana | 10 + 0.65% max mana |

The 7.31d unannounced cost changes were explicitly reverted and are not treated as a durable design branch here.

**Compact design note:** maximum mana expands the available budget but also raises the percentage-based price of using it. Mana regeneration therefore has a different role from mana capacity: it increases how quickly Storm can rebuild the next movement/combat budget without increasing the percentage coefficient of each cast.

### Historical design branch: Lightning Grapple

Before 6.58, Storm's ultimate mobility was **Lightning Grapple**:

- Point targeted.
- Cast range: **700 / 1050 / 1400**.
- Radius: **200**.
- Cooldown: **35 seconds**.
- Mana cost: **100**.
- Storm and nearby affected heroes were pulled toward the target point at **1200 speed**.
- The movement did **not** make Storm or affected units invulnerable.

**Compact design note:** Grapple used the conventional fixed-range/fixed-cooldown/fixed-cost model and could move other heroes. Ball Lightning replaced it with personal, cooldown-free movement whose distance is bounded primarily by the mana economy.

### Level 25 branch: the movement path starts placing another ability

The current level 25 talent creates a Static Remnant every **450 distance** traveled. The same Ball Lightning expenditure can therefore buy position change, travel damage, an Overload trigger, and repeated spatial threat placement along the path.

## The 6.58 kit rework as a design boundary

The 6.58 rework is worth preserving as a whole-kit branch rather than as four unrelated patch notes. Before the rework, Storm's kit included:

- **Electric Rave** - toggled mana drain for attack speed;
- **Barrier** - a unit-targeted magical-damage shield for allies;
- **Overload** - attack-count accumulation;
- **Lightning Grapple** - fixed-cooldown, fixed-range movement that could pull other heroes.

6.58 replaced that complete model with Static Remnant, Electric Vortex, spell-triggered Overload, and Ball Lightning. The modern kit therefore emerged together around repeated spell casts, self-positioning, normal-attack follow-through, and mana-priced mobility.

## Current talents

| Level | Left | Right |
| --- | --- | --- |
| 10 | +1.5 mana regeneration | +25/25% Overload attack-speed / movement-speed slow |
| 15 | +60 Static Remnant damage | +250 health |
| 20 | -1.25 s Static Remnant cooldown | +0.2 s Electric Vortex duration |
| 25 | Static Remnant every 450 Ball Lightning distance | 2x Overload attack bounce |

The current right level-25 branch uses **2 bounces** with a **50% bounce damage factor** after the 7.41d reduction.

## Kit relationships

- **Galvanized -> mana regeneration -> Ball Lightning / spell-loop recovery:** participation permanently and temporarily improves the resource economy that determines how often Storm can re-enter the loop.
- **Ball Lightning -> chosen self-position -> Electric Vortex:** movement selects the location from which single-target or Scepter area control is resolved.
- **Every ability cast -> Overload -> attack:** ordinary spell-generated charges do not stack, so the kit rewards alternating abilities and attacks rather than unloading all abilities before right-clicking.
- **Vortex -> controlled attack window -> Overload:** Vortex creates time for Storm to cash out the charge it also generates; the Overload slow then extends contact.
- **Short Ball Lightning casts -> more reposition / Overload opportunities, but repeated activation fees:** engagement tempo and mana efficiency compete directly.
- **Remaining mana -> future options:** mana spent entering a fight is also mana unavailable for later attacks, repositioning, or escape.

## Compact design conclusions

- A mobility skill can price **distance** with a continuous resource instead of pricing use primarily with cooldown, letting the player choose engagement depth directly.
- Separating an activation fee from a distance fee makes **how many movements** and **how far to move** distinct decisions even when total distance is similar.
- A spellcaster can preserve normal attacks as a core action by making every spell generate a non-stacking attack payoff; the storage rule itself creates the spell-attack rhythm.
- Position can become an explicit input to control design: Scepter Vortex is strongest not because it gains cast range, but because Ball Lightning lets Storm choose where the control center will exist.
- Permanent and losable portions of the same growth resource can reward long-term participation while preserving a meaningful death penalty on recent momentum.
- Using the same mana pool for initiation, continued offense, repositioning, and escape makes **future optionality** part of the real cost of an aggressive movement.

These are case-supported observations, not yet cross-hero principles.

## Sources

Current and historical factual material was checked against:

- Liquipedia - Storm Spirit: https://liquipedia.net/dota2/Storm_Spirit
- Liquipedia - Storm Spirit Changelogs: https://liquipedia.net/dota2/Storm_Spirit/Changelogs
- Liquipedia - Storm Spirit Old Abilities: https://liquipedia.net/dota2/Storm_Spirit/Old_Abilities
- Liquipedia - Hero Attributes Table: https://liquipedia.net/dota2/Table_of_hero_attributes
- Liquipedia - Version 6.58: https://liquipedia.net/dota2/Version_6.58
- Liquipedia - Version 6.82: https://liquipedia.net/dota2/Version_6.82
- Liquipedia - Version 6.85: https://liquipedia.net/dota2/Version_6.85
- Liquipedia - Version 6.87: https://liquipedia.net/dota2/Version_6.87
- Liquipedia - Version 7.41d: https://liquipedia.net/dota2/Version_7.41d
- DotaCoach - Storm Spirit 7.41e current ability values: https://dotacoach.gg/en/heroes/storm-spirit

Where a historical mechanic had many balance-only parameter changes, this document records a representative or mature parameter set rather than reproducing the full patch chronology.
