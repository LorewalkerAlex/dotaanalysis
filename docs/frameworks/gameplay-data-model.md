# Gameplay Data Model - Working Hypotheses

**Status:** `[OPEN]`

This document records the current structural hypotheses being developed in DOTAANALYSIS. They are deliberately incomplete and should be revised only after enough observed Dota 2 structures have been recorded and compared.

The purpose is to derive a reusable gameplay data model that can inform other game projects. It is **not** an attempt to reproduce or infer Valve's internal Dota 2 implementation architecture.

## Goal

Build a small set of general, composable data structures that can describe representative Dota 2 gameplay content and runtime state without introducing a special model for every mechanic.

Dota 2 heroes, items, abilities, modifiers, projectiles, map state, and systems are validation evidence for this model. They are not assumed to require separate top-level frameworks.

## Current research rhythm

The project is currently observation-first. The working sequence is:

```text
Observe
  -> Record
  -> Normalize
  -> Compare
  -> Abstract
  -> Pressure-test
```

The purpose of this rhythm is to prevent premature abstraction from consuming the research process.

### Observe

Collect structures that can be confirmed from current Dota 2 gameplay data and documentation. Record what exists before deciding what it means in a reusable model.

### Record

Add the observations to the `Observed Structure Catalog` with version/date context, source references, uncertainty, and visible relationships.

### Normalize

Unify names and recording conventions only after enough observations exist to show that two entries are describing the same kind of thing. Normalization is not yet abstraction.

### Compare

Build cross-subject matrices and look for repeated structures across heroes, ordinary units, buildings, abilities, items, modifiers, projectiles, world objects, world state, players, teams, and matches.

### Abstract

Revise this gameplay data model from repeated observed patterns rather than from a single convenient example.

### Pressure-test

Use deliberately difficult boundary cases to attack the abstraction. If a model fails, revise it and continue observation.

## Abstraction freeze during the first observation batch

The Object / Relation / Property / Contribution ideas below remain useful working hypotheses, but they are temporarily frozen during the first observation batch:

1. Hero
2. Ordinary unit / creep
3. Building
4. Ability
5. Item

During this batch, do not redesign the model merely because one observed field fits an alternative abstraction more elegantly. A model change is justified before the first checkpoint only if the existing observation language cannot record a fact at all.

After these five subjects have been recorded, run the first abstraction checkpoint: normalize names, compare structures, identify repeated patterns, and then revise this document.

## Modeling principles

1. **Observe before abstracting.** Current Dota 2 structure is evidence; the reusable model is a later synthesis.
2. **Model structure before interpretation.** Questions about strength, weakness, counterplay, identity, or design quality belong to a later analytical layer.
3. **Separate definition from runtime instance as a working hypothesis.** This distinction remains useful, but its exact implementation is not assumed.
4. **Prefer composition over mechanic-specific types.** A Dota mechanic name does not automatically justify a model primitive.
5. **Keep stored and derived data distinct when evidence supports the distinction.** Do not assume visible UI values map one-to-one to stored fields.
6. **Represent relationships explicitly when they are not intrinsic object state.** Ownership, source/target attachment, control, and similar relations should not automatically become fields on one participant.
7. **Use difficult cases to revise the model.** Ability, Modifier, Projectile, Item, Tree, terrain, and similar boundary cases are more useful than easy cases when testing an abstraction.
8. **Do not overfit Dota.** A proposed primitive is stronger when it explains multiple unrelated mechanics and can plausibly transfer to another game.

## Current structural hypotheses

The current model tentatively separates game definitions from runtime world data.

```text
GameData {
    Definition[]
}

RuntimeWorld {
    ObjectInstance[]
    RelationInstance[]
    WorldState
}
```

`SubobjectInstance` is a current working hypothesis for runtime state that is structurally owned by another object. Whether it should remain distinct from `ObjectInstance` is unresolved.

```text
ObjectInstance {
    id
    definition_ref
    state
    parts[]?
}

SubobjectInstance {
    local_id
    definition_ref
    owner_ref
    state
}

RelationInstance {
    type
    subject
    object
    state?
}

WorldState {
    global_values
    spatial_fields
}
```

These structures are hypotheses, not conclusions. The observed structure catalog takes precedence as evidence when a later abstraction conflicts with what Dota 2 actually exposes.

### Definition

A `Definition` tentatively describes a kind of gameplay content independently of any particular match instance.

Examples of candidate definition domains include heroes, units, items, abilities, modifiers, and projectiles. The existence of a named Dota category does not imply that each category needs a unique base model.

### ObjectInstance

An `ObjectInstance` is a candidate representation for something that needs independent runtime identity and runtime state or lifecycle.

Spatial presence is not required. A projectile may be a spatial object; another runtime object may have no independent position.

### SubobjectInstance

A `SubobjectInstance` is a provisional representation for runtime state that has local identity but whose lifecycle is structurally bound to an owner.

Abilities are an important future pressure-test case because they can have runtime values such as level, cooldown, charges, or toggle state while also being tightly attached to a unit.

### RelationInstance

A `RelationInstance` tentatively represents data that belongs to a relationship between participants rather than intrinsically to one object.

Simple relations may be fact-like, while other relations may require their own runtime state and lifecycle. Ownership and source/target attachment are candidate examples. Modifier representation is deliberately unresolved.

### WorldState

`WorldState` tentatively contains state that belongs to the match or world rather than to a discrete runtime object.

The current working distinction is:

```text
WorldState {
    global_values
    spatial_fields
}
```

A spatial field can be treated abstractly as a query over position:

```text
SpatialField<T>:
    Position -> T
```

Terrain height or passability are candidate spatial-field data. A discrete tree with independent identity, state, and lifecycle may instead be an object. Therefore `Environment` remains a useful human-facing word but is not currently a formal top-level model category.

## Property model hypothesis

A `Property` is currently treated as a value query, not automatically as a stored field.

```text
Property(object, key) -> value
```

Current working property sources are:

```text
PropertySource :=
    DefinitionValue
    | StateValue
    | DerivedValue
    | AggregateValue
```

This classification is explicitly provisional. The observation pass may show that it mixes independent dimensions such as data location and evaluation strategy.

### DefinitionValue

Read from definition data for the object's type or content definition.

### StateValue

Stored mutable runtime state belonging to the current instance.

### DerivedValue

Computed from other values and therefore not necessarily stored independently.

```text
health_ratio(object) =
    health_current(object) / health_max(object)
```

### AggregateValue

Resolved from a base value plus external contributions.

```text
AggregateValue(object, property) =
    Resolve(
        base_value,
        Contributions(object, property)
    )
```

The exact resolver model is unresolved. Additive, multiplicative, override, ordering, stacking, and other semantics should be introduced only when repeated observations require them.

## Contribution hypothesis

`Contribution` is the current neutral representation for an external source influencing an aggregate property.

```text
Contribution {
    source
    target
    property
    operation
    value
}
```

This is a working hypothesis, not yet an established primitive. Item, ability, modifier, and aura observations may later show that Contribution is a special case of a more general structure.

## Current versus maximum/capacity values

Runtime current values and maximum/capacity/parameter values should not be collapsed into one field in the current hypothesis.

Examples:

```text
health_current != health_max
mana_current   != mana_max
cooldown_remaining != cooldown_duration
```

A change to a maximum or duration does not by itself define how the corresponding current value changes. That behavior belongs to later interaction/rule semantics rather than to the property definition alone.

## Property dependencies

Properties may depend on other properties:

```text
A -> B -> C
```

This implies a possible property dependency graph. The project has not yet decided how such dependencies should be declared, evaluated, cached, invalidated, or ordered.

## Current model boundaries

The following concepts are intentionally **not yet** part of the established structural model:

```text
Action
Interaction
Effect
Event
Rule
Condition
Transition
Capability
Constraint
Strength
Weakness
Counterplay
Identity
```

Some will likely become necessary. They should be introduced only when observation and comparison show that the current structural vocabulary cannot represent the next tested layer without them.

Higher-level design concepts such as capability, counterplay, strengths/weaknesses, and identity belong above the structural data model rather than inside its basic vocabulary.

## Unresolved questions

### World and runtime objects

- What is the minimal distinction between independent `ObjectInstance` and owner-bound `SubobjectInstance`?
- Should Ability be an object, subobject, component, or another structure?
- Should Modifier be a stateful relation, subobject, object, or multiple representations depending on behavior?
- Which item states belong to the item instance, which belong to ownership/inventory relations, and which are derived?
- Which projectiles require full runtime identity versus being execution data of another interaction?
- Which map elements are discrete objects and which are spatial fields or other world state?

### Properties

- What is the minimal property schema shared across heroes, ordinary units, buildings, items, abilities, and other representative objects?
- Which property values should be stored, derived, or aggregate?
- How should additive, multiplicative, override, ordering, and stacking semantics be represented?
- How should a property dependency graph be evaluated?
- How are Contribution activation, targeting, lifetime, and removal represented?

### Next structural layers

- What is the minimal neutral representation of an interaction?
- What data selects source and target participants?
- How should conditions, effects, events, transitions, and time-dependent rules compose?
- Can attacks, abilities, item actives/passives, auras, environmental effects, and system rules share the same primitives?

## Validation strategy

Do not attempt to model all of Dota 2 at once. Build the observation inventory first, then use representative and boundary cases to pressure-test the smallest model supported by repeated evidence.

The planned observation corpus is:

1. Hero
2. Ordinary unit / creep
3. Building
4. Ability
5. Item
6. Modifier / buff / debuff
7. Projectile and other short-lived spatial objects
8. World objects such as trees, wards, and runes
9. World state such as terrain, vision, time, and spatial fields
10. Player, Team, and Match-level structures

The first abstraction checkpoint occurs only after the first five subjects have been recorded.

When a case cannot be represented cleanly, first ask whether the catalog is missing an observation or whether existing primitives can be composed differently. Add a new primitive only when it explains a reusable structural distinction rather than one isolated Dota exception.

## Next research step

Continue the `Observed Structure Catalog` with the remaining Hero runtime-visible structure and relationships. Then close the Hero observation pass and move immediately to ordinary units / creeps without revising the abstract model.
