# Design Case Analysis Method

**Status:** Current working method

This document defines how DOTAANALYSIS studies concrete Dota 2 designs and stores durable evidence for later comparison and reuse.

The method is intentionally **case-first**. A hero, item, lane rule, neutral camp, objective, map feature, vision rule, or combat system is valuable because of the behavior and decisions it creates, not because it can be classified into a complete abstract schema.

## Core rule

Research discussion may be analysis-heavy, but the durable case record should normally be **fact-rich and analysis-light**.

The working loop is:

```text
Verified design facts
    -> player-facing behavior
    -> constraints and costs
    -> decisions and trade-offs
    -> counterplay and failure modes
    -> identity / pacing / strategic function
    -> transferable design lessons
```

The repository should preserve enough verified facts and key numbers that later numerical analysis, comparison, or reinterpretation does not require re-querying basic information. It should not preserve every intermediate argument from the chat.

## Evidence discipline

Keep three claim types separate:

- **Verified fact** - externally checkable current or historical Dota 2 information.
- **Analytical interpretation** - what a verified design choice does to gameplay and decisions.
- **Design-intent hypothesis** - a hypothesis about why a designer chose that solution.

For current mechanics, numbers, maps, heroes, items, or other changeable facts, record a source and enough patch/version context to identify the factual reference state.

Historical evidence is organized by **design branch**, not by patch chronology. Version numbers and dates are supporting evidence only; they are not the primary structure of a case.

Do not infer implementation architecture or designer intent from observable behavior alone.

## What durable case files should preserve

Durable case files should preferentially preserve:

1. current baseline values that are likely to be compared later;
2. the defining rules and key values of historically meaningful design branches;
3. deleted abilities or upgrades when they represent a distinct design solution;
4. important targeting, range, timing, cost, damage/heal, scaling, immunity, dispel, death, attack, and trigger rules;
5. talent, innate, Shard, Scepter, or similar upgrades when they materially change a design branch;
6. short analytical notes explaining why a branch is interesting;
7. a compact whole-case identity and a few candidate lessons.

Do **not** record every balance-only number change. A sequence such as `100 -> 105 -> 100` is normally noise unless the magnitude or relationship changed the ability's use. When a historical branch matters, record a representative or mature set of parameters sufficient to understand and compare the branch.

## General case workflow

### 1. Define the concrete case

Start with the hero, item, rule, map feature, or other concrete design being studied. Do not begin by deciding which abstract categories it must populate.

### 2. Capture the reusable factual baseline

Collect the current values that are likely to matter for later numerical or mechanical comparison. This may include:

- attributes and growth;
- health, mana, regeneration, armor, resistance;
- movement and attack chassis;
- range, area, cast point, attack point, BAT, projectile behavior;
- damage, heal, threshold, duration, cooldown, cost;
- trigger probability or trigger count;
- targeting, dispel, immunity, death, attack, and status interactions;
- upgrade values and progression rules.

The goal is not encyclopedic completeness. The goal is to avoid repeatedly re-querying basic facts that are predictably useful to later design work.

### 3. Identify design branches

For each important ability or system, identify the distinct designs that have actually existed.

A **design branch** is a materially different solution, such as:

- random proc versus deterministic accumulation;
- fixed spell damage versus attack-speed-scaled spell damage;
- a special state that excludes normal attacks versus one that reintegrates attacks;
- a single-target effect versus an area effect;
- an ordinary damage rule versus an alternate death rule;
- an upgrade that increases magnitude versus one that adds a new action pattern.

Do not structure the case as a patch timeline. Record the branch, its defining rules and key numbers, and whether it is current or historical/removed.

### 4. Preserve deleted designs when they are informative

A removed ability, facet, innate, Shard, Scepter effect, or other mechanic remains part of the research corpus if it was a meaningful design solution.

If a removed mechanic later reappears in another upgrade slot or ability, record that relationship as a design connection rather than as a chronological patch log.

### 5. Keep analysis compact

For each branch, a short note should normally be enough to capture:

- the behavior it encourages;
- the main strength/cost relationship;
- the counterplay it creates or removes;
- the design question it helps answer.

Long chat reasoning does not need to be copied into the repository when the underlying facts are preserved well enough to reproduce the reasoning later.

### 6. Identify kit/system relationships

Record causal connections that matter, especially when:

- one ability creates the condition another ability needs;
- one ability pays for the risk created by another;
- multiple abilities share one growth resource;
- an upgrade reconnects a secondary mechanic to the character's core action;
- a weakness is deliberately left to another system rather than solved internally.

Do not treat simple thematic similarity or two abilities both dealing damage as meaningful synergy by itself.

### 7. Close with a compact case summary

End with:

- the design identity;
- the most important recurring behavior;
- the main counterplay/cost structure;
- a small number of candidate transferable lessons;
- uncertainties that later cases may resolve.

Candidate lessons remain case-level until multiple deliberately varied cases support them.

## Hero case guide

### One hero, one durable case document

Each hero should normally have one durable Markdown case file containing the reusable factual baseline, design branches, deleted abilities, compact analysis, and case summary.

Do not split one hero into separate fact, analysis, history, Shard, Scepter, or talent files unless the single file becomes genuinely unmanageable.

### Baseline combat chassis

Preserve a compact current table with the values most likely to matter later, normally including:

- primary attribute;
- starting STR/AGI/INT and growth;
- starting health and mana when available;
- health and mana regeneration when useful;
- starting armor;
- starting attack damage;
- melee/ranged and attack range;
- base attack speed and BAT;
- attack point and backswing where useful;
- movement speed and turn rate;
- day/night vision.

Record only additional baseline parameters when they explain a real design feature.

### Growth and progression

Preserve growth facts that change what the hero can do or that are likely to support later numerical comparison:

- attribute growth;
- ability-level scaling;
- thresholds, frequency, radius, or duration progression;
- talents;
- hero-level scaling;
- permanent growth mechanics;
- Shard/Scepter/Innate progression when relevant.

Focus analysis on whether progression changes magnitude, frequency, reliability, access, coverage, commitment, or action space.

### Individual abilities and design branches

For each important ability, normally record:

1. **Current factual baseline** - current defining rules and key values.
2. **Historical design branches** - distinct mechanisms that materially changed how the ability worked.
3. **Upgrade branches** - Talent, Shard, Scepter, Facet, Innate, or other effects that substantially changed the ability.
4. **Compact design note** - a few sentences at most.

Put an upgrade under the ability it extends when that is the clearest representation. If an upgrade creates a genuinely separate ability such as Swiftslash, give that ability its own section inside the same hero document.

### Deleted abilities

Deleted abilities are recorded in the same hero document when they represent a distinct design solution. Mark them clearly as historical/removed and preserve their defining mechanics and key values.

### Kit design

Keep this section compact. Record the causal relationships among abilities and the most important capability gaps. Detailed item analysis is deferred to the equipment phase unless an item interaction is inseparable from understanding the hero's design.

### Hero conclusion

End with:

- design identity;
- core mechanical relationships;
- main costs/counterplay;
- a few case-supported design lessons;
- unresolved comparison questions.

## Equipment and item case guide

For equipment or other items, preserve the values needed for later comparison while focusing analysis on:

- acquisition price and timing;
- build path and intermediate value;
- slot pressure and opportunity cost;
- passive numerical value;
- active or passive capability changes;
- cooldown, charge, targeting, duration, and reliability;
- whether the item amplifies, repairs, or transforms a hero's behavior;
- which opponents or situations increase or reduce its value;
- what counterplay becomes available after the item is revealed;
- whether the item creates a strategic timing window.

## System case guide

For lane, creep, economy, objective, terrain, vision, combat, or other systemic rules:

1. preserve the rules and values needed for later comparison;
2. identify who makes decisions because of them;
3. identify the resource, spatial, temporal, or informational pressure created;
4. identify how players can manipulate or contest the rule;
5. connect the local rule to match pacing and broader strategy;
6. preserve meaningful alternative historical designs when they illuminate the design space;
7. extract only compact candidate lessons until multiple cases support synthesis.

## Cross-case synthesis

Do not synthesize after every case.

After a deliberately varied group exists, compare the stored factual records and ask which patterns actually survive contrast. Candidate synthesis topics include:

- strength allocation and power budget;
- capability versus numerical magnitude;
- growth and timing curves;
- reliability versus upside;
- commitment and escape;
- range and spatial control;
- opportunity cost;
- information and uncertainty;
- counterplay;
- identity through aligned strengths and weaknesses;
- how optional upgrades change action space.

A cross-case principle should name both the repeated pattern and the cases that challenge its limits.

## Anti-patterns for this project

Avoid these research failure modes:

- building a complete ontology before asking a design question;
- storing a patch-by-patch chronology as if it were design analysis;
- omitting reusable numerical facts so that later comparison requires fresh lookup;
- preserving every minor balance-only number change;
- copying long chat analysis when a shorter note plus good facts is enough;
- treating a role label as a design explanation;
- inferring designer intent from mechanics alone;
- promoting a pattern from one or two convenient cases;
- splitting one hero across many files without a clear retrieval benefit.

## Success condition

A successful durable case should let a future session recover the important design facts, compare the case numerically and mechanically with other cases, and reconstruct or improve the analysis without needing the original chat transcript.
