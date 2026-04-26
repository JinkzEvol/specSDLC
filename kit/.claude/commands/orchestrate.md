---
description: "Compute the next best action and route work toward the active destination."
argument-hint: "Scope, blocker, or desired outcome"
---

# /orchestrate

Use for multi-stage work, incidents, releases, or unclear ownership. This command keeps the system travelling toward its destination by selecting the next best action from current state instead of from chat momentum.

## Always read first

1. `docs/ENVIRONMENT_PROFILE.md`
2. `docs/SYSTEM_STATE.md`
3. `.github/instructions/sdlc-workflow.instructions.md`
4. `.github/instructions/environment-regrowth.instructions.md`
5. The active specs and operating docs named in the environment profile

## Routes to

- `.github/agents/sdlc-orchestrator.agent.md`
- `.github/prompts/orchestrate.prompt.md`

## Steps

1. Locate the destination — current milestone, gate, or release commitment. If none, route to `/receive-signal` or `/sync-spec`.
2. Locate current pipeline position and outstanding evidence.
3. Compute the gap to destination in pipeline order: spec sync → change impact → planning → spec guardian → TDD → code review → security review → verify → quality gate → phase assessment → regression → deployment → broadcast → learn.
4. Pick the earliest unblocked stage with missing evidence. Do not skip ahead.
5. Hand off to the named agent or slash command with explicit scope, expected evidence, and the gate it unblocks.
6. Update `docs/SYSTEM_STATE.md` after the routed work returns.

## Stop conditions

- Required stage was skipped or its evidence is missing
- A required contract does not exist yet
- Ownership of a trust boundary or contract is unclear
- The destination in `SYSTEM_STATE.md` is stale or absent

## Output

```text
Destination:
Current pipeline position:
Outstanding evidence:
Active blockers:
Next best action:
Chosen agent or command:
Why this and not something earlier or later:
Gate unblocked by this action:
Stop conditions triggered:
Recommended follow-up:
```
