# Release Notes

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
