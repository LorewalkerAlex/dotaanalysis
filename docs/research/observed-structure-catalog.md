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

During the first observation batch - Hero, ordinary unit / creep, Building, Ability, Item - do not redesign the working gameplay data model merely because one observation suggests a cleaner abstraction. Record first. Abstract at the checkpoint.

## Observation rules

1. Record externally observable or documentable structure before interpretation.
2. Distinguish verified Dota 2 facts from recording conventions and uncertainty.
3. Include a version/date anchor for changeable Dota 2 facts.
4. Preserve distinctions exposed by sources even when they may later be normalized, such as `base` versus `starting` values.
5. Use group headings only for readability. A group such as `attack` or `movement` does not establish a final schema primitive.
6. Record visible links between subjects without prematurely deciding whether the final model should represent them as ownership, containment, references, relations, subobjects, or something else.
7. Mark unclear cases as uncertain rather than resolving them through abstraction.

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

### First batch

1. Hero
2. Ordinary unit / creep
3. Building
4. Ability
5. Item
6. First abstraction checkpoint

### Second batch

1. Modifier / buff / debuff
2. Projectile and other short-lived spatial objects
3. World objects such as trees, wards, runes, and similar discrete objects
4. World state such as terrain, vision, time, and spatial fields
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

These sources are used as observable documentation, not as evidence of Valve's internal storage model.

## Definition-facing structure

The following groups are recording conveniences only. They are not yet final schema categories.

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

The attributes table also exposes totals such as total starting attributes, total growth, and level-30 totals. These are recorded as visible results but are not yet classified as stored or derived data.

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

At this stage, `starting` values are recorded as exposed values. Their dependency on attributes or other rules is deliberately not normalized into the catalog entry.

## Linked gameplay content - first-pass observation

Current Dota 2 hero structure visibly links a hero to additional gameplay content including:

- innate ability content
- other hero abilities / ability slots
- talent choices
- Aghanim's Scepter upgrade references where applicable
- Aghanim's Shard upgrade references where applicable

For this catalog, these are recorded only as visible links. The catalog does **not** yet decide whether the reusable model should represent them as containment, ownership, references, relations, subobjects, components, or another structure.

## Current exclusions from the Hero definition-facing pass

The following are intentionally deferred to the Hero runtime-visible and relationship passes:

- current health and mana
- level and experience
- position and facing direction during a match
- alive / dead state
- learned ability levels
- cooldown states
- charges
- current inventory contents
- selected talents
- active modifiers / buffs / debuffs
- current orders / targets
- player and team relationships

## Variations / exceptions already visible

- Projectile speed is meaningful for ranged attack structures and may not apply in the same way to melee attacks.
- Sources can expose separate day/night movement or vision values.
- Base and starting values are not always the same visible number, so those labels must remain distinct during observation.
- 7.41 removed the Facet layer from current hero structure.

## Uncertain observations

The following questions are intentionally unresolved until later subjects are recorded and compared:

- Which Hero definition-facing entries are authoritative inputs versus calculated presentation values?
- Which entries belong to a general Unit structure shared by creeps and buildings?
- Which linked ability/talent/upgrade structures are owned by the Hero, referenced by the Hero, or independently instantiated at runtime?
- Which current Hero values are best recorded as runtime state versus evaluated properties?

## Hero observation status

- [x] Definition-facing structure recorded at first-pass granularity
- [ ] Runtime-visible structure
- [ ] Relationships and linked structures beyond the first-pass content links

The next concrete analysis step is to record Hero runtime-visible structure. After Hero relationships are recorded, close the Hero observation pass and move directly to ordinary units / creeps without revising the abstract gameplay data model.
