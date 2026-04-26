---
description: "Structured intake for a new feature, bug, or external signal before spec sync."
argument-hint: "Signal source and short description"
---

# /receive-signal

First entry point in the pipeline. Triage a new signal, decide whether it's accepted, queued, or blocked, and update state.

## Always read first

1. `docs/SYSTEM_STATE.md` for blockers and active phase
2. `docs/ENVIRONMENT_PROFILE.md`
3. The current milestone or release commitment

## Routes to

- `.github/prompts/receive-feature-signal.prompt.md`

## Steps

1. Capture source, requestor, signal type (feature | bug | external requirement | incident).
2. Check `SYSTEM_STATE.md` for blockers that pause new intake.
3. Assess phase or milestone fit.
4. Flag obvious compatibility concerns with active specs.
5. Decide: accept | queue | block | reject.
6. On accept, hand off to `/sync-spec`.
7. Update `docs/SYSTEM_STATE.md` regardless of decision.

## Stop conditions

- Required information about the signal is missing
- Phase fit cannot be assessed without spec work first
- The signal contradicts an in-flight commitment

## Output

```text
Signal source:
Requestor:
Type:
Decision (accept | queue | block | reject):
Phase fit:
Compatibility concerns:
Next command:
SYSTEM_STATE update applied:
```
