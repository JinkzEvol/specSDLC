---
description: "Extract durable lessons from completed work, incidents, or gate failures."
argument-hint: "Source episode (commit, incident, gate failure)"
---

# /learn

Extract reusable patterns from completed work, incidents, and gate failures. Write durable lessons to the memory, knowledge, decision, and quality layers as appropriate.

## Always read first

1. The source episode (commit, incident report, gate failure, or postmortem)
2. `.github/memories/memory-episode-template.md`
3. `knowledge/INDEX.md`
4. `decisions/README.md`
5. `quality/criteria.md`

## Routes to

- `.github/agents/learn.agent.md`

## Steps

1. Identify the episode and the surprise it contains.
2. Classify the lesson: memory (situational), knowledge (general principle), decision (durable choice), instruction (process change), or quality criterion (gate update).
3. Write the lesson to the right layer using the layer's conventions.
4. If the lesson changes a gate, file a quality-criteria update and notify `/quality-gate`.
5. Cross-link related entries.

## Stop conditions

- The episode is not yet closed
- The surprise is not yet articulated in one sentence
- The lesson would belong in more than one layer (split it instead)

## Output

```text
Episode:
Surprise:
Layer (memory | knowledge | decision | instruction | quality):
File created or updated:
Cross-links:
Gate or instruction impact:
Next command:
```
