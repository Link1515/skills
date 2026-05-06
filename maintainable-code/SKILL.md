---
name: maintainable-code
description: Use when modifying application code in this repo. Produces minimal, reviewable diffs that follow repo conventions, preserve architecture boundaries, extract reusable modules when appropriate, and generate secure code that applies secure-by-default practices, input validation, least privilege, and avoids common security weaknesses.
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
- Extract reusable, focused modules when doing so improves readability, testability, or reuse
- Produce secure-by-default code that reduces common application security risks

# Rules
1. Reuse existing abstractions and utilities when possible.
2. Do not introduce new dependencies unless necessary.
3. Prefer explicit names and straightforward control flow.
4. Keep functions focused and small.
5. Before adding substantial logic, identify whether any part should be extracted into an existing utility, service, helper, hook, component, validator, adapter, repository, or domain module.
6. Prefer extracting reusable modules when logic is repeated, likely to be reused, independently testable, or represents a distinct concern such as parsing, validation, authorization, formatting, data access, API calls, or business rules.
7. Keep orchestration code thin. Entry points, handlers, controllers, routes, commands, jobs, and UI components should coordinate work, not contain large blocks of domain logic.
8. Do not create abstractions only to reduce line count. Extract only when the boundary has a clear name, stable responsibility, and improves testability or readability.
9. When adding a new module, place it according to existing project conventions and keep its public surface minimal.
10. Validate and sanitize all untrusted inputs at system boundaries.
11. Avoid common security weaknesses such as injection, unsafe deserialization, path traversal, SSRF, insecure direct object references, race-prone temp file handling, and missing authorization checks.
12. Do not hardcode secrets, tokens, credentials, or private keys.
13. Apply least privilege and fail-safe defaults when adding permissions, access checks, configuration, or error handling.
14. Avoid leaking sensitive data in logs, errors, telemetry, or API responses.
15. Use parameterized queries, safe filesystem handling, and framework-provided escaping/encoding protections where applicable.
16. Preserve or improve authentication, authorization, and data validation paths when modifying existing flows.
17. Summarize architectural, modularization, and security impact in the final output.

# Implementation workflow
When modifying application code:

1. Inspect the surrounding module, imports, tests, and nearby files before editing.
2. Identify the existing architectural pattern and ownership boundaries.
3. Decide whether the change belongs in an existing module, a new focused module, or the current file.
4. If adding more than a small amount of logic to one file, first consider extraction into a reusable function, class, service, component, hook, validator, mapper, adapter, repository, or domain module.
5. Implement the smallest scoped change that follows the chosen boundary.
6. Add or update tests at the extracted module boundary when possible.
7. In the final response, mention any extraction decision: what was extracted, what stayed inline, and why.

# Modularization and reuse
Before writing substantial code, inspect nearby files and identify the repository’s existing module boundaries. Prefer reusing or extending existing abstractions before adding new ones.

Do not put large end-to-end logic into a single file when it mixes separate concerns. Keep entry points, handlers, routes, commands, jobs, and UI components thin; they should orchestrate focused modules rather than contain validation, persistence, API access, authorization, business rules, and formatting inline.

Extract logic into a focused reusable module when it is repeated, independently testable, likely to be reused, or represents a distinct concern such as:

- Input validation or normalization
- Parsing or serialization
- Authorization or permission checks
- Business rules
- API, database, filesystem, or network access
- Mapping or formatting
- Error translation or result shaping
- Reusable UI behavior
- Cross-cutting integration logic

Use the repository’s existing naming and placement conventions for extracted modules. Keep public surfaces minimal and explicit.

Prefer concrete, domain-specific names over generic containers. For example, prefer `invoice-total-calculator`, `user-permission-checker`, `order-status-mapper`, or the repository’s existing equivalent pattern over vague catch-all modules such as `utils`, `helpers`, `common`, or `misc`.

Avoid abstraction for its own sake. Leave logic inline when it is short, one-off, clearer colocated, or when extraction would create a larger, less reviewable diff.

# Extraction decision guide
Use this guide before leaving new logic inside the current file.

Extract when:
- The same or similar logic appears in more than one place.
- The logic has a clear standalone responsibility.
- The logic can be tested independently with explicit inputs and outputs.
- The current file would otherwise mix orchestration, validation, authorization, data access, business rules, and presentation concerns.
- Another route, command, component, job, service, or test is likely to need the same behavior.
- The extracted boundary matches an existing project pattern.

Do not extract when:
- The logic is genuinely short and one-off.
- The extracted function or module would have an unclear name.
- Extraction would require excessive parameter threading or make the call site harder to read.
- The repository convention intentionally colocates this kind of logic.
- The refactor would touch unrelated files or make the diff harder to review.
- The abstraction is speculative and not grounded in current requirements.

# Output format
- What changed
- Why this approach
- Modularization decisions
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
- Large new logic was not left in entry points, handlers, controllers, routes, commands, jobs, or UI components without considering extraction
- Reusable validation, parsing, mapping, API access, persistence, authorization, and business rules were placed behind focused modules where appropriate
- New abstractions have clear names, narrow responsibilities, and tests or testable seams where practical

# Gotchas
- Do not move files unless necessary.
- Do not rename exported symbols without checking all references.
- Do not refactor unrelated modules “while here”.
- Do not weaken existing security controls for convenience.
- Do not bypass validation, authorization, or escaping already present in the codebase.
- Do not place a long end-to-end implementation in a single file when it mixes orchestration, validation, data access, authorization, business rules, and formatting.
- Do not create vague catch-all files such as `utils`, `helpers`, `common`, or `misc` unless the repository already uses that pattern and the responsibility is still clear.
- Do not extract prematurely into generic abstractions when a named domain-specific function or module would be clearer.
- Do not introduce new layers that conflict with the existing architecture.