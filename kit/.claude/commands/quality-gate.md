---
description: "Binary pass-or-fail gate after verify, against quality/criteria.md."
argument-hint: "Phase, milestone, or release scope"
---

# /quality-gate

Binary gate after `/verify`. Use the active specs, review outputs, security findings, and `quality/criteria.md` to decide whether work can advance.

## Always read first

1. `quality/criteria.md`
2. The verify evidence packet from `/verify`
3. The plan or spec the change is implementing
4. Outputs from `/code-review` and `/security-review`
5. `docs/SYSTEM_STATE.md`

## Routes to

- `.github/agents/quality-gate.agent.md`

## Steps

1. Confirm `/verify` returned a non-fail verdict.
2. Walk each criterion in `quality/criteria.md` against the evidence.
3. Treat missing evidence as failure, not warning.
4. Issue a single hard verdict: pass or fail.
5. On fail, name the criterion, the missing evidence, and the recommended remediation command.
6. On pass, route to `/phase-assess`.

## Stop conditions

- `/verify` failed
- Required review evidence is missing
- A criterion is ambiguous and not yet clarified in `quality/criteria.md`

## Output

```text
Scope:
Verdict (pass | fail):
Criteria evaluated:
Failed criteria with missing evidence:
Recommended remediation command(s):
Next command:
```
