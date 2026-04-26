---
description: "Assess whether the current phase is complete enough to advance."
argument-hint: "Phase or milestone label"
---

# /phase-assess

Run after `/quality-gate` passes. Decides whether the work landed during this phase materially advances the system toward its destination.

## Always read first

1. `docs/SYSTEM_STATE.md`
2. The phase definition in the spec hierarchy
3. The verify and quality-gate evidence packets
4. `quality/criteria.md` for phase-exit criteria

## Routes to

- `.github/agents/phase-implementation-assess.agent.md`

## Steps

1. Compare current state to phase-exit criteria.
2. Confirm all gate-critical paths in this phase have meaningful verification.
3. Confirm no scope was silently dropped.
4. Confirm follow-up work has been recorded against the right phase.
5. Issue a verdict: phase complete | phase incomplete | phase exceeded.

## Stop conditions

- A phase-exit criterion is missing or ambiguous
- Quality gate has not yet passed
- Scope changed without a spec or plan update

## Output

```text
Phase:
Exit criteria evaluated:
Material progress:
Silently dropped scope:
Verdict (complete | incomplete | exceeded):
Recommended next phase or remediation:
Next command:
```
