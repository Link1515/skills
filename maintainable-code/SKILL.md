---
name: maintainable-code
description: Use when modifying application code in this repo. Produces minimal, reviewable diffs that follow repo conventions, preserve architecture boundaries, and generate secure code that applies secure-by-default practices, input validation, least privilege, and avoids common security weaknesses.
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
- Produce secure-by-default code that reduces common application security risks

# Rules
1. Reuse existing abstractions and utilities when possible.
2. Do not introduce new dependencies unless necessary.
3. Prefer explicit names and straightforward control flow.
4. Keep functions focused and small.
5. Validate and sanitize all untrusted inputs at system boundaries.
6. Avoid common security weaknesses such as injection, unsafe deserialization, path traversal, SSRF, insecure direct object references, race-prone temp file handling, and missing authorization checks.
7. Do not hardcode secrets, tokens, credentials, or private keys.
8. Apply least privilege and fail-safe defaults when adding permissions, access checks, configuration, or error handling.
9. Avoid leaking sensitive data in logs, errors, telemetry, or API responses.
10. Use parameterized queries, safe filesystem handling, and framework-provided escaping/encoding protections where applicable.
11. Preserve or improve authentication, authorization, and data validation paths when modifying existing flows.
12. Summarize architectural and security impact in the final output.

# Output format
- What changed
- Why this approach
- Files touched
- Verification results
- Security considerations
- Risks / follow-ups

# Verification checklist
- Lint passes
- Typecheck passes
- No unrelated files changed
- New or modified code paths validate untrusted input
- No secrets introduced in code, tests, config, or logs
- Authn/authz behavior reviewed for affected flows
- Error handling does not expose sensitive internals

# Gotchas
- Do not move files unless necessary
- Do not rename exported symbols without checking all references
- Do not refactor unrelated modules “while here”
- Do not weaken existing security controls for convenience
- Do not bypass validation, authorization, or escaping already present in the codebase