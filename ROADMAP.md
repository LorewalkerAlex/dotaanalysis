# DOTAANALYSIS Research Roadmap

This file is both the research map and the project progress record. It is expected to evolve as concrete design research changes what is worth studying next.

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

- [x] Reset the research direction from structure-first abstraction to case-first design analysis
  - [x] Treat concrete Dota 2 designs as the primary research units
  - [x] Make reusable design insight, not ontology completeness, the main research output
  - [x] Preserve only the factual detail needed to support design reasoning
  - [x] Require case conclusions to connect design choices to behavior, decisions, trade-offs, counterplay, or pacing
  - [x] Derive cross-case concepts only after repeated evidence supports them
  - [x] Establish the case-analysis method in `docs/methods/design-case-analysis.md`

- [ ] [ACTIVE] Hero design case studies
  - [ ] Select and complete the first representative hero case
    - [ ] Verify the current hero facts and version context needed by the analysis
    - [ ] Analyze baseline attributes and combat chassis
    - [ ] Analyze growth and progression
    - [ ] Analyze each ability as an individual design
    - [ ] Analyze the ability kit as a combined capability set
    - [ ] Analyze the behavior the full design encourages
    - [ ] Analyze strengths, weaknesses, reliability, commitment, and counterplay
    - [ ] Record item dependencies or item-enabled behavior where they materially shape the hero
    - [ ] Extract transferable design lessons and explicit uncertainties
  - [ ] Build a deliberately varied initial hero cohort
    - [ ] Include heroes with meaningfully different ranges, durability, mobility, resource models, timing curves, and combat roles
    - [ ] Prefer contrast over alphabetical or popularity-based ordering
  - [ ] Run the first cross-hero synthesis after a small varied cohort is available
    - [ ] Compare how baseline attributes create behavior before abilities are considered
    - [ ] Compare growth curves and power timing
    - [ ] Compare capability allocation across ability kits
    - [ ] Compare reliability, commitment, opportunity cost, and counterplay
    - [ ] Identify candidate design principles that survive multiple heroes

- [ ] [OPEN] Equipment and item design case studies
  - [ ] Study representative stat-focused equipment
  - [ ] Study representative active capability items
  - [ ] Study defensive and counterplay items
  - [ ] Study mobility and positioning items
  - [ ] Study consumables and limited-charge tools
  - [ ] Study neutral items and other nonstandard acquisition models
  - [ ] Compare price, timing, build path, slot pressure, activation constraints, and hero interaction
  - [ ] Extract reusable principles about equipment changing action space and strategic options

- [ ] [OPEN] Lane, creep, neutral, building, and objective design
  - [ ] Lane wave composition and spawn rhythm
  - [ ] Creep aggro and lane equilibrium
  - [ ] Gold and experience distribution around lane units
  - [ ] Neutral camps, pulling, stacking, farming routes, and contestability
  - [ ] Towers, barracks, base progression, and structural pressure
  - [ ] Roshan and Tormentor as contested timing objectives
  - [ ] Runes and other map-spawned resources
  - [ ] Extract reusable principles about pressure, resource routing, objectives, and match pacing

- [ ] [OPEN] Economy and progression design
  - [ ] Gold sources, loss, reliability, and spending decisions
  - [ ] Experience distribution and level timing
  - [ ] Death cost, respawn, and buyback
  - [ ] Farming efficiency, acceleration, recovery, and comeback mechanisms
  - [ ] Team versus individual resource allocation
  - [ ] Extract reusable principles about pacing, snowball control, recovery, and opportunity cost

- [ ] [OPEN] Map, terrain, movement, and spatial design
  - [ ] High ground, ramps, cliffs, trees, paths, and chokepoints
  - [ ] River, lanes, jungle regions, bases, pits, and objective placement
  - [ ] Mobility rules and traversal exceptions
  - [ ] How geometry changes access, safety, commitment, pursuit, escape, and formation
  - [ ] Extract reusable principles about spatial pressure and strategic geography

- [ ] [OPEN] Vision and information design
  - [ ] Day/night vision differences
  - [ ] Fog of War and shared team information
  - [ ] Observer and Sentry Wards, True Sight, and detection
  - [ ] High-ground and terrain-based information asymmetry
  - [ ] Scan, hidden timers, uncertain information, and information-gathering tools
  - [ ] Extract reusable principles about uncertainty, scouting, risk, deception, and information cost

- [ ] [OPEN] Combat, status, and systemic rule design
  - [ ] Damage, armor, magic resistance, and mitigation
  - [ ] Attack behavior, projectiles, range, timing, and animation commitments
  - [ ] Stuns, slows, silence, break, dispel, immunity, and other status rules
  - [ ] Regeneration, barriers, death, and survival systems
  - [ ] Interaction rules that materially shape hero and item counterplay
  - [ ] Extract reusable principles about reliability, response windows, commitment, and systemic counterplay

- [ ] [OPEN] Cross-case design principles
  - [ ] Maintain principles only when supported by multiple concrete cases
  - [ ] Strength allocation and power budget across magnitude, access, reliability, timing, space, cost, and counterplay
  - [ ] Capability and action-space expansion
  - [ ] Constraints, friction, commitment, and opportunity cost
  - [ ] Decision quality and meaningful trade-offs
  - [ ] Counterplay as part of power design rather than an afterthought
  - [ ] Information as a gameplay resource
  - [ ] Identity emerging from aligned strengths, weaknesses, and behavior
  - [ ] Spatial and temporal advantage
  - [ ] Revise, split, merge, or discard principles when later cases contradict them

## Current next action

Begin the first Hero design case study. Choose a representative first hero deliberately for analytical clarity, then apply the case method in `docs/methods/design-case-analysis.md`. Do not create a new structural data model before the case produces an actual design question that requires one.
