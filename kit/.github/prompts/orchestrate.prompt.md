---
description: "Determine the next best action and route work to keep the system moving toward its destination."
mode: "agent"
---

# Orchestrate: {{input}}

Use this prompt to keep work travelling toward the active destination — the next milestone, gate, or release commitment — by computing the single next best action from current state, not from chat momentum.

## Always read first

1. `docs/ENVIRONMENT_PROFILE.md`
2. `docs/SYSTEM_STATE.md`
3. `.github/instructions/sdlc-workflow.instructions.md`
4. The active specs and operating docs named in the environment profile

## Steps

1. **Locate the destination.** Identify the current milestone, gate, or release commitment from `docs/SYSTEM_STATE.md`. If none is set, stop and route to `receive-feature-signal` or `sync-external-spec`.
2. **Locate current position.** Identify the last completed pipeline stage, outstanding blockers, evidence still owed, and any open packet variance notes.
3. **Compute the gap.** List what must still happen between current position and the destination, in pipeline order: spec sync, change impact, planning, spec guardian, TDD, code review, security review, verify, quality gate, phase assessment, regression, deployment, broadcast, learn.
4. **Pick the next best action.** Choose the single next stage and the agent that owns it. Prefer the earliest unblocked stage that has missing evidence. Do not skip ahead.
5. **Check stop conditions.** Refuse to advance if a required stage was skipped, a contract is undefined, evidence is missing, ownership is unclear, or the destination itself is stale.
6. **Route.** Hand off to the chosen agent or prompt with explicit scope, expected evidence, and the gate it unblocks.
7. **Update state.** When the routed work returns, update `docs/SYSTEM_STATE.md` with the new position and re-run this prompt for the following step.

## Output

```text
Destination:
Current pipeline position:
Outstanding evidence:
Active blockers:
Next best action:
Chosen agent or prompt:
Why this and not something earlier or later:
Gate unblocked by this action:
Stop conditions triggered:
Recommended follow-up:
```

## Bias

If there is real doubt about the next best action, prefer the earlier, narrower stage. Skipping forward is the most common way the system drifts off destination.
