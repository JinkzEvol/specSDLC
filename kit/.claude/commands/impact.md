---
description: "Run blast-radius and impact analysis before planning."
argument-hint: "Change scope under consideration"
---

# /impact

Use before `/plan` when scope is non-trivial. Identifies affected lanes, contracts, gates, and downstream consumers.

## Always read first

1. `docs/ENVIRONMENT_PROFILE.md`
2. The active spec(s) covering the change
3. `agent-work-partitioning.md` (if present at the repo root) for the lane map
4. The contract definitions in the affected lane(s)

## Routes to

- `.github/agents/change-impact.agent.md`

## Steps

1. List affected lanes by file path.
2. List shared contracts the change consumes or modifies.
3. Identify downstream consumers of any modified contract.
4. Identify gates and verification steps that must re-run.
5. Identify coordination files that may need editing.
6. Surface stop conditions for `/plan`.

## Stop conditions

- A modified contract has unidentifiable downstream consumers
- The change spans more than one lane without an integration-packet rationale
- Coordination files would require unbounded edits

## Output

```text
Affected lanes:
Contracts consumed:
Contracts modified:
Downstream consumers:
Gates that must re-run:
Coordination files touched:
Stop conditions surfaced:
Recommended packet shape (single-lane | integration | contract-first sequence):
Next command:
```
