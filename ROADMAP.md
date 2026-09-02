# DOTAANALYSIS Research Roadmap

This file is both the research map and the project progress record. It is expected to evolve as the research develops.

## Status convention

- `[ ]` — not yet completed.
- `[ ] [ACTIVE]` — the current primary research node. There should normally be only one primary active node because the project is sequential rather than parallel.
- `[ ] [OPEN]` — meaningful work exists, but important questions remain unresolved before the node can be treated as currently usable.
- `[x]` — the node currently has a usable result and the project can progress beyond it. This does **not** mean the result is immutable.

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

  - [ ] [OPEN] World and runtime object model
    - [x] Distinguish definition data from runtime instances
    - [x] Use Object, Relation, and WorldState as the current top-level runtime categories
    - [x] Treat environment as a human-facing concept rather than a single formal data category
    - [ ] Resolve the boundary between independent Object and owner-bound Subobject
    - [ ] Resolve representative boundary cases: Ability, Modifier, Item, Projectile, Tree, and similar objects
    - [ ] Determine which relationships need stored runtime identity/state versus being derived from other state

  - [ ] [OPEN] Property model
    - [x] Treat Property as a value query rather than assuming every property is a stored field
    - [x] Distinguish definition values, stored runtime values, derived values, and aggregate values as the current working sources
    - [x] Represent external property influence provisionally as Contribution rather than mutating base definition data
    - [x] Distinguish current runtime values from maximum/capacity/parameter values
    - [ ] Determine the minimal Property schema shared across representative object types
    - [ ] Determine how aggregate property resolution should represent add, multiply, override, ordering, and stacking
    - [ ] Determine how property dependencies form and are evaluated
    - [ ] Determine Contribution activation, targeting, lifetime, and removal semantics

  - [ ] Interaction model
    - [ ] Define a neutral representation of interactions between runtime objects and world state
    - [ ] Determine how source, target selection, conditions, effects, and state/relation changes compose
    - [ ] Test whether attacks, abilities, items, auras, and environmental interactions can share the same primitives

  - [ ] Rule and execution model
    - [ ] Define event, condition, transition, and time-dependent rule primitives only as needed by tested cases
    - [ ] Model multi-phase actions, projectiles, channels, duration, periodic effects, and interruption without mechanic-specific special cases where possible
    - [ ] Keep runtime state representation separate from higher-level design interpretation

  - [ ] Validation corpus
    - [ ] Heroes and ordinary units
    - [ ] Items, inventories, ownership, and dropped items
    - [ ] Abilities and owner-bound runtime state
    - [ ] Modifiers, auras, and stateful relations
    - [ ] Projectiles and other short-lived spatial objects
    - [ ] Buildings, trees, terrain, spatial fields, and global world state
    - [ ] Combat, progression, economy, vision, and other system-level cases
    - [ ] Use deliberately different and difficult counterexamples to force model revision

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
