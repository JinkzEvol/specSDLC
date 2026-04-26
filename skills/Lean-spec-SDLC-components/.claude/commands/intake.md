---
description: Intake a new feature signal before spec synchronization and planning.
mode: "command"
invokes:
  prompt: ".github/prompts/receive-feature-signal.prompt.md"
  agent: ".github/agents/sdlc-orchestrator.agent.md"
---

# Intake

Invoke `.github/prompts/receive-feature-signal.prompt.md` to process a new feature signal.
If accepted, route follow-on work through `.github/agents/sdlc-orchestrator.agent.md`.
