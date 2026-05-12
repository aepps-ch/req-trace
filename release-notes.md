# Release Notes

## v0.7: external rule modules

### Breaking Changes
This release is not backward compatible with v0.6.

The bundled optional rule files were removed from `req-trace/rules/`.
The old req-trace guideline rules now live in the external repository:
- `github.com/timble-one/coding-rules`

Removed bundled rule files:
- `req-trace/rules/autodeploy.md`
- `req-trace/rules/backend.md`
- `req-trace/rules/codestyle.md`
- `req-trace/rules/deployment-agnostic.md`
- `req-trace/rules/docker.md`
- `req-trace/rules/frontend.md`

Projects must no longer reference those old `req-trace/rules/*.md` files directly.
Rule files that come from external repositories are now referenced through `req-trace/modules/`.

### Changes
`template.md` now uses an explicit rule list instead of the old "Additional Guidelines" section.
Every listed rule file must be applied strictly.

`rules.md` now defines how external rules are handled:
when an agent sees a rule reference like `req-trace/modules/[host]/[org]/[repo]/[path]`, it must find the matching file or folder in the origin repository without the `req-trace/modules/` prefix and copy it into `req-trace/modules/` for local access.

### Migration From v0.6
1. Update the project `req-trace` submodule to release `v0.7`.
2. Review the project's root agent instructions file.
   - Preferred file name: `agents.md`
   - Legacy file name: `agent.md`
3. Replace the old req-trace template content with the new `req-trace/template.md` structure.
4. Keep the `git submodule update --init req-trace` initialization instruction at the top.
5. Replace the old "Additional Guidelines" section with a `### Rules` section.
6. Keep `req-trace/rules.md` in the rule list.
7. Remove references to deleted bundled files such as `req-trace/rules/frontend.md`, `req-trace/rules/backend.md`, or `req-trace/rules/codestyle.md`.
8. For every rule that still applies, add a `req-trace/modules/github.com/timble-one/coding-rules/...` reference that points to the corresponding file or folder in `github.com/timble-one/coding-rules`.
9. If the project has local project-specific rules, keep them as separate local rule files and list them explicitly in `agents.md` or `agent.md`.
10. Make sure each referenced external rule file or folder is copied into `req-trace/modules/` according to `req-trace/rules.md` before relying on it locally.

Example `agents.md` rule list after migration:

```md
### Rules

**Important:** Apply every rule that is mentioned and referenced here strictly to every change in this project.

 - req-trace/rules.md
 - project-rules.md
 - req-trace/modules/github.com/timble-one/coding-rules/frontend.md
 - req-trace/modules/github.com/timble-one/coding-rules/docker.md
```

## v0.6: project spec deltas and consolidated spec

### Breaking Changes
This release is not backward compatible with v0.5.

Project specification delta files now live in `spec-deltas/` instead of `requirements/`.
- Old: `requirements/project.vN.md`
- New: `spec-deltas/vN-short-description.md`

Specification delta files now include a short description in the filename.
- Old: `project.vN.md`
- New: `vN-short-description.md`

The initial project specification template was removed.
- Old: `req-trace/requirements.md`
- New: no template file; create the first delta directly in `spec-deltas/`

The shared rules file and optional guideline folder were renamed.
- Old: `req-trace/implementation.md`
- New: `req-trace/rules.md`
- Old: `req-trace/implementation/`
- New: `req-trace/rules/`

### Changes
Projects may start with only spec deltas, but a human can consolidate them over time.
The consolidated effective spec can be stored in either:
- `spec.md`
- `spec/`

When a consolidated spec exists, it must be read before the remaining unconsolidated spec deltas.
Spec content that has been consolidated should no longer remain available as a spec delta.

Spec deltas are only required for durable specification changes.
Relative implementation instructions such as "change this in that way" do not need their own delta.
When the human only approves your suggestion (you, the agent) with a trigger prompt such as "please", the delta must contain a minimal summary of the suggested specification change instead of the trigger prompt.

Projects can contain nested specification scopes.
Any subpackage directory with `spec.md`, `spec/`, or `spec-deltas/` has specification that agents must implement for that directory tree.

For files inside a subpackage, agents must read and implement the project root specification first and then each containing subpackage specification from parent to child.
Child scope specification overrides parent scope specification only inside the child tree.

When agents add durable spec deltas while editing inside a child scope, scope-specific content must be written into that scope's `spec-deltas/`.
Parent-scope content must stay in the parent scope.
If the split between scopes is unclear, the agent must ask the human before writing the spec delta.

### Migration From v0.5
1. Rename `requirements/` to `spec-deltas/`.
2. Rename existing `project.vN.md` files to `vN-short-description.md` inside `spec-deltas/`.
3. Update local documentation, scripts, and agent instructions that reference `requirements/project.vN.md` so they reference `spec-deltas/vN-short-description.md`.
4. Remove references to `req-trace/requirements.md`.
5. Update project `agents.md` references from `req-trace/implementation.md` to `req-trace/rules.md`.
6. Update references to optional guideline files from `req-trace/implementation/` to `req-trace/rules/`.
7. Review scripts, documentation, and agent instructions for old path references.

## v0.5: extracting guidelines
You now have to specify inside agents.md (template.md) which rule modules you want to use.

## v0.4: project renamed
This project was renamed from `agents-md` to `req-trace`.

## v0.3: project requirements moved
Project requirement files moved to `requirements/` instead of the project root.
- Old: `project.vN.md`
- New: `requirements/project.vN.md`
