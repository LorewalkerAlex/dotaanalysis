# Chen - Hero Design Case

**Status:** First durable pass

**Current factual reference state:** Dota 2 7.41e. Chen's latest direct hero change is 7.41b, which increased Holy Persuasion outgoing damage amplification to 5%/10%/15%/20%. Penitence's current 50/100/150/200 pure damage comes from 7.41a. Historical material below is organized by design branch rather than patch chronology.

## Design identity

Chen does not own a closed hero-only capability set. Holy Persuasion turns public non-hero units into a dynamic external ability pool, so the hero's available control, dispel, displacement, aura, summon, and damage tools depend partly on the units that exist in the world and on which limited army slots Chen chooses to spend on them. His fixed hero abilities then organize that changing roster: Penitence creates a common focus-fire target, Divine Favor sustains and protects units, Hand of God provides global recovery, and Zealot supplies a reliable internal unit plus army logistics and sacrifice value.

## Current combat chassis

| Property | Current value |
| --- | ---: |
| Primary attribute | Intelligence |
| Strength | 23 + 2.0 |
| Agility | 15 + 2.1 |
| Intelligence | 19 + 3.2 |
| Starting health | 626 |
| Starting health regeneration | 2.55/s total, including 0.25 base |
| Starting mana | 303 |
| Starting mana regeneration | 1.45/s total, including 0.5 base |
| Starting armor | 1.5 |
| Starting attack damage | 48-58 |
| Attack type / range | Ranged / 650 |
| Projectile speed | 1100 |
| Base attack speed | 100 |
| Base attack time | 1.7 s |
| Attack animation | 0.5 + 0.5 s |
| Movement speed | 305 |
| Turn rate | 0.6 |
| Vision | 1800 / 800 |

### Compact note

Chen's chassis is not the main source of his unusual action space. The defining variance comes from which external units he controls and how he manages those units, rather than from an extreme personal mobility, durability, or attack profile.

## Holy Persuasion

### Current factual baseline

| Property | Value |
| --- | --- |
| Cast | Unit target |
| Cast range | 600 |
| Max persuaded units | 1 / 2 / 3 / 4 |
| Maximum creep level | 3 / 4 / 5 / 6 |
| Persuaded creep minimum health | 400 + 50 x Chen hero level |
| Gold bounty received | 25% / 50% / 75% / 100% |
| Movement-speed bonus | 5 / 10 / 20 / 30 |
| Outgoing damage amplification | 5% / 10% / 15% / 20% |
| Cooldown | 15 s |
| Mana cost | 110 / 130 / 150 / 170 |
| Level 15 talent | +12 percentage points persuaded-unit outgoing damage amplification |
| Level 20 talent | +1300 persuaded-unit minimum health |

Persuading a unit restores its health and mana and applies the current Persuasion bonuses. If Chen is already at the unit limit, the oldest persuaded unit other than the Zealot is replaced. The Zealot itself counts as one of Chen's persuaded units.

Chen can also globally target an already-persuaded creep that has not taken damage recently to dismiss it. This mode costs no mana and uses a 3-second cooldown, allowing deliberate roster replacement instead of relying only on automatic oldest-unit replacement.

### Design branch: external capability acquisition

Holy Persuasion does not define one fixed summoned-unit moveset. It gives Chen access to abilities already owned by public neutral creeps. Representative current examples include:

| Persuaded unit | Representative capability | Design function |
| --- | --- | --- |
| Centaur Conqueror | War Stomp: 250 radius, 1.6 s hero stun | Close-range area control |
| Satyr Banisher | Purge: basic dispel; enemy cast also applies a decaying 50% movement slow | Dispel and pursuit control |
| Wildwing Ripper | Hurricane: vector-targeted 400-distance forced movement | Ally/enemy displacement |
| Alpha Wolf | Packleader's Aura: +20% main attack damage in aura | Team attack amplification |
| Dark Troll Summoner | Raise Dead: summons 3 Skeleton Warriors | Secondary unit generation |

These units also bring bodies, attacks, and sometimes additional auras or passives. An army slot therefore selects an ability package rather than only a damage stat line.

### Design branch: access progression rather than only magnitude progression

Holy Persuasion's 3/4/5/6 creep-level cap changes which unit packages are legal as the skill is leveled. For example, Centaur Conqueror, Alpha Wolf, and Wildwing Ripper are unavailable at lower Persuasion levels but become legal later; level 4 can persuade all ordinary neutral creeps allowed by the ability.

**Compact design note:** progression can expand the set of actions a character may acquire, rather than only increasing the magnitude of an already-owned action.

### Design branch: finite army slots create roster pressure

Because the army size is bounded, capability acquisition has an opportunity cost. Taking a new control, aura, dispel, or summon unit can require retiring an existing package. The 7.41 dismissal mode makes that trade explicit by letting Chen deliberately remove a safe persuaded creep from anywhere on the map.

### Current Shard branch: unlock a second external pool

Aghanim's Shard:

- Allows Ancient creeps to be persuaded.
- The Ancient limit is 1 / 2 / 3 according to Hand of God level, and those units still consume the ordinary Persuasion unit limit.
- Increases specified neutral-creep abilities by one level and can unlock their otherwise unavailable fourth level.

Examples of upgradeable abilities include Centaur War Stomp, Satyr Purge, Alpha Wolf Critical Strike, Ancient Black Dragon Fireball, Ancient Granite Golem Granite Aura, and Ancient Ice Shaman Icefire Bomb.

Neutral creep abilities normally grow according to the neutral-creep progression state at acquisition and do not simply keep upgrading while controlled. Shard therefore changes both **which unit classes are accessible** and **how far selected borrowed abilities can scale**.

### Compact design note

The complexity of Holy Persuasion is not removed from the game by keeping Chen's own spell list short. It is transferred into world knowledge, route planning, unit acquisition, army-slot management, keeping units alive, and multi-unit control.

## Zealot

### Current factual baseline - Innate

- Whenever Chen respawns, he is joined by one Zealot; a killed Zealot respawns after **60 seconds**.
- The Zealot uses the current allied melee-creep progression, including Super/Mega progression, but is a dedicated Chen unit.
- It has **125 attack range**, **2.5 base health regeneration**, and gains **+2 base attack damage per Chen hero level**.
- It is considered a persuaded unit and receives Holy Persuasion's bonuses.
- Level 10 talent: **+25% Zealot max health and base attack damage**.

**Army recall component**

- Global targeting of a Chen-controlled unit starts a **6-second** teleport to Chen.
- Self-casting recalls all Chen-controlled units.
- Offensive enemy player-based damage can cancel the delayed recall.
- Ability cooldown: **10 seconds**; mana cost: **50**.

**Martyrdom**

- The Zealot sacrifices itself and launches a projectile at an allied or enemy unit.
- Enemy damage: **25 + 20% of the Zealot's current health**.
- Ally heal: **50%** of that value.
- Cast range: **500**; cooldown: **10 seconds**; mana cost: **50**.

The detailed current Zealot ability data and current third-party patch mirrors use current health for Martyrdom. Some 7.41 summary text describes the percentage as max health; this case follows the current ability definition.

### Historical design branch: world-only acquisition

Before guaranteed summon systems, Chen's special unit capabilities came from units he could actually find and persuade in the world. This maximized environmental dependence: if the desired creep was not available, that capability was not guaranteed.

### Historical design branch: Summon Convert [Removed]

From 7.36 to 7.40, Summon Convert provided one guaranteed unit according to a selected Facet. Mature branches included:

- Centaur Convert: Centaur Courser -> Centaur Conqueror as Holy Persuasion advanced.
- Hellbear Convert: Hellbear -> Hellbear Smasher.
- Troll Convert: Hill Troll -> Dark Troll Summoner.
- Satyr Convert: Satyr Mindstealer -> Satyr Tormenter.
- Marshmage Convert: Marshmage Apprentice -> Marshmage.

A mature Convert used **220 + 80 x Chen hero level** health, counted as a persuaded unit, inherited Holy Persuasion's non-health bonuses, and died with Chen.

**Compact design note:** Convert reduced the uncertainty of the public creep pool by guaranteeing one player-selected external capability family.

### Current design branch: fixed internal baseline unit

7.41 removed Summon Convert and all Convert Facets and replaced them with Zealot. Zealot does **not** guarantee a Centaur stun, Satyr dispel, Wolf aura, or other public neutral ability. Those capabilities must again be found in the world. Instead, Zealot guarantees a fixed internal army member that can be replaced after death and that owns army recall and sacrifice functions.

**Compact design note:** the redesign preserves environmental dependence for specialized capabilities while providing a reliable minimum army component.

### Design branch: sacrifice moved to an expendable owner

A previous Scepter branch gave Martyrdom to persuaded neutral creeps themselves, making valuable borrowed capability packages consumable as heals. Current Martyrdom instead belongs to the regenerating Zealot, preserving the idea of converting a unit body into immediate value without requiring Chen to destroy a difficult-to-reacquire neutral capability.

## Penitence

### Current factual baseline

| Property | Value |
| --- | --- |
| Cast | Unit target |
| Damage type | Pure |
| Cast range | 800 |
| Damage | 50 / 100 / 150 / 200 |
| Movement slow | 12% / 18% / 24% / 30% |
| Allied attack-speed bonus against target | 20 / 40 / 60 / 80 |
| Duration | 5 / 6 / 7 / 8 s |
| Cooldown | 20 / 17 / 14 / 11 s |
| Mana cost | 80 / 90 / 100 / 110 |
| Level 10 talent | +75 damage |
| Level 15 talent | +15 percentage points movement slow |

Allied units attacking the Penitence target gain the attack-speed bonus, so Chen, his army, and allied heroes can all use the same mark as a focus-fire signal.

### Historical design branch: universal damage vulnerability

Pre-7.20 Penitence applied the same **18% / 24% / 30% / 36%** movement slow and all-damage amplification for **5 / 6 / 7 / 8 seconds**. It made the marked target broadly more vulnerable to attacks and spells.

### Current design branch: army focus-fire accelerator

7.20 removed the universal damage amplification and instead made allied units that attack the target gain attack speed. The exact bonus has been tuned since, but the defining branch is stable: Penitence rewards many allied bodies for committing attacks to one target rather than simply amplifying every source of damage.

**Compact design note:** Holy Persuasion maximizes capability diversity; Penitence temporarily compresses that diversity into one shared offensive instruction.

### Historical branch: target-specific attack access

A later branch granted Chen, and eventually relevant controlled ranged units, **50 / 150 / 250 / 350** extra attack range specifically against the Penitence target. 7.40 removed this geometry-changing branch and added direct pure spell damage instead.

**Compact design note:** the older solution helped the army participate from safer positions; the current solution raises the spell's guaranteed value even when the army cannot immediately connect.

## Divine Favor

### Current factual baseline

| Property | Value |
| --- | --- |
| Passive aura radius | 1200 |
| Health regeneration bonus | 1.5 / 3 / 4.5 / 6 per second |
| Active cast range | 1200 |
| Active armor | 5 / 10 / 15 / 20 |
| Incoming heal/regen amplification | 5% / 10% / 15% / 20% |
| Active duration | 6 s |
| Cooldown | 20 / 18 / 16 / 14 s |
| Mana cost | 75 |
| Level 20 talent | +15 percentage points heal amplification |

The aura affects allied heroes and Chen-controlled units. When the active is cast on Chen, his controlled units receive the active protection buff.

### Historical design branch: Test of Faith [Removed]

A mature pre-7.20 Test of Faith combined two direct outcomes in one button:

- Enemy target: random **50-100 / 100-200 / 150-300 / 200-400** pure damage.
- Allied target: random **25-50 / 50-100 / 75-150 / 100-200** healing, with self-cast using the maximum heal.

Older Test of Faith variants also owned parts of Chen's ally/army teleport function at different times.

### Design branch: direct outcome -> sustain ownership

7.20 replaced Test of Faith with the first Divine Favor: a 12-second allied-unit buff providing **7 / 13 / 19 / 25 health regeneration**, **25% heal amplification**, and **10 / 20 / 40 / 80 attack damage**.

Later Divine Favor moved toward a persistent local regeneration aura plus a shorter active defensive window. The current version no longer directly damages enemies and is more specialized around maintaining the allied bodies that Chen's broader system depends on.

### Historical logistics branch

Army teleport functionality has moved among Test of Faith, Holy Persuasion, Divine Favor, and finally Zealot. In the 7.36-7.40 Divine Favor branch, self-casting could recall Chen-controlled units after a delay; 7.41 moved that logistics responsibility to Zealot while current Divine Favor retains its armor and health-restoration active.

**Compact design note:** separating sustain from army recall leaves Divine Favor with a clearer protection role and gives logistics a dedicated owner.

## Hand of God

### Current factual baseline

| Property | Value |
| --- | --- |
| Cast | No target |
| Radius | Global |
| Initial heal | 200 / 300 / 400 |
| Heal per second | 20 / 30 / 40 |
| Heal duration | 10 s |
| Cooldown | 150 / 130 / 110 s |
| Mana cost | 200 / 300 / 400 |
| Level 25 left talent | Fully heals Chen and his player-controlled units |
| Level 25 right talent | Applies a strong dispel |

Hand of God affects allied heroes globally and Chen's player-controlled units, including hidden or invulnerable valid allies. It therefore maintains a baseline recovery connection even when Chen's army and teammates are geographically dispersed.

### Historical design branch: Persuaded-unit Martyrdom Scepter [Removed]

The 7.32 Scepter gave persuaded units a shared-cooldown **Martyrdom** active. A creep sacrificed itself to perform a single-target Hand of God-like rescue on an ally with global cast range. Later tuning changed the heal model; a mature late branch used a heal based on **30% of the sacrificing unit's current health** before the design was removed in 7.39.

**Compact design note:** this distributed high-value rescue across the army, but it also made borrowed capability packages themselves expendable resources.

### Current Scepter branch: global rescue -> local protection zone

The current Scepter:

- Reduces Hand of God cooldown by **40 seconds**.
- Keeps the normal global initial heal.
- Allows Chen to continue channeling for up to **6 seconds** after that heal.
- Creates an **800-radius** Chen-centered protection area during the channel.
- Other allied units in that area gain debuff immunity and **60% magic resistance**.
- Units in the area receive **3x** the normal Hand of God heal-over-time rate while the channel is maintained.
- The channel protection does **not** protect Chen himself.

**Compact design note:** the upgrade changes the strongest part of Hand of God from a location-independent rescue into a Chen-centered, interruptible formation. The opponent can attack the protection system by reaching or disabling the channeling Chen rather than having to remove every protected unit individually.

## Current talents

| Level | Left | Right |
| --- | --- | --- |
| 10 | +25% Zealot health / base attack damage | +75 Penitence damage |
| 15 | +15% Penitence slow | +12% Holy Persuasion outgoing damage amplification |
| 20 | +1300 Holy Persuasion minimum health | +15% Divine Favor heal amplification |
| 25 | Hand of God fully heals Chen and his creeps | Hand of God applies a strong dispel |

## Kit relationships

- **World neutral pool -> Holy Persuasion -> dynamic capability set:** public units provide control, dispel, displacement, auras, summons, and other actions that are not written directly on Chen's own fixed spell list.
- **Finite army slots -> roster decisions:** acquiring a new capability package can require giving up an old one; the global dismissal mode makes replacement explicit.
- **Holy Persuasion diversity -> Penitence focus fire:** a single marked target gives otherwise heterogeneous units a shared offensive action.
- **Persuaded units -> Divine Favor:** local regeneration and targeted defense help preserve the bodies that carry Chen's borrowed capabilities.
- **Geographically distributed army -> Zealot recall / Hand of God:** recall solves army reassembly, while the ultimate preserves recovery reach without requiring immediate regrouping.
- **World-dependent special capabilities -> Zealot:** the fixed internal unit guarantees logistics and sacrifice value without guaranteeing the specialized neutral capabilities themselves.
- **Hand of God Scepter -> Chen-centered protection:** a global low-commitment rescue gains a stronger local component that requires positioning and channel commitment.

## Compact design conclusions

- A hero's capability set can extend into public world content instead of being fully encoded on the hero, but the complexity is transferred into knowledge, acquisition routes, roster management, unit survival, and control execution.
- Progression can increase **access** to new capability packages, not only increase numerical magnitude.
- Limited controlled-unit slots make external capability acquisition a trade-off rather than unrestricted collection.
- Fixed hero abilities can be designed to **organize and sustain** a changing external toolkit instead of competing with it for identity.
- A guaranteed internal summon can provide a reliability floor while preserving uncertainty in the more specialized external capability pool.
- Moving sacrifice value from difficult-to-reacquire neutral units to a regenerating dedicated unit preserves the mechanic while reducing conflict with roster composition.

These are Chen-supported observations, not yet cross-hero principles.

## Sources

Current and historical factual material was checked against:

- Liquipedia - Chen: https://liquipedia.net/dota2/Chen
- Liquipedia - Chen Changelogs: https://liquipedia.net/dota2/Chen/Changelogs
- Liquipedia - Chen Old Abilities: https://liquipedia.net/dota2/Chen/Old_Abilities
- Liquipedia - Hero Attributes Table: https://liquipedia.net/dota2/Table_of_hero_attributes
- Liquipedia - Version 7.20: https://liquipedia.net/dota2/7.20
- Liquipedia - Version 7.32: https://liquipedia.net/dota2/7.32
- Liquipedia - Version 7.36: https://liquipedia.net/dota2/7.36
- Liquipedia - Version 7.39: https://liquipedia.net/dota2/7.39
- Liquipedia - Version 7.41: https://liquipedia.net/dota2/7.41
- Liquipedia - Chen 7.41b changelog entry: https://liquipedia.net/dota2/Chen/Changelogs
- DOTABUFF - Chen Abilities: https://www.dotabuff.com/heroes/chen/abilities
- Dota 2 Pro Tracker - Version 7.41 changes: https://dota2protracker.com/patches/7.41
- Liquipedia - Centaur Conqueror: https://liquipedia.net/dota2/Centaur_Conqueror
- Liquipedia - Satyr Banisher: https://liquipedia.net/dota2/Satyr_Banisher
- Liquipedia - Wildwing Ripper: https://liquipedia.net/dota2/Wildwing_Ripper
- Liquipedia - Alpha Wolf: https://liquipedia.net/dota2/Alpha_Wolf
- Liquipedia - Dark Troll Summoner: https://liquipedia.net/dota2/Dark_Troll_Summoner

Current-source inconsistencies were resolved before persistence. In particular, current detailed data confirms that Divine Favor still owns its armor/heal-amplification active after 7.41, while the army-recall component moved to Zealot. Current detailed Zealot data and current patch mirrors use **current health** for Martyrdom even though some 7.41 summary text says max health. Penitence uses the 7.41a **50/100/150/200 pure-damage** values.

Where an ability or neutral-unit mechanic had many balance-only parameter changes, this document records a representative or mature parameter set rather than reproducing the full patch chronology.
