---
description: "Portable security standards for review, implementation, and deployment gates."
applyTo: "**"
---

# Security Standards

- No hardcoded secrets.
- Validate untrusted input.
- Review auth and authorization at boundaries.
- Check injection risks for the active stack.
- Keep sensitive data out of logs and errors.
- Verify environment-specific secret handling before deployment.
- Treat isolation, tenancy, or permission drift as blocking.

## Response rule

If a serious security issue is found, stop normal progress and route through the security reviewer or security lead.

