---
name: legacy-refactoring
description: Use when improving heavily coupled or difficult-to-maintain code. Focuses on incremental refactoring, behavior preservation, dependency reduction, and architectural improvement without unnecessary rewrites.
---

# Legacy Refactoring

Use when the goal is reducing technical debt or improving architecture.

The objective:

> Improve structure while preserving existing behavior.

---

# Core principles

## Do not rewrite blindly

Avoid complete rewrites unless:

- Current code cannot be safely modified.
- Behavior is understood.
- Migration strategy exists.
- Verification is possible.

---

# Understand existing behavior first

Before refactoring:

Identify:

- Current inputs and outputs.
- External dependencies.
- Side effects.
- Error behavior.
- Existing edge cases.
- Hidden business rules.

---

# Establish safety before changing structure

When possible:

- Add characterization tests.
- Capture existing behavior.
- Add regression coverage.

Tests should protect behavior, not existing implementation details.

---

# Refactoring strategy

Prefer:
Understand
↓
Add safety net
↓
Introduce boundaries
↓
Extract responsibilities
↓
Migrate gradually
↓
Remove obsolete paths

---

# Introduce seams

Prefer creating replaceable boundaries:

Examples:

Before:
business logic
|
direct database/API/filesystem call

After:
business logic
|
interface boundary
|
external dependency

The goal is reducing coupling.

---

# Extraction rules

Extract when:

- Responsibility is clear.
- Boundary improves future change.
- Testing becomes easier.
- Dependencies become simpler.

Avoid:

- Creating many small classes.
- Introducing patterns without need.
- Moving complexity without reducing it.

---

# Migration rules

Prefer incremental migration:

old behavior
|
new boundary
|
new implementation

Avoid:
old system
|
complete replacement

---

# Final response

Include:

- Current problems identified
- Refactoring strategy
- Behavior preservation approach
- New boundaries introduced
- Migration steps
- Tests added
- Remaining technical debt