# Dota 2 Observed Structure Catalog

**Status:** `[OPEN]`

This document is the observation-first evidence catalog for the active gameplay-data-model research phase.

Its purpose is to record structures that can be confirmed from current Dota 2 gameplay data and documentation **before** deciding how those structures should be abstracted into a reusable model.

The catalog is not a Dota 2 implementation specification and is not a claim about Valve's internal code or data architecture.

## Research rhythm

Use this sequence for the current phase:

```text
Observe
  -> Record
  -> Normalize
  -> Compare
  -> Abstract
  -> Pressure-test
```

The first observation batch - Hero, ordinary unit / creep, Building, Ability, Item - is now recorded at first-pass granularity and has passed through the first Normalize / Compare checkpoint. The second observation batch should pressure-test the resulting working model rather than silently redesign it after every isolated case.

## Observation rules

1. Record externally observable or documentable structure before interpretation.
2. Distinguish verified Dota 2 facts from recording conventions and uncertainty.
3. Include a version/date anchor for changeable Dota 2 facts.
4. Preserve distinctions exposed by sources even when they may later be normalized, such as `base` versus `starting` values.
5. Use group headings only for readability. A group such as `attack` or `movement` does not establish a final schema primitive.
6. Record visible links between subjects without prematurely deciding whether the final model should represent them as ownership, containment, references, relations, subobjects, components, or another structure.
7. Mark unclear cases as uncertain rather than resolving them through abstraction.
8. Treat named Dota categories as evidence domains, not as proof that each category must become a distinct reusable-model type.

## Standard observation template

```text
Subject:
Version / observed date:
Sources:

Definition-facing structure:
- field / nested group
- value shape if relevant
- multiplicity if relevant

Runtime-visible structure:
- state / value / collection
- visible change behavior if relevant

Relationships and linked structures:
- subject <-> other subject
- multiplicity / role if directly observable

Variations / exceptions:
- notable structural variants

Uncertain observations:
- facts or boundaries that need stronger evidence
```

## Observation order

### First batch - completed at first-pass granularity

1. Hero
2. Ordinary unit / creep
3. Building
4. Ability
5. Item
6. First abstraction checkpoint

### Second batch - next

1. Modifier / buff / debuff
2. Projectile and other short-lived spatial objects
3. World objects such as trees, wards, runes, and similar discrete objects
4. World state such as terrain, vision, time, and spatial structures
5. Player, Team, and Match-level structures
6. Second abstraction checkpoint

---

# Subject: Hero

## Version anchor

- Observed date: 2026-09-02.
- Current version used for this observation pass: Dota 2 7.41e, released 2026-07-30.
- Structural historical note: Facets were removed in 7.41, released 2026-03-24, so Facet data is not treated as part of the current Hero structure.

## Sources checked

- Liquipedia, `Version 7.41e`: https://liquipedia.net/dota2/7.41e
- Liquipedia, `Version 7.41`: https://liquipedia.net/dota2/7.41
- Liquipedia, `Hero Attributes Table`: https://liquipedia.net/dota2/Table_of_hero_attributes
- Liquipedia, `Template:Infobox hero`: https://liquipedia.net/dota2/Template:Infobox_hero
- Liquipedia, `Attributes`: https://liquipedia.net/dota2/Attributes
- Liquipedia, `Experience`: https://liquipedia.net/dota2/Experience
- Liquipedia, `Head-up Display`: https://liquipedia.net/dota2/Head-up_Display
- Liquipedia, `Abilities`: https://liquipedia.net/dota2/Abilities
- Liquipedia, `Controls`: https://liquipedia.net/dota2/Controls

These sources are used as observable documentation, not as evidence of Valve's internal storage model.

## Definition-facing structure

The following groups are recording conveniences only. They are not final schema categories.

### Identity / classification

Observed entries include:

- hero identity / name
- primary attribute classification
- attack type classification

### Attributes

Observed entries include:

```text
strength
- base strength
- strength growth per level

agility
- base agility
- agility growth per level

intelligence
- base intelligence
- intelligence growth per level
```

Sources also expose totals such as total starting attributes, total growth, and level-based totals. These are visible results but are not assumed to be independently stored values.

### Movement / facing

Observed entries include:

- base movement speed
- base movement speed at night where applicable in source structure
- turn rate

### Attack

Observed entries include:

- base minimum attack damage
- base maximum attack damage
- starting minimum attack damage
- starting maximum attack damage
- base attack speed / attack speed value
- base attack time
- attack point
- attack backswing
- attack range
- projectile speed
- attack acquisition range
- attack type

The source material exposes both `base` and `starting` attack damage concepts. They remain separate observations at this stage.

### Defense

Observed entries include:

- base armor
- starting armor
- base magic resistance

The source material exposes both `base` and `starting` armor concepts. They remain separate observations at this stage.

### Vision

Observed entries include:

- daytime vision range
- nighttime vision range

### Body / collision

Observed entries include:

- collision size

### Health / mana presentation

Observed entries include:

- starting health
- base health regeneration
- starting mana
- base mana regeneration

`Starting` values are recorded as exposed values. Their dependency on attributes or other rules is deliberately not normalized here.

### Linked gameplay content

Current hero structure visibly links a hero to additional gameplay content including:

- innate ability content
- other hero abilities / ability slots
- talent choices
- Aghanim's Scepter upgrade references where applicable
- Aghanim's Shard upgrade references where applicable

## Runtime-visible structure

Observed mutable/current structures include:

### Resources and current combat values

- current health and maximum health
- current mana and maximum mana
- current health regeneration and mana regeneration
- current attribute values
- current armor, movement, attack, resistance, and other exposed combat results that can differ from definition-facing values
- current barrier / shield capacity where a barrier-producing effect is present

The observation is that current values exist and change during a match. This catalog does not decide which are stored fields versus derived or aggregate results.

### Growth and progression

- current hero level
- current experience progress
- unspent ability points
- learned/current ability levels
- selected talents

Hero level and experience are distinct from the fixed `Level` values exposed by some creep definitions.

### Spatial and lifecycle state

- current world position
- current facing direction used by gameplay movement/attack/cast behavior
- alive / dead state
- respawn state and remaining respawn time when dead

### Ability-linked runtime collections/state

For abilities associated with the hero, observable runtime state can include:

- learned level
- cooldown remaining
- charges and charge-restore progress where applicable
- toggle state
- autocast state
- current cast/channel state where applicable

These facts are recorded without deciding whether the ability runtime state is part of the Hero, a separate runtime instance, or another structure.

### Inventory-linked runtime collections/state

Observable Hero-linked item context includes:

- six main inventory slots
- three backpack slots
- dedicated Town Portal Scroll slot
- dedicated neutral-item slot
- current item occupancy of those slots

The stash is deliberately left as a boundary case for later Player / Team / Match observation because its relationship to the hero and player context needs comparison.

### Modifiers and status

Observable current status includes:

- active visible buffs and debuffs
- disable/status categories and remaining durations where exposed
- barriers/shields produced by active effects

Visible HUD modifiers are not assumed to be the complete modifier set because hidden modifiers exist. Presence of a modifier is also not equivalent to its effects being currently effective; debuff-immunity behavior provides a counterexample.

### Orders / targets

Observable current control state can include:

- current move / attack / follow / ability / item order
- point or unit targets depending on the order
- queued orders

The boundary between Hero state and Player/controller state is intentionally unresolved.

## Relationships and linked structures

Observed Hero links include:

- Hero <-> Player controller
- Hero <-> Team
- Hero <-> Ability / Talent / upgrade content
- Hero <-> Item through inventory/slot context
- Hero <-> modifier/buff/debuff sources and targets
- Hero <-> generated or controlled units in summon/illusion cases

Summons and illusions warn against collapsing `created by`, `controlled by`, `copied from`, and `owned by` into one relationship. Illusions can copy a source Hero's current state at creation and then diverge rather than remaining synchronized.

## Variations / exceptions

- Projectile speed is meaningful for ranged attack structures and may not apply in the same way to melee attacks.
- Sources can expose separate day/night movement or vision values.
- Base and starting values are not always the same visible number.
- Current Hero values can be influenced by abilities, items, modifiers, talents, world rules, and other external state.
- 7.41 removed the Facet layer from current hero structure.

## Uncertain observations

- Which current Hero values are stored versus derived or aggregate?
- Which Hero entries will normalize into a general Unit structure shared with creeps or buildings?
- Which ability/talent/upgrade structures need runtime identity distinct from the Hero?
- Which inventory/order/buyback/stash facts ultimately belong to Hero, Player, Team, or relationships among them?
- How should player-visible information be separated from actual runtime truth?

## Hero observation status

- [x] Definition-facing structure recorded at first-pass granularity
- [x] Runtime-visible structure recorded at first-pass granularity
- [x] Relationships and linked structures recorded at first-pass granularity

---

# Subject: Ordinary unit / creep

## Scope and version anchor

- Observed date: 2026-09-02.
- Current version: Dota 2 7.41e.
- Baseline scope: lane creeps and regular neutral camp creeps.
- Boundary variants included because they materially pressure-test the baseline: controlled creeps, summons, creep-heroes, Roshan, and Tormentor.

`Ordinary unit / creep` is a research subject label, not a proposed reusable-model type. Roshan and Tormentor are recorded here as special neutral-creep boundary variants rather than being treated as ordinary baseline creeps.

## Sources checked

- Liquipedia, `Unit Types`: https://liquipedia.net/dota2/Unit_Types
- Liquipedia, `Lane Creeps`: https://liquipedia.net/dota2/Lane_Creeps
- Liquipedia, `Neutral Creeps`: https://liquipedia.net/dota2/Neutral_Creeps
- Liquipedia, `Summons`: https://liquipedia.net/dota2/Summons
- Liquipedia, `Creep-heroes`: https://liquipedia.net/dota2/Creep-heroes
- Liquipedia, `Roshan`: https://liquipedia.net/dota2/Roshan
- Liquipedia, `Tormentor`: https://liquipedia.net/dota2/Tormentor
- Liquipedia, `Version 7.41`: https://liquipedia.net/dota2/7.41
- Liquipedia, `Version 7.41e`: https://liquipedia.net/dota2/7.41e

## Definition-facing structure

Across lane-creep and regular-neutral-creep documentation, repeatedly exposed entries include:

### Identity / classification

- unit identity / creep subtype
- faction-aligned or neutral classification/context
- attack classification
- exposed unit `Level` value where documented

A creep's exposed `Level` must not be normalized with Hero runtime level merely because the label matches. Ordinary creeps do not follow the Hero XP-driven personal leveling lifecycle.

### Resources / defense / body

- maximum/base health
- health regeneration
- mana and mana regeneration where applicable
- armor
- magic resistance
- status resistance where applicable
- collision size / bound radius

Mana is structurally optional across creep variants.

### Attack / movement / vision

- attack damage range
- attack range
- acquisition range
- attack speed / base attack time
- attack point / backswing
- projectile speed where relevant
- movement speed
- turn rate
- daytime / nighttime vision

### Rewards

- gold bounty
- experience bounty

### Linked abilities

Creeps can link to gameplay abilities. The structure ranges from simple passive/classification-like abilities on lane creeps to active, mana-costing, cooldown-bearing abilities on neutral creeps.

## Time- and spawn-context-dependent definition-facing values

Creep values are not adequately described as one immutable number set independent of match context.

Observed patterns include:

- lane-creep stats and bounties change across match-time upgrade intervals
- future lane-creep variants can depend on Barracks state
- neutral creeps receive match-time stat upgrades
- some neutral-creep ability levels depend on the time band in which the creep spawned

This catalog records these dependencies without deciding whether they are multiple Definitions, parameterized definitions, spawn-time calculations, world-state queries, or another structure.

## Runtime-visible structure

### Current values

Observed mutable state includes:

- current health
- current mana where the creep uses mana
- current combat results affected by modifiers and world rules
- ability cooldown / mana usage / other ability state for creeps with active abilities

### Spatial / target / behavior state

Creep instances visibly have:

- current world position
- current facing
- current movement/chase/return behavior
- current attack target
- current aggro state

Lane creeps autonomously select and change targets while moving down lanes. Neutral creeps have camp/home context, aggro/return behavior, and can abandon neutral AI behavior after player control is acquired.

### Distinct time-update behaviors

Observed creep variants expose different relationships between global time and already-existing instances:

- lane-creep periodic upgrades affect later spawns rather than retroactively updating older lane creeps already alive on the map
- neutral-creep periodic stat upgrades can update already-existing neutral creeps, including controlled ones
- neutral-creep ability levels can remain tied to spawn-time bands rather than increasing when later time thresholds are crossed

These are deliberately recorded as separate behaviors. No single `spawn snapshot` or `live query` rule is inferred for all creep properties.

## Relationships and linked structures

Observed links include:

### Lane-creep context

- creep <-> faction/team side
- creep <-> lane
- creep <-> spawn wave
- future creep spawn variant <-> Barracks state

### Neutral-creep context

- creep <-> neutral camp
- creep <-> camp type / spawn composition
- creep <-> camp spatial/home context

### Controller / source / historical-credit context

- a neutral creep can acquire a player controller
- controller changes do not erase every other state or historical source attached to the creep
- successful neutral-camp stacking can create later creeps carrying stack-credit context associated with the stacking player
- summons distinguish creation/source context from current player control

These observations argue for preserving `created by`, `controlled by`, `spawned in`, `belongs to wave/camp`, and historical-credit facts as distinct until normalization proves otherwise.

## Boundary variant: Roshan

Roshan remains an Ancient Neutral Creep but introduces structures not present in the ordinary creep baseline.

### Definition/runtime observations

- ordinary unit-like resources, defenses, attack, movement, vision, bounty, and linked abilities remain present
- combat values scale with match time
- time-based growth continues to matter across Roshan's death/respawn cycle
- Roshan has alive/dead/respawn-pending lifecycle rather than permanent removal on death
- Roshan changes pit/location context with natural day/night cycles
- current pit, movement-between-pits, target, aggro, and ability state are gameplay-relevant runtime facts

### Hidden-information observation

Roshan's actual respawn timing and what a player/team can know about that timing are not the same thing. Spectator information and special information-granting mechanics provide further evidence that:

```text
actual runtime truth
!= viewer-specific knowledge
!= UI presentation
```

This is recorded as a future Player/Team/vision-model obligation, not as a new primitive at this checkpoint.

### Historical-state observation

Future Roshan behavior and rewards can depend on match history, including prior kills / kill ordinal and the team responsible for a previous kill. The observation is that compressed historical results can remain gameplay-relevant current state.

### Spatial-region observation

Roshan pits expose rules that depend on region membership and vision boundaries rather than only Euclidean distance from a point. This is evidence that future spatial modeling must consider regions/boundaries in addition to generic position queries.

## Boundary variant: Tormentor

Tormentor is also an Ancient Neutral Creep but strongly challenges ordinary unit assumptions.

### Barrier-dominant durability

Observable durability distinguishes:

- current health
- current barrier
- barrier capacity
- barrier regeneration

The barrier values grow with match time. This reinforces the catalog-wide distinction between a current quantity and its maximum/capacity/reference value.

### Special movement/state transition

Tormentor normally lacks ordinary mobile-unit behavior, yet its world position can change through special day/night world transitions. Current 7.41e also documents projectile-disjoint behavior during this transition.

Therefore `has a position` and `has ordinary movement capability` are separate observations.

### Triggered ability state

Tormentor-linked passive behavior can move through inactive / triggered / active-with-timer / refreshed states. Linked passive content therefore can have its own runtime phase/state rather than being only a static possession flag.

### Owner-death / lingering-effect boundary

Tormentor death can leave a temporary area regeneration effect after the Tormentor itself is no longer alive. This is important boundary evidence against assuming that every linked effect shares its source/owner lifecycle.

### Reward-selection boundary

Tormentor reward resolution can depend on slaying team context and player/hero state rather than simply creating a generic ground drop. The detailed rule belongs to later Interaction / Rule / Player-Team observation, but the cross-subject dependency is recorded here.

## Variations / exceptions

- mana is optional across creep definitions
- ranged/melee/siege and neutral subtypes expose different attack and projectile structures
- active abilities are optional
- creep context can be faction-aligned, neutral, or player-controlled
- summons add explicit creation-source/player-control context
- creep-heroes are creeps but are treated as Hero-like for selected rules, making them a future pressure-test case
- some effects can change how a creep is classified or treated by rules after creation
- Roshan and Tormentor expose unique lifecycle, time, region, barrier, reward, and historical-state behavior without ceasing to be neutral-creep-category subjects in Dota documentation

## Uncertain observations

- Which unit fields normalize cleanly across Hero / creep / Building?
- Which creep `Level`-like values are definition labels versus runtime/evaluated properties?
- How should spawn-time values and later world-time updates coexist in one reusable model?
- Which camp/wave/lane contexts need independent runtime identity versus relational/state representation?
- How should controller changes, historical stack credit, and source relations be represented?
- Is a respawned Roshan the same runtime identity, a successor instance, or another lifecycle representation? Current observation does not decide this.

## Ordinary unit / creep observation status

- [x] Lane-creep baseline recorded
- [x] Regular neutral-creep baseline recorded
- [x] Runtime behavior and time-update variants recorded
- [x] Controller / camp / wave / lane relationships recorded
- [x] Roshan and Tormentor boundary variants recorded
- [x] Summon / creep-hero boundary notes recorded

---

# Subject: Building

## Version anchor

- Observed date: 2026-09-02.
- Current version: Dota 2 7.41e.

## Sources checked

- Liquipedia, `Buildings`: https://liquipedia.net/dota2/Buildings
- Liquipedia, `Towers`: https://liquipedia.net/dota2/Towers
- Liquipedia, `Buildings Changelogs`: https://liquipedia.net/dota2/Buildings/Changelogs
- Liquipedia, `Version 7.41`: https://liquipedia.net/dota2/7.41
- Liquipedia, `Version 7.41e`: https://liquipedia.net/dota2/7.41e

## Definition-facing structure

Repeated building entries include:

- identity / building subtype
- team/faction context
- maximum/base health
- health regeneration
- armor
- magic resistance
- vision
- collision / body dimensions
- gold or objective rewards where applicable
- linked abilities / protections

For attacking Towers, additional entries include:

- attack damage
- attack range
- acquisition range
- attack speed / base attack time
- attack point / backswing
- projectile speed

Buildings do not need ordinary unit movement parameters to have a world position and interaction ranges.

## Runtime-visible structure

Observable current state includes:

- current health
- current armor/resistance/protection results
- current world position, normally fixed
- alive / destroyed state
- invulnerable / vulnerable state where progression rules apply
- current Tower attack target where the building attacks
- active shared or temporary protection states such as Glyph / Backdoor-related effects

Building destruction is ordinarily permanent within the match rather than entering a unit-like respawn cycle.

## Relationships and linked structures

Observed Building links include:

- Building <-> Team
- Tower / structure <-> lane/base progression context
- higher-tier structure vulnerability <-> survival/destruction state of prerequisite structures
- Barracks state <-> future lane-creep spawn variant
- surviving Barracks count <-> Tier 4 Tower armor through current Barracks Reinforcement behavior
- multiple allied Buildings <-> shared team-activated protection effects such as Glyph
- Buildings <-> Backdoor Protection conditions / base-region context

These links show that a Building's current gameplay result can depend on other runtime instances, team state, world/spatial context, and shared effects.

## Variations / exceptions

- not all buildings attack
- not all buildings share the same vulnerability progression rules
- some building protections are local/regional while others are team-activated shared effects
- fixed position does not mean absence of runtime state
- a building's current armor or vulnerability can depend on other buildings rather than only its own definition

## Uncertain observations

- Which Building properties are direct state versus evaluated from other instances/world rules?
- Which base/lane/progression structures need independent identity versus relational/world-state representation?
- How should shared Building protection effects relate to the later Modifier / buff / debuff subject?

## Building observation status

- [x] Definition-facing structure recorded at first-pass granularity
- [x] Runtime-visible structure recorded at first-pass granularity
- [x] Relationships and linked structures recorded at first-pass granularity

---

# Subject: Ability

## Version anchor

- Observed date: 2026-09-02.
- Current version: Dota 2 7.41e.
- 7.41 changed current innate/hero-level-scaling structures, so earlier Facet-era ability organization is not treated as current.

## Sources checked

- Liquipedia, `Abilities`: https://liquipedia.net/dota2/Abilities
- Liquipedia, `Cooldown`: https://liquipedia.net/dota2/Cooldown
- Liquipedia, `Disable`: https://liquipedia.net/dota2/Disable
- Liquipedia, `Version 7.41`: https://liquipedia.net/dota2/7.41
- Liquipedia, `Version 7.41e`: https://liquipedia.net/dota2/7.41e

## Definition-facing structure

Ability definitions expose an intentionally heterogeneous set of optional structures, including:

### Identity / classification / targeting

- ability identity/name
- passive / active / toggle / autocast and related behavior classifications
- targeting shape such as no-target, unit-target, point/area-target, or combined forms
- target filters / allowed target categories where documented

### Cost / timing / execution parameters

- mana and/or health cost where applicable
- cooldown duration
- charge count / restore time where applicable
- cast point
- backswing
- channel duration where applicable
- cast range / area/radius values where applicable

### Effect parameters

- damage type where relevant
- duration values
- numerical parameters with per-level or other scaling
- linked upgrade behavior

### Level/scaling structure

Ability parameterization can vary by:

- learned ability level
- Hero level for current HeroLvl-scaling structures
- Aghanim-related upgrades or other linked content

The catalog does not assume every ability is representable as one fixed array indexed only by learned ability level.

## Runtime-visible structure

Depending on the ability, observable current state can include:

- learned/current level
- cooldown remaining
- current charges
- charge-restore progress
- toggle state
- autocast state
- casting phase
- channeling state and remaining channel time
- current availability / disabled state

An ability's current availability can depend on the caster's current status. Silence, break, disables, resource state, and other context can affect whether an ability may execute without changing the ability's definition.

## Relationships and linked structures

Observed links include:

- Hero / creep / Building / Item <-> Ability definition/content
- Ability <-> caster/owner context at runtime
- Ability <-> talent / Aghanim upgrade content
- Ability execution <-> selected target / point / area
- Ability current availability <-> caster state and resources
- Ability <-> modifiers/projectiles/effects that are documented as consequences of execution, to be observed directly in later subjects

The catalog does not yet decide whether an Ability runtime presence is a standalone runtime instance, owner-bound subobject, component, relation, or another structure.

## Variations / exceptions

- many optional fields are absent on many abilities
- passive abilities can still have runtime state/activation behavior
- toggle/autocast/channel/charge mechanics introduce distinct state shapes
- HeroLvl scaling prevents one universal `learned level -> parameters` assumption
- ability availability can be externally constrained while toggle/passive state remains present

## Uncertain observations

- Does every stateful Ability need independent runtime identity?
- Which effects belong to the Ability runtime state versus created modifiers/projectiles/other effects?
- How should cast phases, channels, interruption, and execution events be represented without prematurely defining an Interaction model?
- Which target-selection structures are reusable definition data versus runtime relation/state?

## Ability observation status

- [x] Definition-facing structure recorded at first-pass granularity
- [x] Runtime-visible structure recorded at first-pass granularity
- [x] Relationships and linked structures recorded at first-pass granularity

---

# Subject: Item

## Version anchor

- Observed date: 2026-09-02.
- Current version: Dota 2 7.41e.

## Sources checked

- Liquipedia, `Items portal`: https://liquipedia.net/dota2/Portal:Items
- Liquipedia, `Item Sharing`: https://liquipedia.net/dota2/Item_Sharing
- Liquipedia, `Neutral Items`: https://liquipedia.net/dota2/Neutral_Items
- Liquipedia, `Head-up Display`: https://liquipedia.net/dota2/Head-up_Display
- Liquipedia, `Magic Wand`: https://liquipedia.net/dota2/Magic_Wand
- Liquipedia, `Bottle`: https://liquipedia.net/dota2/Bottle
- Liquipedia, `Version 7.41e`: https://liquipedia.net/dota2/7.41e

## Definition-facing structure

Item documentation exposes structures including:

### Identity / acquisition / economy

- item identity/name
- shop/category context
- purchase cost
- sell value
- availability restrictions where applicable

### Composition

- component / recipe links
- recipe quantities / combination structure where applicable
- disassembly behavior where applicable

Recipes demonstrate that an object can be an inventory item while carrying little or no ordinary gameplay-stat bonus itself.

### Gameplay contribution/content

- passive stat bonuses
- passive abilities/effects
- active abilities/effects
- cooldown / mana or other costs for item actives
- charges where applicable
- shareability / droppability / sellability / other item-specific rules

## Runtime-visible structure

Depending on the item, observable current state can include:

- cooldown remaining
- current charges
- current mode/state selection
- stored content, such as Bottle rune content
- owner context
- holder context
- inventory/container/slot context
- enabled / muted / inactive behavior resulting from context
- ground/world position when dropped

Examples demonstrate that one item definition can support materially different runtime state shapes: charge accumulation, stored content, mode switching, or persistent ownership-state changes.

## Relationships and linked structures

Observed links include:

- Item <-> owner/purchaser
- Item <-> current holder
- Item <-> inventory/container/slot
- Item <-> recipe/components
- Item <-> active/passive Ability content
- Item <-> Hero stat/ability consequences

Owner and holder are observably not always the same relationship. Inventory location also carries gameplay meaning: moving the same item instance into the backpack can disable its active/passive benefits and change cooldown progression behavior without changing the item definition.

## Neutral-item variant

Neutral items use a dedicated slot and current crafting/acquisition rules distinct from ordinary shop purchase. The subject therefore exposes:

- dedicated container/slot context
- replacement behavior when another neutral item is selected/crafted
- tier/time availability context
- additional selection/enchantment context under current rules

The detailed crafting rule belongs to later Player/Team/Match and Interaction/Rule observation; the item-side structural consequences are recorded here.

## Variations / exceptions

- not every item has charges, active abilities, passive bonuses, modes, or stored content
- Recipe items show that inventory identity does not imply ordinary combat functionality
- ground items can have a world position while carried items normally use holder/container context instead
- owner and holder can diverge
- container/slot context can change an item's current behavior without changing its identity/definition
- some upgrade rewards, such as non-inventory Aghanim's Shard acquisition contexts, challenge a universal assumption that every item-like reward persists as a normal inventory item

## Uncertain observations

- Which item state belongs intrinsically to the item runtime instance versus ownership/holder/container relations?
- Does every carried item need independent runtime identity?
- Which recipe/component links belong to definition data and which combination processes belong to later Interaction/Rule models?
- How should dropped world-position state and carried holder-context state coexist in one reusable representation?

## Item observation status

- [x] Definition-facing structure recorded at first-pass granularity
- [x] Runtime-visible structure recorded at first-pass granularity
- [x] Relationships and linked structures recorded at first-pass granularity

---

# First observation batch: normalized comparison

This section records first-pass repeated names and cross-subject contrasts. It is **not** the reusable schema itself. Model conclusions are maintained in `../frameworks/gameplay-data-model.md`.

## First-pass normalized vocabulary

The following recording names recur strongly enough to use consistently in subsequent observation passes:

- `definition identity / classification`
- `definition-facing parameter`
- `current runtime value`
- `current quantity` versus `maximum / capacity / duration / parameter`
- `runtime position`
- `lifecycle state`
- `linked definition/content`
- `runtime relationship/context`
- `controller`, `owner`, `holder`, `source`, and `target` kept distinct unless evidence proves equivalence
- `container / slot context`
- `world or match context`
- `time-dependent value behavior`

Normalization here only standardizes observation language. It does not decide whether the final model stores or derives any particular value.

## Cross-subject structure matrix

| Observed structure | Hero | Creep / neutral boundary variants | Building | Ability | Item |
| --- | --- | --- | --- | --- | --- |
| Definition identity / classification | yes | yes | yes | yes | yes |
| Definition-facing numeric/typed parameters | yes | yes | yes | yes | yes |
| Mutable runtime state | yes | yes | yes | yes | yes |
| Current vs maximum/capacity/duration distinction | health/mana/barriers | health/mana; Tormentor barrier | health/protection | cooldown/charges/channel | charges/cooldown/stored content |
| Runtime spatial position | yes | yes | fixed but present | usually attached to caster rather than independently spatial | carried context or ground position |
| Lifecycle variation | death/respawn | spawn/death; Roshan respawn | permanent destruction | learned/available/cast/channel phases | buy/combine/drop/consume/transfer |
| Linked Ability/content | yes | yes | yes | upgrades/effect-producing content | yes |
| Owner/controller/holder context | player/team | neutral/faction/controller/source variants | team | caster/owner context | owner and holder can differ |
| Container/slot context | ability/inventory slots | weak in baseline | no ordinary inventory | ability slot/context | strong and behavior-changing |
| External state changes current result | strong | strong | strong | caster/world/upgrades | holder/slot/world/upgrades |
| Match-time dependency | progression/world rules | strong; multiple update semantics | some protections/scaling dependencies | HeroLvl/world dependencies | neutral-item/timing rules |
| Autonomous AI/aggro context | not baseline Hero structure | central for ordinary creeps | Tower target logic only | not an independent AI subject | not baseline |
| Historical state affects future results | some match systems | explicit in Roshan/stack credit | prerequisite-destruction history can matter through current state | not primary first-pass evidence | ownership/transfer history in special cases |
| Viewer-specific information differs from runtime truth | present in game generally but not isolated in Hero pass | explicit Roshan respawn case | not primary first-pass evidence | availability/UI can differ from mechanics but not yet modeled | not primary first-pass evidence |

## Repeated cross-subject observations that drive the first checkpoint

### Definition data and runtime state repeatedly differ

All five subjects expose definition-facing content and match-specific current state. This repeated distinction is strong enough to drive model revision.

### Same subject can use different time-update semantics for different values

Creep cases are especially clear:

- later lane-creep spawns use upgraded values without retroactively upgrading older surviving lane creeps
- existing neutral creeps can receive periodic stat upgrades
- neutral-creep ability levels can remain tied to spawn-time bands
- Roshan/Tormentor values can continue depending on match time through specialized lifecycle behavior

No universal `copy definition at spawn` or `always evaluate live` rule is supported by observation.

### Relationship context can change behavior without changing definition identity

Examples include:

- controlled neutral creeps
- Item owner versus holder
- Item backpack versus main inventory
- Building state depending on other Buildings/team protections
- Ability availability depending on caster state

### Runtime truth, historical state, and spatial context need future pressure-testing

Roshan/Tormentor expose obligations not yet mature enough for new primitives:

- actual runtime truth can differ from viewer-specific knowledge
- compressed historical facts can affect future behavior
- spatial regions/boundaries can control interaction and vision
- effects can outlive the source unit that caused them

These are carried forward explicitly so later observation can test whether existing runtime/world/relation structures are sufficient.

## First batch status

- [x] Hero first pass complete
- [x] Ordinary unit / creep first pass complete, including regular neutral creeps and Roshan/Tormentor boundary variants
- [x] Building first pass complete
- [x] Ability first pass complete
- [x] Item first pass complete
- [x] First-pass normalization and cross-subject comparison complete

## Next observation step

Continue with **Modifier / buff / debuff**.

This subject should specifically pressure-test:

- whether every stateful gameplay structure needs a `RuntimeInstance`
- whether owner/source/target attachment is better represented by a separate Subobject concept or ordinary relations
- whether duration, stacks, dispel behavior, aura attachment, and lingering effects can be recorded without inventing mechanic-specific primitives
- where `PropertyContribution` is sufficient and where modifier behavior requires later Interaction / Rule concepts

Do not redesign the model after one modifier example. Record a representative modifier batch first, then continue through the remainder of the second observation batch before the second abstraction checkpoint unless the observation language itself becomes insufficient.
