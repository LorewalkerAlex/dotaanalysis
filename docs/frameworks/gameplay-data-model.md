# Gameplay Data Model - Working Hypotheses

**Status:** `[OPEN]`

This document records the current structural hypotheses being developed in DOTAANALYSIS. It represents the project's **current best working model**, not a claim about Dota 2's internal implementation architecture.

The model is deliberately provisional. It should change when repeated observation shows that a simpler or more general structure explains the evidence better.

## Goal

Build a small set of general, composable data structures that can describe representative Dota 2 gameplay content and runtime state without introducing a special model for every mechanic.

Dota 2 heroes, units, buildings, abilities, items, modifiers, projectiles, world objects, world state, players, teams, and matches are evidence for this model. Named Dota categories are not assumed to require separate top-level reusable-model types.

## Research rhythm

The project uses:

```text
Observe
  -> Record
  -> Normalize
  -> Compare
  -> Abstract
  -> Pressure-test
```

The first observation batch is complete at first-pass granularity:

1. Hero
2. Ordinary unit / creep, including regular neutral creeps and Roshan / Tormentor boundary variants
3. Building
4. Ability
5. Item

The first Normalize / Compare / Abstract checkpoint is also complete. The current model below is the result of that checkpoint.

The next observation batch begins with Modifier / buff / debuff. During the second batch, treat this first-checkpoint model as a working hypothesis and collect pressure-test evidence rather than redesigning the model after every isolated case. Broad revision belongs at the second abstraction checkpoint unless the observation language itself cannot record a fact.

## Modeling principles

1. **Observe before abstracting.** Current Dota 2 structure is evidence; the reusable model is synthesis.
2. **Model structure before interpretation.** Strength, weakness, counterplay, identity, and design quality belong to later analytical layers.
3. **Separate definition-facing data from match runtime state.** The first observation batch repeatedly supports this distinction.
4. **Prefer neutral runtime vocabulary.** A runtime structure does not need ordinary spatial-object behavior to have identity and state.
5. **Prefer composition over mechanic-specific types.** A Dota mechanic name does not automatically justify a primitive.
6. **Represent relationship context explicitly when evidence shows it matters.** Owner, holder, controller, source, target, container, lane, camp, and similar relationships should not be collapsed merely for convenience.
7. **Treat Property as a value query, not automatically as a stored field.** Visible values can depend on definition data, current state, relations, world state, and resolution rules.
8. **Separate value inputs from value-resolution strategy.** Data origin and evaluation method are independent dimensions.
9. **Do not promote every external gameplay effect into PropertyContribution.** Contributions are currently only a candidate mechanism for aggregate property resolution.
10. **Keep current quantities distinct from capacities/durations/parameters.** Current health, current mana, barrier amount, charges, and cooldown remaining have behavior distinct from their maximum/capacity/reference values.
11. **Use boundary cases to attack abstractions.** Ability, Item, Roshan, Tormentor, Modifier, Projectile, Tree, terrain, and viewer-specific information are especially useful.
12. **Do not overfit Dota.** A proposed primitive is stronger when it explains multiple unrelated mechanics and can plausibly transfer to other games.

---

# First abstraction checkpoint

## Evidence that survived comparison

The first five subjects repeatedly expose:

- stable definition-facing identity/content
- match-specific mutable state
- definition-to-definition links
- runtime relationships whose state/context changes gameplay
- current values that can differ from definition-facing values
- properties influenced by multiple inputs
- lifecycle differences that do not map cleanly to one Dota category hierarchy

Several boundary cases also prevent premature simplification:

- Ability has runtime level/cooldown/charges/toggle/channel state despite usually lacking independent world position.
- Item can change holder/container/slot context without changing definition identity; owner and holder can differ.
- Lane-creep, neutral-creep, and boss values use different time-update semantics.
- Roshan exposes viewer-specific information that differs from runtime truth, historical state that affects future behavior, and region/boundary spatial rules.
- Tormentor exposes barrier-dominant durability, special world-transition movement, triggered passive state, and effects that can remain after the source unit dies.

These observations motivate the current model without yet requiring a full Interaction / Rule / Information model.

---

# Current structural working model

```text
GameData {
    Definition[]
    DefinitionLink[]
}

RuntimeWorld {
    RuntimeInstance[]
    RelationInstance[]
    WorldState
}

RuntimeInstance {
    id
    definition_ref
    state
}

DefinitionLink {
    type
    source
    target
    data?
}

RelationInstance {
    type
    subject
    object
    state?
}

WorldState {
    global_values
    spatial_data
}
```

These structures are hypotheses, not conclusions. The `Observed Structure Catalog` remains the evidence source and takes precedence if future observation contradicts this model.

## Definition

A `Definition` describes gameplay content independently of a particular match instance.

Candidate definition domains include heroes, units, buildings, items, abilities, modifiers, and projectiles. A named Dota category is not itself evidence that the reusable model needs a category-specific base type.

Definition-facing values may include parameters later used directly, copied at creation, transformed at creation, queried live, or combined with runtime/world context. The first observation batch shows that no single evaluation policy should be inferred merely from a value being visible in definition-facing documentation.

## DefinitionLink

`DefinitionLink` is a first-checkpoint addition supported by repeated definition-layer connections such as:

- Hero -> Ability / Talent / upgrade content
- Creep -> Ability
- Building -> Ability
- Item -> component / Recipe / Ability
- Ability -> linked upgrade content

Current neutral shape:

```text
DefinitionLink {
    type
    source
    target
    data?
}
```

`data?` permits link-local information such as slot/order/quantity/role when evidence requires it.

This is not yet assumed to be structurally identical to runtime `RelationInstance`. The distinction should be revisited after more subjects are compared.

## RuntimeInstance

`RuntimeInstance` replaces the earlier name `ObjectInstance` as the current neutral working term.

A runtime instance is something for which the model needs match-specific identity and state/lifecycle.

```text
RuntimeInstance {
    id
    definition_ref
    state
}
```

Independent spatial presence is **not** required. This matters because:

- Heroes, creeps, and buildings are clearly world-located runtime instances.
- Items can be carried through holder/container context or exist on the ground.
- Abilities can carry runtime level/cooldown/charge/toggle/channel state while normally remaining attached to another runtime participant.

`RuntimeInstance` deliberately does not say how state is physically stored or computed.

## SubobjectInstance - still unproven

The earlier model proposed:

```text
SubobjectInstance {
    local_id
    definition_ref
    owner_ref
    state
}
```

The first observation batch does **not** provide enough evidence to keep this as an established primitive.

Ability state provides some motivation for an owner-bound structure, but boundary cases warn against defining a general subobject by owner-bound lifecycle:

- an effect can persist after its source unit dies, as seen in the Tormentor boundary case
- ownership, attachment, source, holder, and controller are observably distinct relationships in other subjects

Therefore the current status is:

```text
SubobjectInstance?   // candidate only; not part of the supported minimal model yet
```

Modifier and Projectile observations are the next major tests of whether a distinct owner-bound runtime primitive is actually necessary.

## RelationInstance

A `RelationInstance` represents runtime data that belongs to a relationship/context between participants rather than intrinsically to one participant.

```text
RelationInstance {
    type
    subject
    object
    state?
}
```

First-batch evidence supporting explicit runtime relations includes:

- Hero <-> Player controller
- Hero <-> Team
- neutral creep <-> current controller
- creep <-> lane / wave / camp context
- Item <-> owner
- Item <-> current holder
- Item <-> container / slot
- Building <-> Team / prerequisite-building context
- Ability <-> caster / target context

The Item case is especially important because owner and holder can differ, and the same item instance can behave differently after only its container/slot relation changes.

The model does not yet decide when a relation requires independent identity, stored state, lifetime, or derivation from other state.

## WorldState

`WorldState` represents runtime state that belongs to the match/world rather than to one discrete runtime instance or one pairwise relation.

Current shape:

```text
WorldState {
    global_values
    spatial_data
}
```

### Global values

Repeated first-batch evidence supports world/global values such as:

- match time
- day/night state
- other match-level values that influence multiple unrelated participants

Time affects creep upgrades, Roshan/Tormentor scaling and movement context, ability scaling rules, item/neutral-item availability, and other systems.

### Spatial data - shape intentionally unresolved

The earlier model prematurely proposed only:

```text
SpatialField<T>:
    Position -> T
```

The first batch shows that future spatial representation must also be able to discuss structures such as:

- point position
- lane context
- camp/home regions
- Roshan pit membership
- region boundaries that alter attack validity
- vision boundaries
- paths / relocation between regions

A spatial field may remain one useful representation, but it is no longer treated as the only expected spatial shape.

The second observation batch should test whether reusable spatial primitives need fields, regions, geometry, graphs, discrete world objects, or some combination.

`Environment` remains a human-facing concept rather than a formal top-level category.

---

# Property working model

## Property is a value query

A `Property` remains a value query rather than an assumption that every exposed value is stored directly on an instance.

```text
Property(instance, key, world) -> value
```

The first observation batch confirms that the earlier `PropertySource` union mixed two independent questions:

1. **Where do inputs come from?**
2. **How is the result resolved?**

The model now separates them.

## ValueInput

Current candidate input origins:

```text
ValueInput :=
    DefinitionData
    | InstanceState
    | RelationState
    | WorldState
```

A property may use more than one input origin.

### DefinitionData

Values or structures from content definitions.

### InstanceState

Mutable match state associated with the relevant runtime instance.

Examples include current health, current charges, current mode, or a stored historical result if observation later supports that representation.

### RelationState

State/context belonging to a relation.

The Item backpack case strongly motivates this input category: item definition and item identity remain the same while holder/container/slot context changes current availability and cooldown behavior.

### WorldState

Match/world values such as time, day/night, and later spatial state.

Roshan and Tormentor time scaling provide clear first-batch examples of current values depending on world time rather than only definition data or instance-local state.

## Resolution

Current candidate evaluation strategies:

```text
Resolution :=
    Direct
    | Derived
    | Aggregate
```

### Direct

The result is read directly from one selected input value for the purpose of the current model.

`Direct` does not claim anything about Valve's internal storage; it is only a modeling distinction from further derivation or aggregation.

### Derived

The result is computed from other values.

Example shape:

```text
health_ratio(instance) =
    health_current(instance) / health_max(instance)
```

Time-scaled values can also be derived from definition parameters plus `WorldState.match_time`.

### Aggregate

The result combines a base/input value with one or more contributing influences.

Example shape:

```text
AggregateProperty(instance, key) =
    Resolve(
        base_inputs,
        PropertyContributions(instance, key)
    )
```

The exact resolver remains unresolved. Additive, multiplicative, override, ordering, priority, stacking, and caps should be introduced only when repeated observation requires them.

---

# PropertyContribution hypothesis

`PropertyContribution` is the current neutral candidate for an external source influencing an **Aggregate** property.

```text
PropertyContribution {
    source
    target
    property
    operation
    value
}
```

First-batch evidence makes this useful for structures such as:

- item stat bonuses
- building protection/reinforcement values
- other additive/multiplicative/override-like property influences

However, the first batch also shows that it must **not** become the universal representation of every gameplay effect.

PropertyContribution does not naturally explain by itself:

- future creep spawn changes caused by Barracks destruction
- Glyph enabling additional Tower attack behavior
- backpack context disabling an item's active/passive functionality
- Silence / Break changing ability availability by rule
- Roshan behavior depending on previous killing team or kill ordinal
- Tormentor death creating a lingering area effect
- reward selection that queries team/player state
- pit-region membership controlling whether an interaction is valid

Those cases belong to later Interaction / Effect / Rule / Event / Transition investigation.

Therefore the first-checkpoint conclusion is:

> `PropertyContribution` is a candidate component of Aggregate property resolution, not a general external-effect primitive.

---

# Current versus maximum / capacity / duration / parameter values

The first observation batch strongly reinforces this distinction.

Examples include:

```text
health_current != health_max
mana_current != mana_max
barrier_current != barrier_capacity
cooldown_remaining != cooldown_duration
charges_current != charges_capacity
channel_remaining != channel_duration
```

A change to a maximum, capacity, duration, or other reference parameter does not by itself determine how the corresponding current value changes.

Observed cases show multiple policies are possible:

- later creep spawns can use new values while existing instances retain previous values
- existing neutral creeps can receive selected live stat upgrades
- neutral-creep ability levels can remain tied to spawn-time bands
- current quantities can refill, regenerate, preserve percentage, preserve absolute value, reset, or follow another rule depending on the mechanic

Those transition semantics belong to later Rule / Interaction modeling rather than to the property key alone.

---

# Property dependencies

Properties can depend on other properties and context:

```text
A -> B -> C
```

First-batch cases make a dependency graph plausible, but the project has not yet decided how dependencies should be:

- declared
- evaluated
- cached
- invalidated
- ordered
- cycle-checked

Do not introduce infrastructure-level assumptions into the research model until repeated gameplay cases demand them.

---

# Evidence obligations deliberately not yet promoted to primitives

The first batch exposed several important structures but not enough repeated evidence to justify dedicated primitives yet.

## Runtime history

Roshan and stacking/reward cases show that past events can affect future behavior.

For now, compressed history can be represented as current instance/relation/world state when needed, such as a previous responsible team or kill count. A separate `History` primitive is not yet justified.

## Runtime truth versus viewer-specific information

Roshan respawn information provides a clear distinction:

```text
actual runtime truth
!= viewer-specific knowledge
!= UI presentation
```

This is a required future modeling problem, but Player / Team / vision/world-state observations are still missing. No `Information` primitive is introduced yet.

## Spatial regions and boundaries

Roshan pits, camps, lanes, and building protection contexts show that future space modeling must go beyond only point coordinates.

No final `Region`, `Field`, `Graph`, or `Geometry` primitive is selected yet.

## Effects that outlive sources

Tormentor's lingering post-death area effect shows that source lifecycle and effect lifecycle can diverge.

This is a direct pressure-test target for the Modifier / buff / debuff and later Effect observations.

---

# Current model boundaries

The following concepts are intentionally **not yet established primitives**:

```text
SubobjectInstance
Action
Interaction
Effect
Event
Rule
Condition
Transition
Information
History
Region
SpatialField
Capability
Constraint
Strength
Weakness
Counterplay
Identity
```

Some will likely become necessary. They should be promoted only when repeated observation shows a reusable structural distinction that cannot be expressed cleanly through the current model.

Higher-level analytical concepts such as capability, counterplay, strengths/weaknesses, identity, and strategic function belong above the structural gameplay data model.

---

# Unresolved questions

## Runtime instances and relations

- Does a stateful Ability need independent `RuntimeInstance` identity, or can some ability state be represented in another owner-bound form?
- Does `SubobjectInstance` represent a real reusable lifecycle distinction, or can source/owner/attachment relations plus ordinary runtime instances express the same evidence more cleanly?
- Should Modifier be a runtime instance, relation, owner-bound structure, property contribution, or multiple forms depending on behavior?
- Which projectiles need full runtime identity versus execution-state representation?
- Which item state belongs to the item instance versus owner/holder/container relations?
- Which relations require their own stored state/lifetime instead of being derived?

## Definitions and definition links

- Is `DefinitionLink` genuinely distinct from a generic Relation abstraction, or only the definition-layer use of the same concept?
- What link-local data is needed repeatedly across ability slots, recipes, upgrades, and other content graphs?

## Properties

- What is the minimal Property schema shared across representative runtime structures?
- How should additive, multiplicative, override, ordering, priority, stacking, and caps be represented?
- How should dependency graphs be evaluated?
- How are PropertyContribution activation, targeting, lifetime, suppression, and removal represented?
- Which visible values should be modeled as state versus derived/aggregate queries?

## World / space / information

- What spatial structures are needed for terrain, vision, pits, lanes, camps, height, passability, and area effects?
- Which map elements are discrete runtime instances and which belong to spatial/world state?
- How should runtime truth be separated from what a Player or Team knows or is allowed to observe?
- Which match-history facts need explicit durable state versus derivation from current state or event history?

## Next structural layers

- What is the minimal neutral representation of an interaction?
- What data selects source and target participants?
- How should conditions, effects, events, transitions, and time-dependent rules compose?
- Can attacks, abilities, item actives/passives, auras, environmental effects, and system rules share the same primitives?

---

# Validation strategy

Do not attempt to model all of Dota 2 at once.

## Completed first batch

1. Hero
2. Ordinary unit / creep
3. Building
4. Ability
5. Item
6. First abstraction checkpoint

## Second observation batch

1. Modifier / buff / debuff
2. Projectile and other short-lived spatial objects
3. World objects such as trees, wards, and runes
4. World state such as terrain, vision, time, and spatial structures
5. Player, Team, and Match-level structures
6. Second abstraction checkpoint

When a case cannot be represented cleanly, first ask whether:

1. the observation catalog is missing a fact;
2. existing primitives can be composed differently;
3. a current primitive is over-specific or conflates independent dimensions.

Add a new primitive only when it explains a repeated structural distinction rather than one isolated Dota exception.

---

# Next research step

Continue the `Observed Structure Catalog` with **Modifier / buff / debuff**.

That pass should directly pressure-test:

- `RuntimeInstance`
- the unresolved `SubobjectInstance?` hypothesis
- `RelationInstance`
- `PropertyContribution`
- duration / stack / suppression / dispel / source / target / aura relationships
- source lifecycle versus effect lifecycle

Do not redesign the model after one modifier example. Record representative modifier structures first and continue the second observation batch before the second abstraction checkpoint unless the observation language cannot capture an observed fact.
