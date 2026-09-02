# DOTAANALYSIS Project

## Purpose

DOTAANALYSIS is a long-running game-design research project that studies Dota 2 in order to extract reusable design insight.

The goal is not to build a Dota 2 strategy guide, encyclopedia, tier list, or balance commentary archive. The goal is to understand how Dota 2 uses rules, numbers, constraints, interactions, timing, space, information, and asymmetry to create meaningful gameplay, then turn that understanding into design knowledge that can transfer to other games.

## Main research areas

The project currently has three broad research areas:

1. **Hero design** — attributes, growth, movement, attack behavior, cast behavior, skills, timings, ranges, animation-related parameters, strengths, weaknesses, identity, kit structure, and other hero-specific design.
2. **Item design** — numerical value, active and passive capabilities, build paths, timing, slot pressure, opportunity cost, hero interaction, counterplay, and how items change a hero's available actions.
3. **System design** — combat math, status and control rules, map and terrain, vision and information, economy, experience, lanes, objectives, time, pacing, environment, and other underlying systems.

These areas are starting points, not permanent taxonomy. The roadmap and knowledge structure may be reorganized when research produces a better model.

## Research direction

The intended progression is broadly:

1. Build high-level analysis frameworks.
2. Test and refine those frameworks with representative cases and counterexamples.
3. Use the refined frameworks to analyze individual heroes, items, and systems systematically.
4. Compare cases across the corpus and revise earlier frameworks when they stop explaining the evidence well.

The project therefore moves from framework to case study and back again. Individual analyses are evidence for improving the larger model, not isolated articles.

## Evidence and claim types

Keep three kinds of claims distinct:

- **Verified fact** — an externally checkable statement about Dota 2, such as a mechanic, parameter, patch behavior, or historical change.
- **Analytical interpretation** — an explanation of what a verified design choice does to gameplay, decisions, incentives, feel, counterplay, or system behavior.
- **Design-intent hypothesis** — a hypothesis about why a designer may have chosen a particular rule or value. Do not present inferred intent as verified fact without direct evidence.

Current or changeable Dota 2 facts must be verified against reliable current sources. Record the relevant version or date when it materially affects the analysis.

## How knowledge should evolve

DOTAANALYSIS is exploratory research. Most research content is deliberately mutable.

Ideas, terminology, categories, frameworks, design patterns, and even previously useful conclusions may be renamed, merged, split, reorganized, or rejected as better evidence appears. A checked roadmap item means that the project currently has a usable result, not that the result is permanently final.

The repository should normally contain the project's **current best understanding**, not a transcript of how every idea evolved. Git history already preserves earlier versions when that history is needed.

## Chat sessions and the repository

ChatGPT sessions are temporary reasoning workspaces for discussion, disagreement, hypothesis formation, examples, counterexamples, research, and refinement.

The GitHub repository is the durable project checkpoint. Because sessions are sequential, the repository must always contain enough structure and state for a fresh session to reconstruct the ongoing research without depending on the previous chat transcript.

`ROADMAP.md` is both the research map and the progress record. `docs/INDEX.md` is the map to durable research knowledge.

## Repository control

The user retains final control over all durable project changes.

Repository reads and analysis may be performed as needed. Any repository mutation requires explicit user approval for the specific proposed change before it is performed. Discussion alone never authorizes persistence.
