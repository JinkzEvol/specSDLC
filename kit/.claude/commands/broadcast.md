---
description: "Generate a state broadcast and refresh the live system state file."
argument-hint: "Audience or 'internal'"
---

# /broadcast

Run after `/deploy` or at the close of a phase. Produces a concise, evidence-backed update for stakeholders and refreshes `docs/SYSTEM_STATE.md`.

## Always read first

1. `docs/SYSTEM_STATE.md`
2. The most recent verify, quality-gate, phase-assess, and deploy evidence
3. Open blockers and risk register
4. The audience target if specified

## Routes to

- `.github/prompts/broadcast-state.prompt.md`

## Steps

1. Gather recent activity, gate outcomes, deploy results, and blockers.
2. Compare current evidence to `docs/SYSTEM_STATE.md`.
3. Produce a broadcast tailored to the audience: leadership, engineering, customer-facing, or internal.
4. Update `docs/SYSTEM_STATE.md`.
5. Hand off to `/learn` if the phase is closing.

## Stop conditions

- Evidence is missing for a claim in the broadcast
- `docs/SYSTEM_STATE.md` is stale
- A blocker is being broadcast as resolved without verification

## Output

```text
Audience:
Recent activity:
Gate outcomes:
Deploy results:
Open blockers:
Broadcast text:
SYSTEM_STATE update applied:
Next command:
```
