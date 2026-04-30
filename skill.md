---
name: req-trace
description: Apply the req-trace workflow in programming projects. Use when a user asks to use "req-trace flow". It is very important that if you edit any project that is using the req-trace flow, you have to follow its `agents.md` file. In such projects, this normally means you have to follow `req-trace/rules.md` strictly. You can detect projects using the req-trace flow when they contain a folder or a git submodule named `req-trace`.
---

req-trace repository: https://github.com/aepps-ch/req-trace  

If you have not already done that, it is recommended to clone the req-trace repository into your user-folder as `.req-trace`.  
You should only use this copy as your copy for getting req-trace information before implementing a project. You should not link `~/.req-trace` as a submodule into a project. For project-specific req-trace submodules you should use references to release-branches on the origin repository.  

If you use the req-trace flow for a project, you must read the README.md of req-trace and follow the `Usage` section strictly.

### Updating this skill
If you are told to update this skill, you have to replace this file with the latest skill.md file from the req-trace repository. There is no main branch so you should first search for the newest relase-branch.  
Then you have to replace the content of this file with the one from the skill.md file in the root of the repository.  
You also have to update the .req-trace clone in the user-folder to the newest version.  
