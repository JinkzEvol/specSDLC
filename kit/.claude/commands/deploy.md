---
description: "Execute a scoped deployment with readiness checks and controlled reporting."
argument-hint: "Environment and scope"
---

# /deploy

Execute mode for the deployment agent. Run only after `/prepare-deploy` returns `ready`.

## Always read first

1. The readiness packet from `/prepare-deploy`
2. `.github/instructions/deployment-checklist.instructions.md`
3. `docs/ENVIRONMENT_PROFILE.md` for real deployment commands
4. `docs/SYSTEM_STATE.md`

## Routes to

- `.github/agents/deployment.agent.md` (execute mode)
- `.github/prompts/execute-deployment.prompt.md`

## Steps

1. Re-run readiness checks immediately before execution.
2. Stay strictly within the requested scope.
3. Execute the deployment using the real commands.
4. Capture deploy IDs, versions, and timestamps.
5. Run post-deploy smoke checks.
6. Separate blockers from warnings.
7. Issue a hard verdict and `/broadcast`.

## Stop conditions

- Readiness re-check fails
- Scope drift requested mid-execution
- Smoke check fails after deploy

## Output

```text
Environment:
Scope:
Commands run:
Deploy IDs / versions / timestamps:
Smoke check result:
Blockers:
Warnings:
Verdict (success | partial | failed):
Rollback initiated (yes | no):
Next command:
```
