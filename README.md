# req-trace (formerly agents-md)

<img src="https://openmoji.org/data/color/svg/1F99E.svg" alt="lobster mascot" align="right" width="110" />

<sub>Mascot icon: OpenMoji (CC BY-SA 4.0)</sub>

A lightweight **requirements operating system** for AI-assisted project work.

Instead of repeating long setup prompts in every project, keep `req-trace/` as a stable submodule and evolve requirements in your project as versioned deltas.

> `req-trace` is the shared rulebook; your project owns the requirements history.

## What this is (and isn't)
- ✅ **Is:** shared process + constraints (`req-trace/`) reused across projects
- ✅ **Is:** a versioned requirements flow (`requirements/project.vN.md`)
- ❌ **Is not:** a one-off template to copy once and forget

## Files
- `requirements.md` — guideline for drafting initial project requirements (`requirements/project.v1.md`)
- `implementation.md` — organization-wide implementation constraints (shared)
- `instructions.md` — prompt/workflow shortcuts
- `template.md` — integration note (submodule usage)
- `openclaw.md` — OpenClaw extension for consistent req-trace application

## Usage
1. Make sure your project is initialized as a git-repository.
2. Keep this repository at `req-trace/` of your project
   - Recommended: pin it as a git submodule to a release branch
   - Example add command: `git submodule add -b release/v0.3 https://github.com/trace-code-org/req-trace.git req-trace`
3. Copy `req-trace/template.md` as `agents.md` into the root of your project.
4. Delete the additional-guidelines from the copied agents.md that aren't mentioned explicitly mentioned in your instructions.  
5. The newly created `agents.md` file must be followed for implementation when using the req-trace flow.
6. Maintain **project-specific requirements** as versioned delta files in `requirements/project.vN.md`
(see: `req-trace/implementation.md` → **Project Requirements / Versions**)

## Example prompt for your agent

```text
Please implement these requirements with the github.com/trace-code-org/req-trace flow:
- Build a web app that tracks naps for office cats 🐈
- Start/stop nap timer per cat
- Show daily nap leaderboard
- Add a “zoomies detected” event button
```

## Skill for agents
If you are using an agent (like open-claw or codex) and want to use req-trace for your projects, tell your agent this:

**Generic:**  
> Please install the req-trace skill from `github.com/trace-code-org/req-trace`. 

**Codex:**  
If you are using codex directly, you should follow this: [setup](codex/codex.md)

After this instruction, you can always tell your agent to create a project following the req-trace flow.
If a project uses req-trace, the flow will be applied automatically.

## Breaking changes
### v0.5: extracting guidelines
You now have to specify inside agents.md (template.md) which implementation-guidelines you wan't to use.

### v0.4: project renamed
This project was renamed from `agents-md` to `req-trace`.

### v0.3: project-requirements moved
Project requirement files now live in `requirements/` instead of the project root.
- Old: `project.vN.md`
- New: `requirements/project.vN.md`
