---
description: "Create an implementation plan with control points, assumptions, and risks."
argument-hint: "Feature, change, or scope to plan"
---

# /plan

Use when the request is planning-only. If the work extends into implementation or gate sequencing, route through `/orchestrate` instead.

## Always read first

1. `docs/ENVIRONMENT_PROFILE.md`
2. `docs/SYSTEM_STATE.md`
3. The active specs identified for the scope
4. `.github/instructions/sdlc-workflow.instructions.md`

## Routes to

- `.github/agents/planner.agent.md`
- `.github/prompts/plan-feature.prompt.md`

## Steps

1. Confirm the spec is current. If not, route to `/sync-spec` first.
2. Run `/impact` if blast radius is non-trivial.
3. Produce a plan with phases, control points, assumptions, risks, dependencies, and exit criteria.
4. Run `/compliance` against the plan before any implementation begins.
5. Save the plan to the repo's agreed planning location (named in the environment profile).

## Stop conditions

- Spec is missing, ambiguous, or contradicts another active spec
- Required contracts are undefined
- Plan would cross multiple lanes without an integration packet
- A risk has no mitigation or owner

## Output

```text
Scope:
Specs referenced:
Phases:
Control points:
Assumptions:
Risks and mitigations:
Dependencies:
Exit criteria per phase:
Lane(s) involved:
Recommended next command:
```
