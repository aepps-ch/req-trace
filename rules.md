# req-trace Rules

## req-trace setup

### installation
Keep this repository at `req-trace/` of your project.
Recommended: pin it as a git submodule to a release branch.
Example add command: `git submodule add -b release/v0.7 https://github.com/aepps-ch/req-trace.git req-trace`

### external rules
If the agents.md file contains references to files like:  
`req-trace/modules/[foohub.com]/[org]/[repo]/[path]`  
You have to search for the file/folder on the origin-repo without the `req-trace/modules/` prefix and copy them into the `req-trace/modules` folder so it can be accessed more easily on the local machine.

### updates
When updating `req-trace` in an existing project, always review `req-trace/release-notes.md` first.
Updates can include breaking changes and migration steps that must be applied to the project.

## Project specification
A specification scope is the project root or any subdirectory that contains `spec.md`, `spec/`, or `spec-deltas/`.
Each scope can contain:
- a consolidated specification in `spec.md` or `spec/`
- versioned specification deltas in `spec-deltas/vN-short-description.md`

The consolidated specification may be absent. New scopes normally start with only `spec-deltas/`.
All specification must be followed as long as it does not contradict the applicable rules.

### Effective specification
For each changed file, collect every specification scope from the project root down to the deepest containing scope.
Read scopes from parent to child.
Within each scope, read the consolidated specification first if present, then all remaining unconsolidated `spec-deltas/v*.md` files in version order.

Child scope specification overrides parent scope specification where they conflict.
Overrides only apply inside the child scope tree.
Do not assume that the root specification is sufficient for files inside a child scope.

### Version Deltas
Every durable specification change must be reflected in a new version delta.
Relative implementation instructions do not need their own spec delta when they only describe how to change the current implementation, for example "change this in that way", "make this smaller", or "fix that bug".

For every new revision, create a new `spec-deltas/v{N+1}-short-description.md` file in the affected specification scope containing the spec delta only.
The description must be a short kebab-case summary of the delta, for example `v2-add-login.md` or `v3-adjust-dashboard-layout.md`.
Do not rewrite or mutate older version files after they are created.

The effective specification for each scope may be distributed across a consolidated spec plus ordered delta history (`spec-deltas/v1-*.md` ... `spec-deltas/vN-*.md`).
Never derive the full specification state from only the newest file.

### Delta Placement
When adding durable specification changes during implementation, write each new delta into the specification scope where the change belongs.
If an edited path is inside a child scope, scope-specific changes must be captured in that scope, while parent-scope changes must remain in the parent scope.
If a requested specification change spans multiple scopes, split the content across those scopes.
If it is not clear how to split the requested content between scopes, ask the human before writing the spec delta.

### Delta Content
If you are instructed to create or change the specification, apply the human's words to the relevant `spec-deltas/vN-short-description.md` exactly as they were given to you.
Content inside `vN-short-description.md` can only be one-to-one the things you were instructed.
You are not allowed to change or complement the specification or to merge things from the applicable rules into it.

Exception: when the human approves your suggestion (you, the agent) with a trigger prompt such as "please", "yes", "do that", or similar, the trigger prompt must not be copied into the spec delta.
In that case, replace the trigger prompt with a minimal summary of the concrete specification change you suggested.

### Consolidation
Consolidation is done by a human from time to time.
It means merging older spec deltas into the consolidated spec (`spec.md` or `spec/`) of the same specification scope.
Spec content that has been consolidated into `spec.md` or `spec/` should no longer remain available as a spec delta in that scope.

### Compliance Requirement
> **Non-negotiable:** every change (feature, bug fix, refactor) must comply with the entire effective specification for each changed path — i.e. every applicable parent-to-child scope, each with `spec.md` or `spec/` when present plus the union of _all remaining unconsolidated_ `spec-deltas/v*.md` files up to the latest version.
> Never scope your work based solely on the newest delta; always cross-check the complete history before making changes.
> New code must be re-checked against all applicable specification rules after each change, and refined iteratively until every spec item is satisfied.

### Archive Folders Are Not Implementation Input
Folders named like `archive*` (for example `archive`, `archive-v1`, `archive-2026`) are historical snapshots.
Do not use archive-folder content as implementation input when building the current version, unless the human explicitly requests it.
Current implementation must be derived from active specification files and active project sources only.

### Secure defaults
If we there is an allow list e.g. `["READ", "WRITE"]` then a empty list `[]` should always mean nothing is allowed / no access. Empty lists should never default to everything is allowed.
