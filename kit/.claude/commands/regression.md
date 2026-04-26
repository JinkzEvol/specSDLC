---
description: "Regression check — confirm the previous baseline still holds end-to-end."
argument-hint: "Phase or change scope"
---

# /regression

Run after `/verify` passes the immediate change, before `/quality-gate`. Confirms that nothing the change should not have affected has actually changed.

## Always read first

1. The recorded baseline (golden flows, regression suites named in `docs/ENVIRONMENT_PROFILE.md`)
2. The set of changed paths in scope
3. `quality/criteria.md` for regression criteria

## Routes to

- `.github/agents/regression-sentinel.agent.md`

## Steps

1. Run the recorded regression suite using the real test command.
2. Run any golden flows or example traces named in the environment profile.
3. Compare results against the previous green baseline.
4. Investigate any divergence and tie it to a changed path or declare it unrelated.
5. Issue a verdict: clean | regression detected | flaky.

## Stop conditions

- The regression suite itself has been edited in this packet
- The baseline is undefined
- A regression cannot be tied to a changed path or marked as flaky with evidence

## Output

```text
Baseline:
Suites run:
Divergences:
Tied to changed paths (yes | no | partial):
Verdict (clean | regression | flaky):
Next command:
```
