---
name: maintainable-code
description: Use for normal application changes including features, bug fixes, and small refactors. Focuses on correctness, minimal risk, repository conventions, maintainability, and secure implementation.
---

# Maintainable Code

Use when implementing normal production changes.

Examples:

- Add feature
- Fix bug
- Modify API behavior
- Update UI logic
- Small refactor

---

# Engineering priorities

1. Correct behavior
2. Security
3. Compatibility
4. Maintainability
5. Optimization

---

# Principles

## Understand before editing

Before changing code:

- Inspect related modules.
- Identify callers.
- Review tests.
- Understand existing patterns.
- Identify ownership boundaries.

Do not modify code based only on one file.

---

## Prefer minimal sufficient changes

Make the smallest change that fully solves the problem.

Avoid:

- Unrelated refactoring.
- Architecture redesign.
- Renaming unrelated code.
- Introducing new patterns without need.

---

## Follow repository conventions

Prefer:

- Existing utilities.
- Existing abstractions.
- Existing naming.
- Existing error handling.
- Existing testing style.

---

# Modularization

Extract code only when it improves:

- Responsibility boundaries.
- Testability.
- Reuse.
- Readability.

Extract when:

- Logic repeats.
- Logic has a clear domain responsibility.
- A module boundary already exists.

Do not extract:

- Short one-off logic.
- Generic helpers.
- Abstractions created only to reduce lines.

---

# Security

Ensure:

- Input validation at boundaries.
- Authorization checks remain intact.
- Secrets are not introduced.
- Sensitive data is not leaked.
- Safe APIs are used.

---

# Testing

For behavior changes:

- Update existing tests.
- Add regression tests.
- Test behavior rather than implementation details.

---

# Final response

Include:

- What changed
- Why this approach
- Behavior impact
- Files touched
- Verification results
- Security considerations
- Risks