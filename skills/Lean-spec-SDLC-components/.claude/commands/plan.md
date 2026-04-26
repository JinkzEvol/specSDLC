---
description: Create an implementation plan with control points, assumptions, and risks.
mode: "command"
invokes:
  prompt: ".github/prompts/plan-feature.prompt.md"
  agent: ".github/agents/planner.agent.md"
---

# Plan

Use this command when the request is planning-only.
This command wraps the plan-feature prompt and planner flow.

If the work extends into implementation or gate sequencing, use `/orchestrate` instead.
