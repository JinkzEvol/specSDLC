---
description: "Structured code review for security, performance, correctness, and lane discipline."
argument-hint: "PR, branch, or diff scope"
---

# /code-review

Run after implementation, before `/security-review` and `/verify`. Block on N+1 queries, missing edge cases, error-handling gaps, lane violations, and contract drift.

## Always read first

1. The diff or PR
2. The active spec the change implements
3. `.github/instructions/coding-standards.instructions.md`
4. The lane map for the changed paths
5. The contracts the change touches

## Routes to

- `.github/agents/code-reviewer.agent.md`

## Steps

1. Walk each changed file with the lane map.
2. Flag cross-lane edits without an integration packet.
3. Flag contract drift, schema changes without consumer updates, or removed exports.
4. Walk happy paths, error paths, and edge cases.
5. Flag security-adjacent issues but defer to `/security-review` for the verdict.
6. Issue a hard verdict: pass | request changes | block.

## Stop conditions

- The diff edits coordination files without packet declaration
- A contract changed without consumer updates
- Tests are present but skipped, pending, or trivially passing

## Output

```text
PR or branch:
Files reviewed:
Lane violations:
Contract drift findings:
Correctness findings:
Verdict (pass | request changes | block):
Next command:
```
