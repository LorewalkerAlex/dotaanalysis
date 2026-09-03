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
  - [x] Make reusable design insight, not ontology completeness, the main research goal
  - [x] Preserve reusable factual baselines and key design-branch values without turning the repository into a patch-by-patch balance archive
  - [x] Require case conclusions to connect design choices to behavior, decisions, trade-offs, counterplay, or pacing
  - [x] Derive cross-case concepts only after repeated evidence supports them
  - [x] Establish and calibrate the case-analysis method in `docs/methods/design-case-analysis.md`

- [ ] [ACTIVE] Hero design case studies
  - [x] Establish the durable hero-case format
    - [x] Use one durable document per hero
    - [x] Make the case fact-rich and analysis-light
    - [x] Preserve comparison-ready current baseline numbers
    - [x] Organize meaningful historical mechanics as design branches rather than patch chronology
    - [x] Preserve removed abilities, Innates, Facets, Shards, Scepters, or talents when they represent distinct design solutions
    - [x] Keep detailed equipment analysis out of the hero case unless inseparable from understanding the hero
  - [x] Complete Axe as the first representative hero case
    - [x] Record current combat chassis and key progression values
    - [x] Record Berserker's Call design branches
    - [x] Record Battle Hunger design branches
    - [x] Record Counter Helix design branches
    - [x] Record Culling Blade design branches
    - [x] Record One Man Army and removed Coat of Blood
    - [x] Preserve compact kit relationships and candidate lessons
  - [x] Complete Juggernaut as the second contrasting hero case
    - [x] Record current combat chassis and key progression values
    - [x] Record Bladeform and removed Duelist
    - [x] Record Blade Fury integration branches
    - [x] Record Healing Ward branches
    - [x] Record Blade Dance progression branches
    - [x] Record old and current Omnislash models plus Swiftslash
    - [x] Preserve compact kit relationships and candidate lessons
  - [ ] Build a deliberately varied initial hero cohort
    - [ ] Select a third hero that contrasts materially with Axe and Juggernaut rather than another similar melee physical core
    - [ ] Include heroes with meaningfully different ranges, durability, mobility, resource models, timing curves, control models, and combat roles
    - [ ] Prefer contrast over alphabetical or popularity-based ordering
    - [ ] Continue using one hero per durable document with reusable numerical facts and design branches
  - [ ] Run the first cross-hero synthesis after a small varied cohort is available
    - [ ] Compare baseline attributes and combat chassis
    - [ ] Compare growth curves and power timing
    - [ ] Compare how abilities connect to or reject public combat systems such as attacks, damage, status, and movement
    - [ ] Compare reliability, commitment, opportunity cost, and counterplay
    - [ ] Identify candidate design principles that survive multiple contrasting heroes

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

Select and study a third hero that deliberately contrasts with both Axe and Juggernaut. Prefer a case that expands the sample beyond melee physical combat - for example a ranged spellcaster, support/controller, summoner, or mobility-centric hero. Build the case as one fact-rich durable hero document, preserve meaningful historical design branches, keep analysis compact, and defer cross-hero synthesis until the cohort is more varied.
