# Recreation workflow
Recreation means reimplementing the code from the active specification.
It does not mean consolidating spec deltas into `spec.md` or `spec/`.

Recommended repeatable process:
1. Read `req-trace/rules.md`.
2. Read the active specification: `spec.md` or `spec/` first if present, then all remaining unconsolidated files in `spec-deltas/` in order.
3. Archive the current implementation into an `archive-v{N}` folder at repo root.
4. Reimplement the project from the active specification.
5. Do not use archive-folder content as implementation input unless the human explicitly requests it.
6. Commit and push the recreated implementation.
