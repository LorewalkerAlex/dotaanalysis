# Gameplay Data Model — Working Model

**Status:** `[OPEN]`

This document records the current best structural model being developed in DOTAANALYSIS. It is deliberately incomplete and should be revised when representative Dota 2 cases expose a better abstraction.

The purpose is to derive a reusable gameplay data model that can inform other game projects. It is **not** an attempt to reproduce or infer Valve's internal Dota 2 implementation architecture.

## Goal

Build a small set of general, composable data structures that can describe representative Dota 2 gameplay content and runtime state without introducing a special model for every mechanic.

Dota 2 heroes, items, abilities, modifiers, projectiles, map state, and systems are validation evidence for this model. They are not assumed to require separate top-level frameworks.

## Modeling principles

1. **Model structure before interpretation.** First describe what data exists and how it relates. Questions about strength, weakness, counterplay, identity, or design quality belong to a later analytical layer.
2. **Separate definition from runtime instance.** Static content definition and a particular match instance are different kinds of data.
3. **Prefer composition over mechanic-specific types.** A Dota mechanic name does not automatically justify a model primitive.
4. **Keep stored and derived data distinct.** Do not duplicate a value as stored state when it can be derived reliably from other state.
5. **Represent relationships explicitly when they are not intrinsic object state.** Ownership, source/target attachment, control, and similar relations should not automatically become fields on one participant.
6. **Use difficult cases to revise the model.** Ability, Modifier, Projectile, Item, Tree, terrain, and similar boundary cases are more useful than easy cases when testing an abstraction.
7. **Do not overfit Dota.** A proposed primitive is stronger when it explains multiple unrelated mechanics and can plausibly transfer to another game.

## Current structural baseline

The current model separates game definitions from runtime world data.

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

### Definition

A `Definition` describes a kind of gameplay content independently of any particular match instance.

Examples of candidate definition domains include heroes, units, items, abilities, modifiers, and projectiles. The existence of a named Dota category does not imply that each category needs a unique base model.

### ObjectInstance

An `ObjectInstance` is a candidate representation for something that needs independent runtime identity and runtime state or lifecycle.

Spatial presence is not required. A projectile may be a spatial object; another runtime object may have no independent position.

### SubobjectInstance

A `SubobjectInstance` is a provisional representation for runtime state that has local identity but whose lifecycle is structurally bound to an owner.

Abilities are an important pressure-test case because they can have runtime values such as level, cooldown, charges, or toggle state while also being tightly attached to a unit.

### RelationInstance

A `RelationInstance` represents data that belongs to a relationship between participants rather than intrinsically to one object.

Simple relations may be fact-like, while other relations may require their own runtime state and lifecycle. Ownership and source/target attachment are candidate examples. Modifier representation is deliberately unresolved: some modifiers may be better modeled as stateful relations, subobjects, or another structure discovered later.

### WorldState

`WorldState` contains state that belongs to the match or world rather than to a discrete runtime object.

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

## Property model

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

The exact resolver model is unresolved. Additive, multiplicative, override, ordering, stacking, and other semantics should be introduced only when representative cases require them.

## Contribution

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

For example, an item should not need to mutate a hero's base definition value permanently. It may instead contribute to an effective runtime property while the relevant relation and activation rules hold.

The lifecycle, activation conditions, target selection, ordering, and stacking semantics of contributions remain unresolved.

## Current versus maximum/capacity values

Runtime current values and maximum/capacity/parameter values should not be collapsed into one field.

Examples:

```text
health_current != health_max
mana_current   != mana_max
cooldown_remaining != cooldown_duration
```

A change to a maximum or duration does not by itself define how the corresponding current value changes. That behavior belongs to interaction/rule semantics rather than to the property definition alone.

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

Some will likely become necessary. They should be introduced only when the current object/property model cannot describe the next tested layer without them.

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

Do not attempt to model all of Dota 2 at once. Use representative and boundary cases to pressure-test the smallest current model.

The validation corpus should include deliberately different examples from:

- heroes and ordinary units;
- items, inventory/ownership, and dropped items;
- abilities with runtime state;
- modifiers and auras;
- projectiles and short-lived spatial objects;
- buildings, trees, terrain, spatial fields, and global world state;
- combat, progression, economy, vision, and other system-level rules.

When a case cannot be represented cleanly, first ask whether existing primitives can be composed differently. Add a new primitive only when it explains a reusable structural distinction rather than one isolated Dota exception.

## Next research step

The immediate next step is to build a first **Property Schema** from representative object types without yet modeling full interaction execution.

The research should compare which properties are shared or specific across candidate objects such as heroes, ordinary units, buildings, items, and abilities, then use those cases to revise the current `Property` model before moving into `Interaction` and `Rule`.
