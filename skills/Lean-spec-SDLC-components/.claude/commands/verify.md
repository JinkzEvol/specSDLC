---
description: Run verification checks and return an evidence-backed pass or fail verdict.
mode: "command"
invokes:
  prompt: ".github/prompts/verify-phase.prompt.md"
  agent: ".github/agents/verify.agent.md"
---

# Verify

Invoke `.github/agents/verify.agent.md` via `.github/prompts/verify-phase.prompt.md`.
Run the repo's build or typecheck, tests, and routing or packaging checks using commands from `docs/ENVIRONMENT_PROFILE.md`.

Block on failures. Report evidence, not guesses.
