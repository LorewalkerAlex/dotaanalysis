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
  - [x] Define the default per-hero analysis sequence
    1. Verify the current combat chassis and reusable progression baseline.
    2. Identify the hero's defining mechanic or design problem before mechanically walking Q/W/E/R.
    3. Follow the causal relationships among abilities and other mechanics in the order that best explains the kit.
    4. Preserve historically meaningful design branches rather than patch chronology.
    5. Record Innate, Facet, Talent, Shard, Scepter, and other progression branches when they change magnitude, frequency, reliability, access, coverage, commitment, or action space.
    6. Reconstruct whole-kit behavior across lane, farming, skirmishing, team fights, pursuit, retreat, positioning, target selection, and resource loops where relevant.
    7. Identify costs, failure modes, opportunity costs, commitment, and opponent counterplay.
    8. Close with a compact design identity, core mechanical relationships, main costs/counterplay, case-level candidate lessons, and unresolved comparison questions.
  - [ ] Complete one durable first pass for every playable hero
    - [x] Use Dota's default hero-grid ordering rather than research-defined design groups: Strength -> Agility -> Intelligence -> Universal, alphabetical within each group
    - [x] Treat the current ordering as an operational roster snapshot, not a design classification; as the live roster changes, insert new heroes alphabetically and move heroes if their attribute group changes
    - [ ] Strength heroes (36)
      - [ ] Alchemist
      - [x] Axe - `docs/heroes/axe.md`
      - [ ] Bristleback
      - [ ] Centaur Warrunner
      - [ ] Chaos Knight
      - [ ] Clockwerk
      - [ ] Dawnbreaker
      - [ ] Doom
      - [ ] Dragon Knight
      - [ ] Earth Spirit
      - [ ] Earthshaker
      - [ ] Elder Titan
      - [ ] Huskar
      - [ ] Kunkka
      - [ ] Largo
      - [ ] Legion Commander
      - [ ] Lifestealer
      - [ ] Lycan
      - [ ] Mars
      - [ ] Night Stalker
      - [ ] Ogre Magi
      - [ ] Omniknight
      - [ ] Phoenix
      - [ ] Primal Beast
      - [ ] Pudge
      - [ ] Slardar
      - [ ] Spirit Breaker
      - [ ] Sven
      - [ ] Tidehunter
      - [ ] Timbersaw
      - [ ] Tiny
      - [ ] Treant Protector
      - [ ] Tusk
      - [ ] Underlord
      - [ ] Undying
      - [ ] Wraith King
    - [ ] Agility heroes (35)
      - [ ] Anti-Mage
      - [ ] Bloodseeker
      - [ ] Bounty Hunter
      - [ ] Broodmother
      - [ ] Clinkz
      - [ ] Drow Ranger
      - [ ] Ember Spirit
      - [ ] Faceless Void
      - [ ] Gyrocopter
      - [ ] Hoodwink
      - [x] Juggernaut - `docs/heroes/juggernaut.md`
      - [ ] Kez
      - [ ] Lone Druid
      - [ ] Luna
      - [ ] Medusa
      - [ ] Meepo
      - [ ] Mirana
      - [ ] Monkey King
      - [ ] Morphling
      - [ ] Naga Siren
      - [ ] Phantom Assassin
      - [ ] Phantom Lancer
      - [ ] Razor
      - [ ] Riki
      - [ ] Shadow Fiend
      - [ ] Slark
      - [ ] Sniper
      - [ ] Spectre
      - [ ] Templar Assassin
      - [ ] Terrorblade
      - [ ] Troll Warlord
      - [ ] Ursa
      - [ ] Vengeful Spirit
      - [ ] Viper
      - [ ] Weaver
    - [ ] Intelligence heroes (34)
      - [ ] Ancient Apparition
      - [x] Chen - `docs/heroes/chen.md`
      - [x] Crystal Maiden - `docs/heroes/crystal-maiden.md`
      - [ ] Dark Seer
      - [ ] Dark Willow
      - [ ] Disruptor
      - [ ] Enchantress
      - [ ] Grimstroke
      - [ ] Invoker
      - [ ] Jakiro
      - [ ] Keeper of the Light
      - [ ] Leshrac
      - [ ] Lich
      - [ ] Lina
      - [ ] Lion
      - [ ] Muerta
      - [ ] Necrophos
      - [ ] Oracle
      - [ ] Outworld Destroyer
      - [x] Puck - `docs/heroes/puck.md`
      - [ ] Pugna
      - [ ] Queen of Pain
      - [ ] Ringmaster
      - [ ] Rubick
      - [ ] Shadow Demon
      - [ ] Shadow Shaman
      - [ ] Silencer
      - [ ] Skywrath Mage
      - [x] Storm Spirit - `docs/heroes/storm-spirit.md`
      - [ ] Tinker
      - [ ] Warlock
      - [ ] Winter Wyvern
      - [ ] Witch Doctor
      - [ ] Zeus
    - [ ] Universal heroes (22)
      - [ ] Abaddon
      - [ ] Arc Warden
      - [ ] Bane
      - [ ] Batrider
      - [ ] Beastmaster
      - [ ] Brewmaster
      - [ ] Dazzle
      - [ ] Death Prophet
      - [ ] Enigma
      - [ ] Io
      - [ ] Magnus
      - [ ] Marci
      - [ ] Nature's Prophet
      - [ ] Nyx Assassin
      - [ ] Pangolier
      - [ ] Sand King
      - [ ] Snapfire
      - [ ] Techies
      - [ ] Venomancer
      - [ ] Visage
      - [ ] Void Spirit
      - [ ] Windranger
  - [ ] Refresh the factual baseline for roster-wide comparison after every hero has a first durable pass
    - [ ] Confirm the then-current playable roster and attribute grouping
    - [ ] Refresh materially stale current mechanics and comparison-critical numbers in older hero cases
    - [ ] Record one shared comparison reference patch/version for the synthesis pass
  - [ ] Run full cross-hero synthesis after roster-wide first-pass coverage and factual refresh
    - [ ] Compare baseline attributes, combat chassis, ranges, mobility, durability, and timing commitments
    - [ ] Compare growth curves, resource models, permanent progression, access progression, and power timing
    - [ ] Compare how heroes construct action space through fixed abilities, attacks, movement, units, transformations, borrowed capabilities, and upgrades
    - [ ] Compare how abilities connect to or reject public combat systems such as attacks, damage, status, movement, death, healing, and unit control
    - [ ] Compare spatial access, positioning requirements, engagement depth, escape, formation, and other commitment structures
    - [ ] Compare reliability, flexibility, execution burden, uncertainty, opportunity cost, and failure modes
    - [ ] Compare opponent counterplay and which weaknesses are deliberately left unsolved inside the hero kit
    - [ ] Compare where power is allocated across magnitude, access, reliability, timing, space, cost, flexibility, and counterplay
    - [ ] Identify candidate principles, then actively test them against counterexamples across the full roster
    - [ ] Produce a gap map of questions that remain unresolved after roster-wide comparison

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

Study Alchemist, the first unfinished hero in the current Strength-group alphabetical order. Use the standard per-hero analysis sequence: verify the current chassis, identify the defining mechanic, follow causal kit relationships, preserve meaningful historical branches and progression upgrades, reconstruct whole-kit behavior, identify costs and counterplay, then close with compact case-level lessons. After Alchemist is durably recorded, continue to the next unfinished hero in the default attribute-group/alphabetical checklist, skipping heroes whose durable first pass is already complete.
