---
description: "Targeted security review for auth, secrets, data exposure, and trust boundaries."
argument-hint: "PR, branch, or diff scope"
---

# /security-review

Run after `/code-review`, before `/verify`. Owns the security verdict for the change.

## Always read first

1. The diff or PR
2. `.github/instructions/security-standards.instructions.md`
3. Trust-boundary documentation in the spec hierarchy
4. Auth, secrets, and data-handling code paths the change touches

## Routes to

- `.github/agents/security-reviewer.agent.md`

## Steps

1. Identify trust boundaries crossed by the change.
2. Audit auth and authorization paths.
3. Audit secrets handling and storage.
4. Audit data exposure: logs, error messages, telemetry, response payloads.
5. Audit input validation, deserialization, and injection surfaces.
6. Issue a hard verdict: pass | request changes | block.

## Stop conditions

- The change touches auth and another concern in the same packet
- Secrets are written to client-reachable code
- A trust boundary is unclear or undocumented

## Output

```text
PR or branch:
Trust boundaries crossed:
Auth findings:
Secrets findings:
Data-exposure findings:
Input-handling findings:
Verdict (pass | request changes | block):
Next command:
```
