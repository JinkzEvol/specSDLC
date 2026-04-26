---
description: "Spec-guardian compliance check before code is written or after a spec change."
argument-hint: "Plan, spec change, or implementation under review"
---

# /compliance

Pre-code spec compliance gate. Confirms the work agrees with the active specs and that no spec drift is being introduced.

## Always read first

1. The plan or spec change under review
2. The active spec(s) the work touches
3. `docs/SYSTEM_STATE.md`
4. `.github/instructions/sdlc-workflow.instructions.md`

## Routes to

- `.github/agents/spec-guardian.agent.md`

## Steps

1. Compare the plan or change against each affected spec.
2. List spec sections referenced or modified.
3. Identify any silent spec drift (behavior change without a spec update).
4. Issue a hard verdict: comply | drift detected | spec gap.
5. On drift, route to `/sync-spec`. On gap, route to `/sync-spec` to define the missing spec section first.

## Stop conditions

- Spec is ambiguous and not yet clarified
- The change requires a new spec section that does not exist
- Two active specs disagree on the same point

## Output

```text
Plan or change:
Specs evaluated:
Verdict (comply | drift | gap):
Drift or gap details:
Recommended spec update:
Next command:
```
