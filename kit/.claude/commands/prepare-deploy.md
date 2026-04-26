---
description: "Assess deployment readiness for the target environment and scope."
argument-hint: "Environment and scope"
---

# /prepare-deploy

Readiness mode for the deployment agent. Does not execute. Use before `/deploy`.

## Always read first

1. `docs/ENVIRONMENT_PROFILE.md` for deployment commands and environments
2. `.github/instructions/deployment-checklist.instructions.md`
3. The most recent `/quality-gate` and `/phase-assess` evidence
4. `docs/SYSTEM_STATE.md`

## Routes to

- `.github/agents/deployment.agent.md` (readiness mode)
- `.github/prompts/prepare-for-deployment.prompt.md`

## Steps

1. Normalize environment, scope, rollout strategy, and constraints.
2. Confirm the deployment checklist is satisfied.
3. Confirm rollback steps are recorded.
4. Confirm `/regression` and `/quality-gate` are green for this scope.
5. Issue a readiness verdict: ready | not ready.

## Stop conditions

- Required environment commands missing from the environment profile
- Rollback plan absent
- Quality gate or regression not green

## Output

```text
Environment:
Scope:
Rollout strategy:
Constraints:
Checklist status:
Rollback plan:
Verdict (ready | not ready):
Next command:
```
