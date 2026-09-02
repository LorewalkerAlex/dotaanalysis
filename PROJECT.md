# DOTAANALYSIS Project

## Purpose

DOTAANALYSIS is a long-running game-design research project that studies Dota 2 in order to extract reusable design insight.

The goal is not to build a Dota 2 strategy guide, encyclopedia, tier list, or balance commentary archive. The goal is to understand how Dota 2 represents and combines gameplay objects, properties, relationships, interactions, rules, numbers, timing, space, information, and asymmetry, then turn that understanding into models and design knowledge that can transfer to other games.

The current first-stage goal is to derive a reusable **gameplay data model** from Dota 2: a small set of general structures that can describe representative heroes, items, abilities, modifiers, projectiles, map state, and other gameplay systems without creating a special model for every mechanic. This is a research model for transfer and comparison, not a claim about Valve's internal implementation architecture.

## Research corpus

The project currently draws evidence from three broad content areas:

1. **Hero design** — attributes, growth, movement, attack behavior, cast behavior, skills, timings, ranges, animation-related parameters, strengths, weaknesses, identity, kit structure, and other hero-specific design.
2. **Item design** — numerical value, active and passive capabilities, build paths, timing, slot pressure, opportunity cost, hero interaction, counterplay, and how items change a hero's available actions.
3. **System design** — combat math, status and control rules, map and terrain, vision and information, economy, experience, lanes, objectives, time, pacing, environment, and other underlying systems.

These areas are evidence domains and validation corpora, not necessarily separate top-level data models. The project should prefer shared primitives and composition when one model can explain multiple domains. The roadmap and knowledge structure may be reorganized when research produces a better model.

## Research direction

The intended progression is broadly:

1. Build a working gameplay data model at a structural level before interpreting design quality.
2. Pressure-test and revise the model using deliberately different Dota 2 cases, especially boundary cases that challenge the current abstractions.
3. Extend the model from world/object structure into properties, interactions, rules, and execution only when the existing layer requires it.
4. Use heroes, items, abilities, modifiers, projectiles, map state, and systems as validation evidence rather than assuming each requires a separate framework.
5. Build higher-level design analysis on top of the structural model, including decisions, counterplay, strengths, weaknesses, identity, and other reusable design concepts.
6. Compare cases across the corpus and revise earlier models when they stop explaining the evidence well.

The project therefore moves from model to case study and back again. Individual analyses are evidence for improving the larger model, not isolated articles.

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

The public GitHub repository is the durable project checkpoint and the authoritative published state. Because sessions are sequential, the repository must always contain enough structure and state for a fresh session to reconstruct the ongoing research without depending on the previous chat transcript.

`ROADMAP.md` is both the research map and the progress record. `docs/INDEX.md` is the map to durable research knowledge.

## Repository control and publication model

The user retains final control over all durable project changes.

Repository reads and analysis may be performed as needed. Any repository mutation requires explicit user approval for the specific proposed change before it is performed. Discussion alone never authorizes persistence.

Approved repository changes use the Web Local Development workflow by default. Public GitHub is the durable read baseline and published source of truth; the user's local checkout is the controlled write workspace. Candidate files are delivered as complete artifacts, applied and validated locally, then committed and pushed in a separate publication step.

Once an assistant-directed local apply succeeds, that local checkout is the session-local working state for the approved change. After the user pushes, the public GitHub repository must be re-read and verified before the mutation is considered complete and the published repository becomes the new durable baseline.

Direct GitHub write operations are not a substitute for this local workflow unless the user explicitly changes that rule.
