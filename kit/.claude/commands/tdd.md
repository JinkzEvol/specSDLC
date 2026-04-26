---
description: "Enforce test-driven development for risky or behavior-changing work."
argument-hint: "Behavior or contract under change"
---

# /tdd

Use to identify critical contracts, write failing tests first, implement minimally, and refactor safely. Required for any behavior-changing work.

## Always read first

1. `docs/ENVIRONMENT_PROFILE.md` for the real test commands
2. `.github/instructions/testing-standards.instructions.md`
3. `.github/instructions/coding-standards.instructions.md`
4. The plan or spec the change is implementing

## Routes to

- `.github/agents/tdd-guide.agent.md`

## Steps

1. Identify the contract or behavior under change.
2. Write the failing test first using the repo's real test runner.
3. Confirm the test fails for the right reason.
4. Implement the smallest change that turns the test green.
5. Refactor under green tests only.
6. Run the full local suite before handing off.

## Stop conditions

- Test would need to be skipped or marked pending to pass
- Test depends on a mock that masks a contract under verification
- Implementation requires touching files outside the lane
- Required contract does not exist (route to `/sync-spec`)

## Output

```text
Contract or behavior under change:
Test(s) added:
Test command run:
Local suite result:
Files changed:
Lane:
Coordination files touched:
Next command:
```
