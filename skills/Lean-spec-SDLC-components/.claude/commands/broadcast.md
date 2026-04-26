---
description: Publish a concise workflow state broadcast and refresh system state.
mode: "command"
invokes:
  prompt: ".github/prompts/broadcast-state.prompt.md"
  agent: ".github/agents/build-lead.agent.md"
---

# Broadcast

Invoke `.github/prompts/broadcast-state.prompt.md` to generate a stakeholder update.
Use `.github/agents/build-lead.agent.md` when cross-workstream coordination is required.
