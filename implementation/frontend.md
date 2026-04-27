# Frontend Implementation
If the project specification doesn't mention how something should be achievable with the specified system, it means that it must be achievable by the user via frontend.

#### Technologies
Typescript, React, React-Relay, Tailwind

#### TypeScript configuration
Use a preset-based `tsconfig.json` via `extends` (for example `@tsconfig/*`) and only override project-specific options.
This keeps projects reproducible while avoiding repeated boilerplate defaults.

#### UI consistency and style
Use a consistent and modern UI design system across the app (typography, spacing, components, and interaction patterns must feel cohesive).

#### Screens
Even if it is not mentioned, applications must be divided into multiple screens.
