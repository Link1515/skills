---
name: maintainable-code
description: Use when modifying application code in this repo. Produces minimal, reviewable diffs that follow repo conventions and preserve architecture boundaries.
---

# When to use
Use for feature changes, bug fixes, and refactors in this repository.

# Do not use when
- Pure documentation edits
- Large cross-cutting migrations unless explicitly requested
- Experimental prototypes

# Goals
- Prefer clear, maintainable code over clever code
- Keep diffs minimal and scoped
- Preserve public APIs unless the task requires changes
- Follow existing project patterns before introducing new abstractions

# Rules
1. Read neighboring files and existing tests before editing.
2. Reuse existing abstractions and utilities when possible.
3. Do not introduce new dependencies unless necessary.
4. Prefer explicit names and straightforward control flow.
5. Keep functions focused and small.
6. Add or update tests for happy path, edge cases, and failure cases.
7. Run lint, typecheck, and relevant tests after changes.
8. Summarize architectural impact in the final output.

# Output format
- What changed
- Why this approach
- Files touched
- Tests added/updated
- Verification results
- Risks / follow-ups

# Verification checklist
- Lint passes
- Typecheck passes
- Relevant tests pass
- No unrelated files changed

# Gotchas
- Do not move files unless necessary
- Do not rename exported symbols without checking all references
- Do not refactor unrelated modules “while here”