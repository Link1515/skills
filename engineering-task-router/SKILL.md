---
name: engineering-task-router
description: Determine the appropriate engineering skill before modifying code. Routes tasks to maintainable-code, legacy-refactoring, security-review, or performance-optimization based on the primary engineering goal.
---

# Engineering Task Router

Use this skill before modifying application code when the task type is unclear or multiple engineering concerns are involved.

The goal is to select the correct engineering approach before implementation.

# Skill selection priority

Choose the skill based on the primary risk and goal.

Priority order:

1. Security risk
2. Legacy architecture / technical debt
3. Performance issue
4. Normal feature or bug fix

---

# Use security-review when

The task involves:

- Authentication
- Authorization
- Permissions
- Sensitive data
- External user input
- Payment flows
- Cryptography
- Data protection
- Security vulnerability fixes

Examples:

- "Fix privilege escalation issue"
- "Review API access control"
- "Harden file upload"

---

# Use legacy-refactoring when

The task goal is improving existing difficult-to-maintain code.

Examples:

- Large monolithic functions
- God classes
- Circular dependencies
- Excessive coupling
- Missing boundaries
- Removing technical debt
- Architecture cleanup
- Migration away from legacy patterns

The goal is:

> Improve structure while preserving behavior.

---

# Use performance-optimization when

The problem involves:

- Slow response time
- High CPU usage
- Memory growth
- Database bottlenecks
- Scaling issues
- Excessive network calls

The goal is:

> Measure first, optimize second.

---

# Use maintainable-code when

The task involves:

- New features
- Bug fixes
- Small refactors
- Local improvements
- Normal application changes

The goal is:

> Make the smallest correct and maintainable change.

---

# Combining skills

Avoid applying multiple large strategies simultaneously unless necessary.

Examples:

Security vulnerability in legacy authentication code:

1. security-review
2. legacy-refactoring only if needed after security risk is addressed

Performance issue in legacy code:

1. performance-optimization
2. legacy-refactoring if architectural changes are required

---

# Decision rule

When uncertain:

Choose the approach with:

- Lower risk
- Smaller blast radius
- Better verification ability
- Less unnecessary change