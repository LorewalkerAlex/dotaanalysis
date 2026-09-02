# DOTAANALYSIS Research Roadmap

This file is both the research map and the project progress record. It is expected to evolve as the research develops.

## Status convention

- `[ ]` - not yet completed.
- `[ ] [ACTIVE]` - the current primary research node. There should normally be only one primary active node because the project is sequential rather than parallel.
- `[ ] [OPEN]` - meaningful work exists, but important questions remain unresolved before the node can be treated as currently usable.
- `[x]` - the node currently has a usable result and the project can progress beyond it. This does **not** mean the result is immutable.

Indentation expresses the relationship between larger questions and their subquestions. Within the same level, top-to-bottom order is the current intended research order unless the user decides to change it.

## Roadmap

- [x] Establish project operating model
  - [x] Treat ChatGPT sessions as sequential context windows for one continuous project
  - [x] Use GitHub as the durable source of truth
  - [x] Use a mutable indented roadmap as both research map and progress record
  - [x] Require explicit user approval before every repository mutation
  - [x] Use Web Local Development for approved changes: public GitHub baseline -> local artifact apply/validation -> separate commit/push -> public GitHub verification
  - [x] Separate verified facts, analytical interpretations, and design-intent hypotheses

- [ ] [ACTIVE] Build a reusable gameplay data model
  - [x] Establish the current modeling direction
    - [x] Treat Dota 2 as evidence for a transferable gameplay data model rather than as three unrelated Hero / Item / System frameworks
    - [x] Model structure before higher-level design interpretation
    - [x] Prefer general composable primitives over mechanic-specific special cases
    - [x] Distinguish the research model from claims about Dota 2's internal implementation architecture

  - [ ] [OPEN] Build an observed structure inventory before further abstraction
    - [x] Adopt the research rhythm: Observe -> Record -> Normalize -> Compare -> Abstract -> Pressure-test
    - [x] Freeze the pre-checkpoint Object / Relation / Property / Contribution ideas while the first observation batch was collected
    - [x] First observation batch
      - [x] Hero
        - [x] Record definition-facing structure
        - [x] Record runtime-visible structure
        - [x] Record relationships and linked structures
      - [x] Ordinary units / creeps, including regular neutral creeps and Roshan / Tormentor boundary variants
      - [x] Buildings
      - [x] Abilities
      - [x] Items
    - [x] First abstraction checkpoint after the first observation batch
      - [x] Normalize repeated field and relationship names at first-pass granularity
      - [x] Build a cross-subject structure matrix
      - [x] Revise the gameplay data model only from repeated observed patterns
    - [ ] Second observation batch
      - [ ] Modifiers / buffs / debuffs
      - [ ] Projectiles and other short-lived spatial objects
      - [ ] World objects such as trees, wards, runes, and similar discrete objects
      - [ ] World state such as terrain, vision, time, and spatial structures
      - [ ] Player, Team, and Match-level structures
    - [ ] Second abstraction checkpoint
      - [ ] Re-test RuntimeInstance / RelationInstance / WorldState and unresolved Subobject hypotheses
      - [ ] Re-test Property input/resolution and PropertyContribution hypotheses
      - [ ] Add new primitives only when repeated observations require them

  - [ ] [OPEN] World and runtime model - first-checkpoint working hypothesis
    - [x] Distinguish definition data from runtime instances
    - [x] Use RuntimeInstance, RelationInstance, and WorldState as the current top-level runtime working categories
    - [x] Add DefinitionLink as a provisional definition-layer structure after repeated cross-subject evidence
    - [x] Treat environment as a human-facing concept rather than a single formal data category
    - [ ] Determine whether owner-bound SubobjectInstance needs to remain a distinct primitive
    - [ ] Resolve representative boundary cases across Ability, Modifier, Item, Projectile, Tree, and similar structures
    - [ ] Determine which relationships need stored runtime identity/state versus being derived from other state
    - [ ] Resolve the shape of spatial world data: fields, regions, geometry, graphs, discrete objects, or combinations
    - [ ] Determine how runtime truth differs from player/team-visible information

  - [ ] [OPEN] Property model - first-checkpoint working hypothesis
    - [x] Treat Property as a value query rather than assuming every property is a stored field
    - [x] Separate value-input origin from value-resolution strategy
    - [x] Admit DefinitionData, InstanceState, RelationState, and WorldState as provisional property inputs
    - [x] Distinguish Direct, Derived, and Aggregate as provisional resolution strategies
    - [x] Restrict PropertyContribution to a candidate mechanism for Aggregate properties rather than a universal external-effect model
    - [x] Distinguish current runtime values from maximum/capacity/parameter values
    - [ ] Determine the minimal Property schema shared across representative runtime structures
    - [ ] Determine how aggregate resolution should represent add, multiply, override, ordering, and stacking
    - [ ] Determine how property dependencies form and are evaluated
    - [ ] Determine PropertyContribution activation, targeting, lifetime, and removal semantics

  - [ ] Interaction model
    - [ ] Define a neutral representation of interactions between runtime instances and world state
    - [ ] Determine how source, target selection, conditions, effects, and state/relation changes compose
    - [ ] Test whether attacks, abilities, items, auras, and environmental interactions can share the same primitives

  - [ ] Rule and execution model
    - [ ] Define event, condition, transition, and time-dependent rule primitives only as needed by tested cases
    - [ ] Model multi-phase actions, projectiles, channels, duration, periodic effects, and interruption without mechanic-specific special cases where possible
    - [ ] Keep runtime state representation separate from higher-level design interpretation

  - [ ] Higher-level design analysis built on the data model
    - [ ] Capability and action-space change
    - [ ] Constraints, costs, reliability, and friction
    - [ ] Decision space and trade-offs
    - [ ] Interaction and counterplay
    - [ ] Strength and weakness structure
    - [ ] Identity and strategic function
    - [ ] Strength allocation / power budget as an analytical model
    - [ ] Spatial and temporal advantage
    - [ ] Identify, rename, merge, or remove concepts as evidence demands

- [ ] Systematic case analysis
  - [ ] Individual heroes
  - [ ] Individual items
  - [ ] Individual systems and mechanics
  - [ ] Cross-case comparisons that test and revise the gameplay data model and higher-level analysis
