# Doom - Hero Design Case

**Status:** First durable pass

**Current factual reference state:** Dota 2 7.41e. The latest direct changes are 7.41e, which reduced Doom's base attack range from 200 to 175 and rescaled Infernal Blade's burn to 18/34/50/66 base damage per second plus 0.5%/1.75%/3%/4.25% max-health damage per second; 7.41d increased Intelligence gain to 2.1 and reduced the Shard Devoured Ability AoE factor to 1.15.

## Design identity

Doom combines environmental capability acquisition with enemy capability denial. Devour turns neutral creeps into configurable ability modules while retaining a stable economic payoff; Doom works in the opposite direction by disabling major parts of an enemy hero's action set for a long window. Scorched Earth, Infernal Blade, and the current Lvl ? Pain Innate supply the close-contact damage structure around those two systems.

## Current combat chassis

| Property | Current value |
| --- | ---: |
| Primary attribute | Strength |
| Strength | 24 + 3.6 |
| Agility | 15 + 1.5 |
| Intelligence | 15 + 2.1 |
| Starting health | 648 |
| Starting health regeneration | about 3.06/s |
| Starting mana | 255 |
| Starting mana regeneration | about 0.75/s |
| Starting armor | about 3.5 |
| Starting attack damage | 56-66 |
| Attack type / range | Melee / 175 |
| Base attack speed | 100 |
| Base attack time | 1.9 s |
| Attack point | 0.5 s |
| Movement speed | 290 |
| Turn rate | 0.6 |
| Vision | 1800 / 800 |

The 175 attack range is the 7.41e value. Doom's 1.9 base attack time and 290 movement speed leave the base chassis relatively slow, making movement and control from Scorched Earth, items, and Devoured Abilities important for repeated close contact.

**Current-source note:** Liquipedia's current attribute display gives about 3.5 starting armor, consistent with the 7.41a base-armor reduction to 1 plus 15 starting Agility. Current Dotabuff displays about 3.1. This case uses about 3.5 and preserves the display discrepancy for a later roster-wide refresh.

## Lvl ? Pain - Innate

### Current factual baseline

Lvl ? Pain is a breakable passive triggered by Doom's attacks against enemy heroes.

| Property | Current value |
| --- | --- |
| Curse duration | 2.5 s |
| Maximum curse instances per unit | 1 |
| Damage-accounting source | Damage sourced to Doom |
| Explosion damage factor | 10% of accumulated damage |
| Base explosion radius | 66 |
| Special hero-level condition | Cursed hero level is a multiple of 6 |
| Conditional damage factor | x1.66 |
| Conditional radius factor | x1.66 |
| Conditional radius | 109.56 |
| Damage type | Magical spell damage |

The attack that applies the curse is included in the accumulated damage. During the fixed 2.5-second window, damage instances sourced to Doom are recorded; HP-removal and no-reflection-flag damage are excluded. When the curse ends, the target and nearby enemies take magical spell damage equal to 10% of the recorded amount.

Subsequent attacks do **not** reapply or refresh the existing curse, so the 2.5-second accounting window is fixed once started. If the cursed enemy hero's level is a multiple of 6, both the final damage and radius are multiplied by 1.66.

**Compact design note:** the current Innate converts a fixed short window of Doom-sourced damage into delayed extra damage. It rewards damage density inside the window rather than indefinite duration extension.

### Historical branch: level advantage -> damage-accounting window

**7.36:** Lvl ? Pain was introduced as an Innate that granted bonus attack damage against units whose level was lower than Doom's. The initial bonus was 10%; later patches increased and adjusted the model.

**7.38:** the conditional attack bonus reached 25% against lower-level heroes.

**7.41-7.41a:** the level-comparison attack amplifier was replaced by the current 2.5-second damage-counter model. The initial conversion factor was 15%; 7.41a reduced it to the current 10%. The historical LVL? theme survives through the target-level multiple-of-6 condition rather than a direct Doom-level advantage check.

## Devour

### Current factual baseline

| Property | Current value |
| --- | --- |
| Targeting | Enemy or neutral creep |
| Cast range | 300 |
| Maximum creep level | 4 / 5 / 6 / 6 |
| Bonus gold | 35 / 70 / 105 / 140 |
| Digest duration | 70 s |
| Cooldown | 66 s |
| Mana cost | 40 / 50 / 60 / 70 |
| Base Ancient targeting | No |
| Acquired ability slots | 2 dedicated slots |

Devour instant-kills the creep, grants its normal bounty and experience like a last hit, and starts a digest buff. The flat Devour bonus gold is granted when the digest buff expires.

By default, Doom acquires the neutral creep's supported special abilities into the dedicated **Devoured Ability 1** and **Devoured Ability 2** slots. If the creep has no acquirable abilities, Doom keeps his current acquired abilities.

With **Alt-Cast enabled**, Doom consumes the creep but does not acquire its abilities. This separates the economic use of Devour from changing the current ability configuration.

Acquired neutral abilities automatically level up at the in-game times when their neutral-creep versions scale, so keeping a chosen capability does not freeze it at the value it had when first acquired.

**Current-source note:** current Liquipedia records the digest duration as 70 seconds while the cooldown is 66 seconds after the 7.41 cooldown reduction. Some player-facing tooltip text still says the duration equals the cooldown. This case preserves the mechanically documented 70-second digest / 66-second cooldown split.

### Aghanim's Shard - acquisition-system upgrade

Current Shard changes Devour and both Devoured Ability slots:

- Devour becomes a **2-charge** ability.
- Each charge has a **66-second restore time**.
- Doom can Devour **Ancient creeps**.
- Devoured Ability 1 and Devoured Ability 2 receive a **1.15 AoE factor**.
- Both acquired slots receive **+40% outgoing spell damage amplification**.

The AoE factor was 1.2 when this Shard model was introduced in 7.41 and was reduced to the current 1.15 in 7.41d.

**Compact design note:** the Shard independently increases acquisition timing flexibility, the available creep pool, and the magnitude of acquired spells rather than simply increasing Devour's gold output.

### Historical Devour branches

**Early Devour:** older versions primarily converted creeps into sustain or economy. 5.35 added health regeneration during digestion; 5.53 removed that regeneration and instead granted bonus gold after digestion.

**6.66 capability acquisition:** Devour began inheriting the abilities of a consumed neutral creep until they were replaced by abilities from a later Devour. This is the major transition from a primarily economic creep-consumption spell to an environmental ability-acquisition system.

**7.20 economy/configuration separation:** Devour gained a toggle/autocast mode that allowed Doom to consume a creep without stealing its abilities. The same patch moved digestion to a constant 80-second model and removed the older restriction that prevented another Devour while digestion was still active.

**7.34 Alt-Cast UI:** Devour moved to the alternative-cast interface, allowing the player to access the opposite consume/acquire behavior with the standard Alt-Cast/Ctrl interaction rather than treating ability preservation as a separate long-term toggle state.

**7.35 persistent scaling:** acquired neutral abilities began leveling automatically according to game time.

**7.36-7.40 Gluttony:** the Gluttony Facet replaced Devour's single cooldown with two charges and upgraded acquired neutral abilities by one level. Charge restore time was initially 90 seconds and was later reduced.

**7.41 current structure:** Gluttony was removed; Devour gained the current two dedicated Devoured Ability slots by default, the consume-without-acquiring Alt-Cast was clarified, and the charge/Ancient/acquired-spell-amplification progression moved into Aghanim's Shard.

## Scorched Earth

### Current factual baseline

| Property | Current value |
| --- | --- |
| Damage type | Magical |
| Radius | 666 |
| Damage per second | 20 / 30 / 40 / 50 |
| Full-duration base damage | 200 / 360 / 560 / 800 |
| Movement speed bonus | 7% / 8% / 9% / 10% |
| Self health regeneration | 6.66/s |
| Duration | 10 / 12 / 14 / 16 s |
| Cooldown | 41 / 39 / 37 / 35 s |
| Mana cost | 60 / 70 / 80 / 90 |

Scorched Earth remains centered on Doom and follows his position. Its current purpose combines local magical damage, movement-speed support for maintaining contact, and a fixed self-regeneration bonus.

### Level-25 talent: Permanent Scorched Earth

The current level-25 talent converts Scorched Earth into a toggle:

- toggle cooldown: **2.5 seconds**;
- mana cost while toggled: **0**;
- the Scorched Earth aura can remain active until toggled off.

This changes Scorched Earth from a temporary combat window into a persistent body-centered state.

### Historical branch

Scorched Earth has repeatedly moved between regeneration/healing and damage/movement models. The current 7.41 branch restored explicit self health regeneration after earlier versions had removed healing, while keeping the area centered on Doom. 7.41 increased the radius from 600 to 666; 7.41c standardized the self-regeneration value to the current 6.66 at every skill level.

## Infernal Blade

### Current factual baseline

| Property | Current value |
| --- | --- |
| Targeting | Attack modifier / enemy unit |
| Damage type | Magical |
| Base burn damage per second | 18 / 34 / 50 / 66 |
| Max-health damage per second | 0.5% / 1.75% / 3% / 4.25% |
| Burn duration | 4 s |
| Stun duration | 0.66 s |
| Cooldown | 13 / 10 / 7 / 4 s |
| Mana cost | 35 |
| Debuff Immunity | Does not pierce |
| Burn dispel | Dispellable |

At level 4, one full burn contributes **264 fixed magical damage plus 17% of the target's maximum health** before reductions and other modifiers. The current level-15 talent adds 1.5 percentage points of max-health damage per second, raising the level-4 percentage component from 4.25% to **5.75% per second**, or **23% max health** across the four-second burn.

7.41e rescaled the ability from 15/30/45/60 + 1%/2%/3%/4% max-health DPS to the current 18/34/50/66 + 0.5%/1.75%/3%/4.25% model.

**Compact design note:** Infernal Blade supplies target-relative damage against high-health units, while its four-second level-4 cooldown allows continuous reapplication only if Doom can repeatedly maintain attack access.

## Doom - Ultimate

### Current factual baseline

| Property | Current value |
| --- | --- |
| Targeting | Enemy unit |
| Cast range | 400 |
| Damage type | Pure |
| Initial effect | Basic dispel |
| Duration | 12 / 14 / 16 s |
| Damage per second | 22 / 44 / 66 |
| Full-duration damage | 286 / 660 / 1122 |
| Cooldown | 140 / 130 / 120 s |
| Mana cost | 150 / 200 / 250 |
| Debuff Immunity | Pierces |
| Dispel | Cannot be dispelled |

Doom applies a basic dispel, Silences the target, prevents healing, and deals pure damage over time. Damage is applied immediately and then in one-second intervals, so full-duration damage contains one more damage instance than a simple `DPS x duration` calculation: the current totals are 286/660/1122.

The base spell does not remove all player action: the target can still move and attack, and item use remains available unless Mute is added through the level-25 talent.

### Current Aghanim's Scepter

Current Scepter changes both control depth and spatial coverage:

- all Doom-affected enemies also receive **Break**;
- other enemies allied to the directly Doomed target suffer Doom while they remain within **350 radius** of that target;
- Doom can self-cast, making Doom himself the center of the **350-radius** Doom effect around nearby enemies.

The directly targeted unit therefore acts as a moving debuff carrier in enemy-target mode, while Doom himself can become the moving carrier in self-cast mode.

### Level-25 talent: Mute

The current level-25 talent makes Doom apply **Mute**, disabling item actives on affected targets. Together with the current base spell and Scepter, the progression can deny separate capability layers:

- base Doom: spell casting and healing;
- Scepter: passive abilities through Break, plus 350-radius propagation/self-carrier targeting;
- level 25: item actives through Mute.

### Major historical Doom branches

**Early Scepter magnitude model:** historical Aghanim's Scepter versions primarily changed Doom's duration, damage per second, and cooldown. For example, 6.39 increased damage, increased duration to 14/16/18, and reduced cooldown relative to the base spell.

**6.81b proximity/time branch:** Scepter could pause Doom's duration while the target remained within 550 range of Doom, making proximity control the effective length of the debuff.

**6.82 Break separation:** base Doom stopped disabling passives, while Aghanim's Scepter explicitly added Break. This separated long-duration spell denial from passive denial as an upgrade layer.

**7.32 spatial Scepter:** Scepter was reworked so enemies within 325 radius of the Doomed target also suffered Doom, and Doom could self-cast to affect nearby enemies. 7.39 later increased this radius to the current 350.

**7.34 healing-denial branch:** base Doom stopped applying Mute and instead gained the modern inability-to-heal/health-freeze behavior. Cooldown became 140/130/120. Mute later returned as a level-25 talent rather than a base property.

**Impending Doom (7.37-7.40):** this Facet increased Doom duration by 0.66 seconds every 6.66 minutes while reducing the spell's DPS relative to the non-Facet branch. It moved late-game growth into duration rather than additional denied systems. The component was removed in 7.41.

**7.41 current upgrade allocation:** Impending Doom was removed; base DPS was adjusted; Scepter stopped adding 15 DPS and instead added Break to the existing AoE/self-cast structure; the previous level-25 Break talent was replaced by Permanent Scorched Earth, leaving Mute as the other current level-25 branch.

## Talents

| Level | Choice A | Choice B |
| --- | --- | --- |
| 10 | +0.2 s Infernal Blade stun | +10% Magic Resistance |
| 15 | +1.5% Infernal Blade max-health damage per second | +7% Scorched Earth movement speed |
| 20 | +66 attack damage | -10 s Doom cooldown |
| 25 | Permanent Scorched Earth | Doom applies Mute |

Useful direct comparisons:

- Level-15 Infernal Blade raises the current level-4 max-health component from 4.25% to 5.75% per second.
- Level-15 Scorched Earth raises its level-4 movement bonus from 10% to 17%.
- Level-20 Doom cooldown changes 140/130/120 to 130/120/110 seconds.
- Level-25 separates a persistent self-centered combat state from deeper enemy capability denial.

## Whole-kit relationships

- **Devour -> configurable capability set:** neutral creeps supply additional active/passive tools while Devour continues to provide a stable economy baseline.
- **Scorched Earth -> contact maintenance:** movement speed, regeneration, and a body-centered damage radius help Doom remain in close range.
- **Attack -> Lvl ? Pain window:** the first attack opens a fixed 2.5-second account for Doom-sourced damage.
- **Infernal Blade -> target-relative pressure:** max-health scaling remains relevant against large health pools if Doom can keep attacking.
- **Doom -> capability denial:** long-duration Silence and healing prevention can be expanded by Scepter Break/AoE coverage and level-25 Mute.

## Costs and counterplay

- Devour's strongest configurations depend on neutral-creep availability, map position, creep-level access, and Devour timing; Shard is required for Ancient targets.
- Alt-Cast lets Doom preserve a strong acquired configuration while continuing to consume creeps for economy, so counterplay to Devour is mainly about map/resource access rather than forcing every economic Devour to replace abilities.
- Lvl ? Pain uses a fixed, non-refreshing 2.5-second window. Disengaging or preventing Doom from continuing to deal damage during that window reduces the delayed burst.
- Scorched Earth is body-centered and does not damage through Debuff Immunity; creating distance attacks both its damage and Doom's ability to keep using Infernal Blade.
- Infernal Blade does not pierce Debuff Immunity and its burn is dispellable. The level-4 four-second cooldown only becomes continuous pressure when Doom maintains repeated attack access.
- Doom has 400 cast range, a very long 140/130/120 cooldown, and can be blocked/redirected by relevant spell-targeting defenses before it lands. Once successfully applied, the debuff itself cannot be dispelled.
- Base Doom does not Mute, so item actives remain a response option before the level-25 Mute talent.
- Scepter's secondary Doom coverage depends on 350-radius proximity to the directly Doomed target, or proximity to Doom during self-cast; spreading away from the moving carrier reduces secondary-target exposure.

## Compact case close

**Design identity:** Doom manipulates capability in opposite directions. Devour adds environment-derived modules to Doom's own action set, while Doom removes increasingly important layers of an enemy hero's action set for a long window.

**Case observations:**

- Ability-acquisition systems can separate stable resource value from configuration value so routine economy use does not forcibly destroy a chosen build.
- Acquisition frequency, acquisition pool, acquired-ability level/scaling, AoE, and spell magnitude are distinct progression levers.
- A disable can scale by denying additional systems or additional targets rather than only by increasing duration.
- Fixed damage-accounting windows such as Lvl ? Pain reward damage density and can connect otherwise separate attacks and spells without requiring another manually managed resource.

These remain case-level observations until wider roster comparison.

## Sources

Current baseline and upgrades:

- https://liquipedia.net/dota2/Doom
- https://liquipedia.net/dota2/Table_of_hero_attributes
- https://www.dotabuff.com/heroes/doom/abilities
- https://dotacoach.gg/en/heroes/doom
- https://liquipedia.net/dota2/Version_7.41e
- https://liquipedia.net/dota2/Version_7.41d
- https://liquipedia.net/dota2/7.41

Historical branches:

- https://liquipedia.net/dota2/Doom/Changelogs
- https://liquipedia.net/dota2/Doom/Old_Abilities
- https://www.dota2.com/720
- https://liquipedia.net/dota2/Version_7.34
- https://liquipedia.net/dota2/Version_7.35
- https://liquipedia.net/dota2/Version_7.36
- https://liquipedia.net/dota2/Version_7.32

### Source calibration notes

- Current attack range is **175** from 7.41e even though some cached/current hero-detail panes still display 200.
- Current starting armor is recorded as about **3.5** from the current base-armor/Agility state; Dotabuff currently displays about 3.1.
- Current Devour digest duration is recorded as **70 seconds** and cooldown as **66 seconds** from Liquipedia's mechanical details plus the documented 7.41 cooldown reduction; some tooltip text still says duration equals cooldown.
- Doom full-duration damage uses the immediate first tick plus one-second intervals, giving **286/660/1122**, not simple DPS multiplied by nominal duration.
