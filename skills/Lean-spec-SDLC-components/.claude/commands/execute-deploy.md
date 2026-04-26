---
description: Execute a scoped deployment with readiness checks and hard verdict output.
mode: "command"
invokes:
  prompt: ".github/prompts/execute-deployment.prompt.md"
  agent: ".github/agents/deployment.agent.md"
---

# Execute Deploy

Invoke `.github/prompts/execute-deployment.prompt.md`.
Run `.github/agents/deployment.agent.md` in execute mode with explicit blockers and warnings.
