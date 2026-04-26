---
description: "Create or list workflow checkpoints — clean, evidence-backed snapshots of system state."
argument-hint: "Label or 'list'"
---

# /checkpoint

Create, verify, or list workflow checkpoints. Checkpoints preserve clean evidence-backed points in long-running work so the system can resume without re-deriving state.

## Always read first

1. `docs/SYSTEM_STATE.md`
2. The most recent verify, quality-gate, and phase-assess evidence
3. Any open packet variance notes

## Steps

1. If the action is `list`, print the existing checkpoints recorded in `docs/SYSTEM_STATE.md`.
2. If creating, confirm the system is at a clean point: `/verify` green, no uncommitted variance notes, no open blockers.
3. Snapshot: pipeline position, last passed gate, active specs, environment profile hash, and outstanding evidence.
4. Append the checkpoint to `docs/SYSTEM_STATE.md` under a Checkpoints section.

## Stop conditions

- Verify is not green
- Open packet variance notes
- The requested checkpoint label already exists

## Output

```text
Action (create | list | verify):
Checkpoint label:
Pipeline position:
Last passed gate:
Active specs:
Environment profile hash:
Outstanding evidence:
Next command:
```
