---
description: "Sync a new requirement or proposal into the target repo's spec hierarchy before implementation."
argument-hint: "Accepted signal or external requirement"
---

# /sync-spec

Update or extend the spec hierarchy before any implementation begins. Specs are the source of truth — implementation is judged against them, not the other way around.

## Always read first

1. `docs/ENVIRONMENT_PROFILE.md` for the spec hierarchy location
2. The current spec(s) covering the affected area
3. `docs/SYSTEM_STATE.md`
4. `.github/instructions/sdlc-workflow.instructions.md`

## Routes to

- `.github/prompts/sync-external-spec.prompt.md`
- `.github/agents/spec-guardian.agent.md`

## Steps

1. Locate the affected spec documents.
2. Draft the spec update with explicit additions, modifications, and removals.
3. Run `/compliance` against the intended changes.
4. On clean compliance, commit the spec update.
5. Update `docs/SYSTEM_STATE.md` to reflect the new spec position.
6. Hand off to `/plan`.

## Stop conditions

- Spec hierarchy location is not declared in the environment profile
- The proposed change conflicts with another spec without resolution
- Compliance fails

## Output

```text
Affected spec(s):
Change summary (added | modified | removed):
Compliance verdict:
Spec update committed (yes | no):
SYSTEM_STATE update applied:
Next command:
```
