# Organization Rules

## Coding Style
Strongly domain-driven and modular (colocation of what belongs together)

## req-trace Updates
When updating `req-trace` in an existing project, always review `req-trace/release-notes.md` first.
Updates can include breaking changes and migration steps that must be applied to the project.

## Project Specification
A project may contain a consolidated effective spec in `spec.md` or inside `spec/`.
This consolidated spec may be absent. New projects normally start with only `spec-deltas/`.
When a consolidated spec exists, read it before reading `spec-deltas/`.
The active specification is the consolidated spec plus the remaining unconsolidated deltas in order.

Additional project specification can be found in versioned delta files (`spec-deltas/vN-short-description.md`) inside the project root.
It has to be followed as long as it doesn't contradict the organization rules.

### Consolidation
Consolidation is done by a human from time to time.
It means merging older spec deltas into the consolidated spec (`spec.md` or `spec/`).
Spec content that has been consolidated into `spec.md` or `spec/` should no longer remain available as a spec delta.

### Versions
Every durable change to the project specification must be reflected in a new version-delta.
Relative implementation instructions do not need their own spec delta when they only describe how to change the current implementation, for example "change this in that way", "make this smaller", or "fix that bug".
For every new revision of the project specification, create a new `spec-deltas/v{N+1}-short-description.md` file containing the spec delta only.
The description must be a short kebab-case summary of the delta, for example `v2-add-login.md` or `v3-adjust-dashboard-layout.md`.
Do not rewrite or mutate older version files after they are created.
The effective specification may be distributed across a consolidated spec plus ordered delta history (`spec-deltas/v1-*.md` ... `spec-deltas/vN-*.md`), so one cannot derive the full specification state from only the newest file.
Implementation must therefore consider the consolidated spec first, if present, and then all remaining unconsolidated deltas up to the highest version.

> **Non-negotiable:** every change (feature, bug fix, refactor) must comply with the entire effective specification — i.e. `spec.md` or `spec/` when present, plus the union of _all remaining unconsolidated_ `spec-deltas/v*.md` files up to the latest version.
> Never scope your work based solely on the newest delta; always cross-check the complete history before making changes.
> New code must be re-checked against all applicable specification rules after each change, and refined iteratively until every spec item is satisfied.

### Content Rules
If you are instructed to create or change the project specification, apply the human's words to `spec-deltas/vN-short-description.md` exactly as they were given to you.
Content inside `vN-short-description.md` can only be one-to-one the things you were instructed.
You are not allowed to change or complement the project specification or to merge things from the organization rules into it.

Exception: when the human approves your suggestion (you, the agent) with a trigger prompt such as "please", "yes", "do that", or similar, the trigger prompt must not be copied into the spec delta.
In that case, replace the trigger prompt with a minimal summary of the concrete specification change you suggested.

### Archive Folders Are Not Implementation Input
Folders named like `archive*` (for example `archive`, `archive-v1`, `archive-2026`) are historical snapshots.
Do not use archive-folder content as implementation input when building the current version, unless the human explicitly requests it.
Current implementation must be derived from active specification files and active project sources only.
