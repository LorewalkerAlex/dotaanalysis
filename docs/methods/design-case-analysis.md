# Design Case Analysis Method

**Status:** Current working method

This document defines how DOTAANALYSIS studies concrete Dota 2 designs in order to extract reusable game-design insight.

The method is intentionally **case-first**. A hero, item, lane rule, neutral camp, objective, map feature, vision rule, or combat system is valuable because of the behavior and decisions it creates, not because it can be classified into a complete abstract schema.

## Core rule

Every substantial case should move from facts to design consequences:

```text
Verified design facts
    -> player-facing behavior
    -> constraints and costs
    -> decisions and trade-offs
    -> counterplay and failure modes
    -> identity / pacing / strategic function
    -> transferable design lessons
```

If a research pass ends with only a parameter inventory, taxonomy, or data representation, it is incomplete.

## Evidence discipline

Keep three claim types separate:

- **Verified fact** - externally checkable current or historical Dota 2 information.
- **Analytical interpretation** - what a verified design choice does to gameplay and decisions.
- **Design-intent hypothesis** - a hypothesis about why a designer chose that solution.

For current mechanics, numbers, patches, maps, heroes, items, or other changeable facts, record a source and relevant version/date context.

Do not infer implementation architecture from observable behavior.

## General case workflow

### 1. Define the design question

Start with the concrete case and ask what is worth explaining.

Examples of useful questions:

- Why does this hero want to fight at this distance?
- Why is this powerful ability allowed to be so strong?
- Why does this item change a hero's behavior rather than merely increase numbers?
- Why does this lane rule create pressure or equilibrium?
- Why does this terrain feature make one position valuable?
- Why does this information rule create uncertainty rather than frustration?

Do not begin by deciding which abstract categories the case must populate.

### 2. Establish the minimum factual baseline

Collect the facts required to understand the design question. This may include numbers, timing, ranges, costs, targeting rules, progression, acquisition conditions, map placement, or historical changes.

Be complete enough to support the analysis, but avoid turning the case into an encyclopedia entry.

### 3. Explain behavior

Translate the rules into what players actually tend or are incentivized to do.

Useful dimensions include:

- preferred distance and positioning;
- target selection;
- initiation, pursuit, retreat, protection, farming, pushing, or scouting behavior;
- resource spending and conservation;
- timing windows;
- risk exposure and commitment;
- dependence on teammates, enemies, terrain, vision, or items;
- how behavior changes when the case is ahead, behind, safe, threatened, or missing key resources.

Behavior is the bridge between raw mechanics and design insight.

### 4. Identify strength allocation

Do not reduce power to damage or durability. Ask where the design places strength and where it withholds it.

Candidate dimensions include:

- magnitude;
- capability - what becomes possible;
- access conditions;
- frequency and uptime;
- resource cost;
- reliability;
- range and spatial access;
- timing and scaling;
- information advantage;
- commitment and exposure;
- flexibility;
- opportunity cost;
- dependence on setup or allies;
- opponent response windows.

The list is a diagnostic aid, not a required universal framework.

### 5. Identify decisions and trade-offs

Ask what meaningful choices the design creates.

A useful decision normally has competing consequences. Examples include spending versus saving, damage versus safety, farming versus pressure, entering versus holding position, using a cooldown now versus preserving it, buying immediate tempo versus scaling, or revealing information in exchange for an objective.

If one option dominates without meaningful context, investigate whether the interesting design lies somewhere else.

### 6. Identify counterplay and failure modes

Treat counterplay as part of the design's power structure.

Ask:

- What can the opponent see or predict?
- What response time exists?
- Can the effect miss, be interrupted, be dispelled, be outranged, be kited, be baited, or be played around spatially?
- What resources must the opponent spend to answer it?
- What happens when the user commits at the wrong time?
- Which weaknesses are produced by the same rule that creates the strength?

Prefer weaknesses that are structurally connected to the strength over arbitrary penalties added afterward.

### 7. State the design identity

Summarize the behavior that the complete design repeatedly rewards.

Identity should emerge from aligned mechanics, incentives, strengths, weaknesses, and constraints. Avoid relying only on theme, lore, role labels, or player reputation.

### 8. Extract transferable lessons

End with a small number of lessons that another designer could test or use.

A strong lesson should:

- be more general than the specific Dota case;
- name the conditions under which it applies;
- explain a causal relationship rather than merely praise the design;
- preserve relevant trade-offs and failure modes;
- be falsifiable by later cases.

Avoid empty slogans such as "make every choice meaningful" unless the case explains a concrete mechanism for doing so.

### 9. Record uncertainties and counterexamples

State what the case does not establish.

If a conclusion depends on role, skill bracket, patch context, team composition, player knowledge, or another condition, record it. Later cases should be allowed to narrow or overturn the lesson.

## Hero case guide

A hero analysis should normally consider the following areas, while spending detail according to the hero rather than mechanically filling every heading.

### Baseline attributes and combat chassis

Consider:

- primary attribute and starting attributes;
- attribute growth;
- health, mana, armor, resistance, regeneration;
- movement speed and turning;
- melee/ranged attack behavior;
- attack range, attack timing, BAT, projectile behavior, acquisition range;
- vision and other baseline parameters when they materially affect behavior.

Ask what the hero already wants to do **before** considering the active skill kit.

### Growth and progression

Consider:

- attribute growth;
- ability-level scaling;
- hero-level scaling;
- talent and upgrade choices;
- item-dependent scaling;
- power spikes, plateaus, and late-game transformations.

Focus on how the hero's available behavior changes over time, not merely whether the numbers increase.

### Individual ability design

For each important ability, examine the relevant combination of:

- capability provided;
- target and targeting method;
- magnitude;
- range and area;
- cast point, backswing, projectile or travel behavior;
- cooldown, charges, duration, and uptime;
- mana, health, or other costs;
- reliability and setup requirements;
- scaling and upgrades;
- counterplay and response windows.

Then explain what behavior that ability rewards.

### Kit design

Study the full ability set as one behavioral system.

Ask:

- Which abilities create conditions for the others?
- Which capabilities deliberately overlap or remain absent?
- What internal trade-offs exist?
- Is there one fixed combo, or a flexible set of sequencing decisions?
- How do passive and active pieces reinforce the same behavior?
- Which weakness prevents the kit from solving every problem itself?

### Full-hero behavior

Describe how the hero tends to approach:

- lane interaction;
- farming and resource acquisition;
- movement around the map;
- skirmishes;
- team fights;
- initiation and follow-up;
- target selection;
- pursuit and retreat;
- defensive play;
- playing from ahead or behind.

### Item interaction

Include item analysis when the hero's behavior or viability materially depends on certain item capabilities. Distinguish between:

- items that amplify an existing strength;
- items that repair a structural weakness;
- items that unlock a new action pattern;
- items that change timing or commitment;
- items that are merely efficient statistics.

### Hero conclusion

End with:

- the hero's design identity;
- the main strengths and where they are allocated;
- the weaknesses and counterplay that pay for those strengths;
- the decisions the player repeatedly makes;
- transferable design lessons;
- unresolved questions to compare against later heroes.

## Equipment and item case guide

For equipment or other items, focus on:

- acquisition price and timing;
- build path and intermediate value;
- slot pressure and opportunity cost;
- passive numerical value;
- active or passive capability changes;
- cooldown, charge, targeting, duration, and reliability;
- whether the item amplifies, repairs, or transforms a hero's behavior;
- which opponents or situations increase or reduce its value;
- what counterplay becomes available after the item is revealed;
- whether the item creates a strategic timing window;
- transferable lessons about optional capability systems.

## System case guide

For lane, creep, economy, objective, terrain, vision, combat, or other systemic rules:

1. identify the local rule;
2. identify who makes decisions because of it;
3. identify the resource, spatial, temporal, or informational pressure it creates;
4. identify how players can manipulate or contest it;
5. connect the local rule to match pacing and broader strategy;
6. compare with nearby rules that produce a different behavior;
7. extract a transferable principle with conditions.

System analysis should explain why a rule exists as part of gameplay, not merely document that it exists.

## Cross-case synthesis

Do not synthesize after every case.

After a small deliberately varied group of cases, compare them along the questions that actually emerged. Candidate synthesis topics include:

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
- how optional items change a character's action space.

A cross-case principle should name both the repeated pattern and the cases that challenge its limits.

## Anti-patterns for this project

Avoid these research failure modes:

- building a complete ontology before asking a design question;
- collecting every visible parameter without explaining behavior;
- treating a role label as a design explanation;
- inferring designer intent from mechanics alone;
- calling something "balanced" without identifying its costs and counterplay;
- assuming stronger numbers imply stronger design;
- promoting a pattern from one convenient case;
- forcing every case through an identical exhaustive template;
- preserving obsolete abstractions in current docs merely because work was already spent on them.

## Success condition

A successful case should leave the project with something another game designer can use: a clearer causal model of how concrete rules create behavior, decisions, trade-offs, counterplay, identity, pacing, or information pressure.

The repository should accumulate **design understanding**, not merely Dota 2 facts.
