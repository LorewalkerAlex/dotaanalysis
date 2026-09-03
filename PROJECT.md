# DOTAANALYSIS Project

## Purpose

DOTAANALYSIS is a long-running game-design research project that studies Dota 2 in order to extract reusable design insight.

The goal is not to build a Dota 2 strategy guide, encyclopedia, tier list, balance archive, or implementation model. The goal is to understand how concrete Dota 2 designs create decisions, trade-offs, counterplay, asymmetry, identity, feel, pacing, spatial pressure, information pressure, and systemic depth, then turn that understanding into principles that can inform other games.

The project is **case-first**. It studies specific heroes, items, lane and neutral systems, objectives, economy, terrain, vision, combat rules, and other concrete designs before attempting broad synthesis. Abstract terminology is useful only when repeated cases show that it explains something designers can actually use.

## Core research question

For every case, the project should ultimately answer:

> What design choices produce this gameplay behavior, why do those choices create meaningful player decisions and counterplay, and what can another designer reuse from the result?

Facts are necessary evidence, but factual completeness is not the end product. A case is not complete merely because its parameters have been cataloged.

## Research domains

The project currently studies the following broad design domains.

### Hero design

Study heroes one by one. Important dimensions include:

- starting attributes and other baseline combat parameters;
- attribute growth and other progression curves;
- movement, attack, cast, range, timing, animation, and resource behavior;
- each ability as an individual design;
- the ability kit as a combined capability set;
- innate abilities, talents, upgrades, and other progression choices where relevant;
- the behavior the full kit encourages in lane, farming, skirmishing, team fights, pursuit, retreat, initiation, protection, positioning, and target selection;
- item dependencies and item-enabled behavior where they materially shape the hero;
- strengths, weaknesses, reliability, opportunity costs, commitment, counterplay, and identity;
- transferable design lessons supported by the case.

The purpose is not to force every hero into one fixed template. The shared dimensions exist to support comparison; each case should spend the most attention on the design decisions that actually explain that hero.

### Equipment and item design

Study purchasable equipment, consumables, neutral items, upgrades, and other item-like tools as concrete cases. Important questions include:

- what new capability or numerical advantage the item provides;
- price, build path, timing, slot pressure, charges, cooldowns, and other costs;
- whether the item strengthens an existing behavior or enables a new one;
- which heroes or situations can exploit it and which cannot;
- how opponents identify, avoid, punish, or counter it;
- how item availability changes strategic and tactical decision space;
- what design principle can be transferred to other equipment systems.

### Lane, creep, neutral, building, and objective design

Study lane waves, creep composition, aggro, bounty, experience, neutral camps, stacking and pulling, towers, barracks, Roshan, Tormentor, runes, and other objective structures in terms of the behavior they create.

Questions should focus on resource routes, lane equilibrium, pressure, timing windows, risk, map movement, contestability, recovery, snowball control, and how local rules combine into match pacing.

### Economy and progression

Study gold, experience, level growth, death costs, buyback, rewards, farming sources, comeback and acceleration mechanisms, and other progression rules as decision systems rather than isolated formulas.

### Map, terrain, and movement

Study terrain height, ramps, trees, paths, chokepoints, rivers, bases, pits, travel routes, mobility rules, and spatial objectives by asking how geometry changes safety, commitment, pursuit, escape, formation, access, and strategic value.

### Vision and information

Study day/night vision, Fog of War, wards, True Sight, high-ground information, Scan, hidden information, uncertain timers, and other information systems by asking what players know, when they know it, what information costs, and how uncertainty creates decisions.

### Combat, status, and systemic rules

Study damage, armor, resistance, control, dispels, immunity, projectiles, attack rules, status interactions, death, regeneration, and similar systems when they materially explain design behavior across cases.

Additional domains may be introduced when concrete cases show that the current research map is missing an important design question.

## Research method

The default research loop is:

```text
Case
  -> Verify current facts
  -> Explain player behavior
  -> Identify constraints and trade-offs
  -> Identify counterplay and failure modes
  -> Form transferable design lessons
  -> Compare against other cases
  -> Revise the lesson when evidence disagrees
```

The detailed case method lives in `docs/methods/design-case-analysis.md`.

Cross-case synthesis should happen after enough deliberately different cases exist to support it. Do not create a new framework merely because one case admits a neat abstraction. A useful principle should explain repeated design evidence and help answer a design question.

## Evidence and claim types

Keep three kinds of claims distinct:

- **Verified fact** - an externally checkable statement about Dota 2, such as a parameter, mechanic, patch behavior, or historical change.
- **Analytical interpretation** - an explanation of what a verified design choice does to gameplay, decisions, incentives, feel, pacing, reliability, or counterplay.
- **Design-intent hypothesis** - a hypothesis about why a designer may have chosen a particular rule or value. Do not present inferred intent as verified fact without direct evidence.

Current or changeable Dota 2 facts must be verified against reliable current sources. Record the relevant version or observation date when it materially affects the analysis.

## What counts as useful research output

Durable research should preferentially preserve:

1. the minimum factual baseline needed to understand a design;
2. the causal explanation linking design choices to player behavior;
3. the trade-offs and counterplay that make the design sustainable;
4. comparisons that reveal why superficially similar designs behave differently;
5. transferable design principles stated clearly enough to test against later cases.

Avoid accumulating structure catalogs, exhaustive parameter inventories, or abstract type systems unless a concrete design question actually requires them.

## How knowledge should evolve

DOTAANALYSIS is exploratory research. Case conclusions, terminology, design patterns, and higher-level principles are mutable.

When later cases overturn an earlier lesson, update the authoritative document to the project's current best understanding. Git history preserves previous versions; the main knowledge base should not become an archive of superseded models.

A principle should become more precise as counterexamples accumulate. Prefer a narrower principle with clear conditions over a universal slogan that cannot survive comparison.

## Chat sessions and the repository

ChatGPT sessions are temporary reasoning workspaces for discussion, disagreement, source checking, case analysis, comparison, and hypothesis formation.

The public GitHub repository is the durable project checkpoint and authoritative published state. Because sessions are sequential, the repository must always contain enough state for a fresh session to reconstruct the research direction and continue without the previous chat transcript.

`ROADMAP.md` is both the research map and the progress record. `docs/INDEX.md` is the map to durable research knowledge.

## Repository control and publication model

The user retains final control over all durable project changes.

Repository reads and analysis may be performed as needed. Any repository mutation requires explicit user approval for the specific proposed change before it is performed. Discussion alone never authorizes persistence.

Approved repository changes use the Web Local Development workflow by default. Public GitHub is the durable read baseline and published source of truth; the user's local checkout is the controlled write workspace. Candidate files are delivered as complete artifacts, applied and validated locally, then committed and pushed in a separate publication step.

Once an assistant-directed local apply succeeds, that local checkout is the session-local working state for the approved change. After the user pushes, the public GitHub repository must be re-read and verified before the mutation is considered complete and the published repository becomes the new durable baseline.

Direct GitHub write operations are not a substitute for this local workflow unless the user explicitly changes that rule.
