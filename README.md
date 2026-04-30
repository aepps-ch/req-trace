# req-trace

<img src="https://openmoji.org/data/color/svg/1F99E.svg" alt="lobster mascot" align="right" width="110" />

<sub>Mascot icon: OpenMoji (CC BY-SA 4.0)</sub>

A lightweight **specification operating system** for AI-assisted project work.

Instead of repeating long setup prompts in every project, keep `req-trace/` as a stable submodule and evolve your project specification as versioned spec deltas.

> `req-trace` is the shared rulebook; your project owns the specification history.

## What this is (and isn't)
- ✅ **Is:** shared process + constraints (`req-trace/`) reused across projects
- ✅ **Is:** a versioned specification flow (`spec-deltas/vN-short-description.md`)
- ✅ **Is:** a path-scoped specification system for projects with subpackages
- ❌ **Is not:** a one-off template to copy once and forget

## Files
- `rules.md` — organization-wide project rules and project specification rules (shared)
- `rules/` — optional rule modules for additional guidelines
- `instructions.md` — prompt/workflow shortcuts
- `template.md` — integration note (submodule usage)
- `openclaw.md` — OpenClaw extension for consistent req-trace application

## Agent Flow
These steps are meant to be done by you (the agent).

1. Make sure your project is initialized as a git-repository.
2. Keep this repository according to [rules.md](rules.md) → **req-trace Setup**.
3. Copy `req-trace/template.md` as `agents.md` into the root of your project.
4. Delete the additional-guidelines from the copied agents.md that aren't mentioned explicitly mentioned in your instructions.  
5. The newly created `agents.md` file must be followed for implementation when using the req-trace flow.
6. Maintain the project specification according to [rules.md](rules.md) → **Project Specification**.

## Concepts
**Consolidation** means a human merges older spec deltas into the consolidated spec (`spec.md` or `spec/`).
See [rules.md](rules.md) → **Project Specification**.

**Recreation** means reimplementing the code according to the active spec.
See [recreate.md](recreate.md).

## Example prompt for your agent

```text
Please implement this specification with the github.com/aepps-ch/req-trace flow:
- Build a web app that tracks naps for office cats 🐈
- Start/stop nap timer per cat
- Show daily nap leaderboard
- Add a “zoomies detected” event button
```

## Skill for agents
If you are using an agent (like open-claw or codex) and want to use req-trace for your projects, tell your agent this:

**Generic:**  
> Please install the req-trace skill from `github.com/aepps-ch/req-trace`. 

**Codex:**  
If you are using codex directly, you should follow this: [setup](codex/codex.md)

After this instruction, you can always tell your agent to create a project following the req-trace flow.
If a project uses req-trace, the flow will be applied automatically.

## Release Notes
See [release-notes.md](release-notes.md) for release history and migration notes.
