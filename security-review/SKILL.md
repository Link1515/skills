---
name: security-review
description: Use when reviewing or modifying security-sensitive code. Focuses on secure defaults, threat boundaries, authorization, validation, and reducing attack surface.
---

# Security Review

Use for security-sensitive changes.

Examples:

- Authentication
- Authorization
- User data
- External input
- File uploads
- Payment
- Secrets handling

---

# Security principles

## Trust boundaries

Identify:

- User input
- External APIs
- Database data
- Files
- Configuration
- Internal services

Treat external data as untrusted.

---

# Validate input

Ensure:

- Format validation.
- Size limits.
- Type validation.
- Normalization.
- Safe parsing.

---

# Authorization

Verify:

- Authentication exists.
- Authorization is checked.
- Object ownership is validated.
- Privilege escalation is prevented.

---

# Common risks

Avoid:

- Injection
- SSRF
- Path traversal
- Unsafe deserialization
- IDOR
- Secret leakage
- Missing access control

---

# Secure defaults

Prefer:

- Fail closed.
- Least privilege.
- Framework security defaults.
- Safe APIs.

---

# Error handling

Do not expose:

- Stack traces.
- Internal paths.
- Secrets.
- Sensitive identifiers.

---

# Final response

Include:

- Threats considered
- Security changes
- Validation changes
- Authorization impact
- Remaining risks