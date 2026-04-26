---
description: Assess deployment readiness for a scoped environment and rollout.
mode: "command"
invokes:
  prompt: ".github/prompts/prepare-for-deployment.prompt.md"
  agent: ".github/agents/deployment.agent.md"
---

# Prepare Deploy

Invoke `.github/prompts/prepare-for-deployment.prompt.md`.
Run `.github/agents/deployment.agent.md` in readiness mode only.
