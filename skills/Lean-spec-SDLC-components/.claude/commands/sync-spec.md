---
description: Sync external requirements into the repo spec hierarchy before implementation.
mode: "command"
invokes:
  prompt: ".github/prompts/sync-external-spec.prompt.md"
  agent: ".github/agents/spec-guardian.agent.md"
---

# Sync Spec

Invoke `.github/prompts/sync-external-spec.prompt.md` to update affected specs first.
Run `.github/agents/spec-guardian.agent.md` before implementation handoff.
