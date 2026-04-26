---
description: Route work through the SDLC Orchestrator when scope, ownership, or stage order is unclear.
mode: "command"
invokes:
  agent: ".github/agents/sdlc-orchestrator.agent.md"
---

# Orchestrate

Use this command for multi-stage work, incidents, releases, or unclear ownership.
This command is a thin wrapper over the SDLC Orchestrator agent.

## Process

1. Invoke `.github/agents/sdlc-orchestrator.agent.md`.
2. Let the orchestrator read state and environment evidence.
3. Let the orchestrator route to domain leads and stage agents.
4. Keep stage order and gate sequencing evidence-driven.
