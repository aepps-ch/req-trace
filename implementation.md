# Organization Requirements
**Coding Style:** Strongly domain-driven and modular (colocation of what belongs together)

### API
If there is an API between frontend and backend it must use graphql.  

### Project Requirements (project.vN.md)
Project requirements can be found in versioned files (`requirements/project.vN.md`) inside the project root.
They have to be followed as long as they don't contradict the organization requirements.

#### Versions
Any change in this project must be reflected in a new version-delta. Even if it is only a bug-fix.  
For every new revision of the project requirements, create a new `requirements/project.v{N+1}.md` file containing the requirement delta only.
Do not rewrite or mutate older version files after they are created.
The effective requirements are distributed across the ordered delta history (`requirements/project.v1.md` ... `requirements/project.vN.md`), so one cannot derive the full requirement state from only the newest file.
Implementation must therefore consider all revisions up to the highest version.  

#### Content rules
If you are instructed to create or change this project you have to apply the words to project.vN.md exactly as they were given to you. Content inside project.vN.md can only be one-to-one the things you were instructed. You are not allowed to change or complement the project-requirements or to merge things from the organization-requirements into them.

#### Archive folders are not implementation input
Folders named like `archive*` (for example `archive`, `archive-v1`, `archive-2026`) are historical snapshots.
Do not use archive-folder content as implementation input when building the current version, unless the human explicitly requests it.
Current implementation must be derived from active requirement files and active project sources only.

### Docker
Everything must be wrapped inside docker container(s) so it can be deployed easily.
A Makefile must contain all the necessary docker-compose commands.  
Containers must be managed with docker-compose.

### Authentication
Requirements for "logging in" and "to register" as a user imply that there needs to be some authentication in the system. This normally also implies that there are resources that can only be accessed by the user, when he is authenticated.
