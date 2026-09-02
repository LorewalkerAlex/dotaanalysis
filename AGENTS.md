# DOTAANALYSIS Agent Instructions

DOTAANALYSIS is one continuous, sequential research project. Multiple ChatGPT sessions exist only because a single session has finite context. Do not treat sessions as independent or parallel research threads unless the user explicitly changes that rule.

The public GitHub repository `LorewalkerAlex/dotaanalysis` is the durable source of truth. Chat history and project memory may provide useful context, but repository content takes precedence when reconstructing project state.

## Session startup

Before substantive analysis:

1. Read `PROJECT.md`.
2. Read `ROADMAP.md`.
3. Read `docs/INDEX.md`.
4. Locate the current `[ACTIVE]` roadmap node and reconstruct what has already been established, what remains open, and what should happen next.
5. Use `docs/INDEX.md` to read only the additional documents relevant to that node. Do not scan the entire repository by default.

If the user says only “继续”, “接着做”, or otherwise asks to resume, recover the next step from the repository rather than asking the user to restate prior work.

## Research behavior

- Distinguish verified Dota 2 facts from analytical interpretations and hypotheses about design intent.
- When a claim depends on current mechanics, numbers, patches, maps, heroes, items, or other changeable information, verify it against reliable current sources.
- Do not create parallel terminology, frameworks, categories, or files before checking whether an existing repository concept already represents the same idea.
- Treat discussion as provisional until the user decides it should be persisted.
- Repository documents should represent the project's current best model. When later research improves or overturns an earlier model, prefer updating the authoritative document rather than preserving obsolete conclusions in the main text; Git history preserves the earlier state.
- Research structures, classifications, terminology, hypotheses, frameworks, and conclusions are mutable. The operating principles in `PROJECT.md` are comparatively stable, but they may still be changed when the user explicitly decides to change them.

## Repository mutation and publication workflow

Reading, searching, and analyzing the public repository does not require separate approval.

Any operation that changes repository state requires the user's explicit approval for the specific proposed change. This includes creating, editing, moving, or deleting files; changing the roadmap or index; creating commits or branches; and other repository writes. Approval for one change is not blanket approval for later changes.

After the user approves a specific repository change, use the Web Local Development workflow by default unless the user explicitly changes this rule:

1. Use public GitHub as the durable read baseline and identify the public baseline commit.
2. Prepare complete candidate files and run the strongest available pre-delivery checks on those exact bytes.
3. Deliver one complete replacement file when one path changes, or one repo-structured ZIP when multiple paths change.
4. Treat the user's local checkout as the write target. Use PowerShell only as a thin orchestration layer to apply the delivered bytes and run local validation; do not embed repository file contents in shell commands.
5. Keep apply/validation separate from commit/push.
6. Stage only the approved, assistant-maintained path manifest, then commit and push as a separate publication step.
7. After push, re-read the public GitHub state and verify the expected commit and files before treating the change as complete.

Do not use direct GitHub write operations as a substitute for this local workflow unless the user explicitly authorizes that change in process.

During an approved mutation, successful assistant-directed operations in the user's local checkout are the session-local working state. Continue from that observed local state until it is repaired, abandoned, or published; do not silently revert reasoning to stale public files while the approved local change is in progress.

When the user asks to archive, finalize, prepare a handoff, or persist the current work:

1. Synthesize only the stable conclusions that should survive the session.
2. Propose the exact repository changes for user review.
3. Make no repository mutation until the user explicitly approves those changes.
4. After approval, update the relevant knowledge documents, `docs/INDEX.md` when needed, and `ROADMAP.md` so that a fresh session can continue without the previous chat, using the publication workflow above.

## Handoff success condition

A fresh ChatGPT session with access only to this repository and the DOTAANALYSIS project instructions must be able to understand what the project is, what has already been established, where the research currently stands, and what should happen next.
