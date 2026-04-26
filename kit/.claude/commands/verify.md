---
description: "Run build, tests, and structural checks using the repo's real commands."
argument-hint: "Phase, milestone, or change scope"
---

# /verify

Run the repo's real build or typecheck, tests, and routing or packaging checks using the commands discovered from `docs/ENVIRONMENT_PROFILE.md`. Block on failures. Report evidence, not guesses.

## Always read first

1. `docs/ENVIRONMENT_PROFILE.md` for build, test, and packaging commands
2. `.github/instructions/testing-standards.instructions.md`
3. `quality/criteria.md`

## Routes to

- `.github/agents/verify.agent.md`
- `.github/prompts/verify-phase.prompt.md`

## Steps

1. Run build or typecheck.
2. Run tests.
3. Run spec compliance checks.
4. Run regression checks (or hand off to `/regression`).
5. Produce one overall verdict: pass, pass-with-warnings, or fail.
6. On any failure, stop and report. Do not continue to `/quality-gate`.

## Stop conditions

- Build, typecheck, or tests fail
- A required check command is missing from the environment profile
- A previously-green test now fails without an in-scope explanation

## Output

```text
Phase:
Build result:
Test result:
Spec compliance result:
Regression result:
Verdict:
Failures with file:line references:
Next command:
```
