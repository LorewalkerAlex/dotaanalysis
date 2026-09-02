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
  - [x] Separate verified facts, analytical interpretations, and design-intent hypotheses

- [ ] [ACTIVE] Build the high-level DOTAANALYSIS analysis framework
  - [ ] Hero design framework
    - [ ] Hero base model
      - [ ] Attributes and growth
      - [ ] Movement and positioning parameters
      - [ ] Attack range, attack point, BAT, projectile behavior, and related attack parameters
      - [ ] Cast range, cast point, projectile behavior, and related cast parameters
    - [ ] Skill and kit design
      - [ ] Skill functions and capabilities
      - [ ] Internal kit synergy and dependencies
      - [ ] Costs, restrictions, reliability, and counterplay
    - [ ] Strength and weakness structure
      - [ ] How advantages are allocated
      - [ ] How weaknesses permit extreme strengths
      - [ ] Whether concepts such as power budget are useful explanatory models
    - [ ] Hero identity
      - [ ] Core gameplay behavior
      - [ ] Strategic identity and role
      - [ ] What is identity-defining versus a balance knob
    - [ ] Define a reusable hero analysis format
    - [ ] Validate and revise the framework using representative, deliberately different heroes

  - [ ] Item design framework
    - [ ] Numerical/stat items and value
    - [ ] Functional items that grant new capabilities
    - [ ] Gold cost, slot cost, timing cost, and opportunity cost
    - [ ] Items that amplify strengths versus compensate for weaknesses
    - [ ] Item-based counterplay and response options
    - [ ] Components, build paths, intermediate power, and upgrade structure
    - [ ] Define a reusable item analysis format
    - [ ] Validate and revise the framework using representative items

  - [ ] System design framework
    - [ ] Combat mathematics
      - [ ] Damage and mitigation
      - [ ] Armor and magic resistance
      - [ ] Attack speed, BAT, and temporal scaling
      - [ ] Critical strike, evasion, block, sustain, and related combat rules
    - [ ] Status, control, immunity, dispel, and counter-control rules
    - [ ] Map, terrain, pathing, and spatial structure
    - [ ] Vision, fog, information, and uncertainty
    - [ ] Economy and resource acquisition
    - [ ] Experience and progression
    - [ ] Lanes, creeps, neutral objectives, and map pressure
    - [ ] Time systems and pacing
    - [ ] Environmental and systemic interactions

  - [ ] Cross-cutting design concepts
    - [ ] Strength allocation / power budget as an analytical model
    - [ ] Counterplay
    - [ ] Strength through weakness
    - [ ] Decision space and trade-offs
    - [ ] Spatial and temporal advantage
    - [ ] Friction, reliability, and responsiveness as design variables
    - [ ] Identify, rename, merge, or remove concepts as the evidence demands

- [ ] Systematic case analysis
  - [ ] Individual heroes
  - [ ] Individual items
  - [ ] Individual systems and mechanics
  - [ ] Cross-case comparisons that test and revise the high-level frameworks
