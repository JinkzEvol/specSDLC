# Source Map

This package was assembled from the live SDLC assets in the current repository and rewritten into portable forms.

## Primary source files used

### Agents

- `.github/agents/sdlc-orchestrator.agent.md`
- `.github/agents/change-impact.agent.md`
- `.github/agents/planner.agent.md`
- `.github/agents/spec-guardian.agent.md`
- `.github/agents/tdd-guide.agent.md`
- `.github/agents/code-reviewer.agent.md`
- `.github/agents/security-reviewer.agent.md`
- `.github/agents/verify.agent.md`
- `.github/agents/quality-gate.agent.md`
- `.github/agents/phase-implementation-assess.agent.md`
- `.github/agents/regression-sentinel.agent.md`
- `.github/agents/deployment.agent.md`
- `.github/agents/learn.agent.md`
- `.github/agents/postmortem.agent.md`
- `.github/agents/process-engineer.agent.md`
- `.github/agents/build-lead.agent.md`
- `.github/agents/platform-lead.agent.md`
- `.github/agents/security-lead.agent.md`
- `.github/agents/quality-lead.agent.md`
- `.github/agents/observability-lead.agent.md`

### Instructions

- `.github/instructions/sdlc-workflow.instructions.md`
- `.github/instructions/coding-standards.instructions.md`
- `.github/instructions/testing-standards.instructions.md`
- `.github/instructions/security-standards.instructions.md`
- `.github/instructions/deployment-checklist.instructions.md`

### Prompts

- `.github/prompts/orchestrate.prompt.md`
- `.github/prompts/receive-feature-signal.prompt.md`
- `.github/prompts/sync-external-spec.prompt.md`
- `.github/prompts/plan-feature.prompt.md`
- `.github/prompts/verify-phase.prompt.md`
- `.github/prompts/prepare-for-deployment.prompt.md`
- `.github/prompts/execute-deployment.prompt.md`
- `.github/prompts/broadcast-state.prompt.md`

### Commands

The slash command set mirrors the pipeline so each phase has a discoverable entrypoint.

- `.claude/commands/orchestrate.md`
- `.claude/commands/receive-signal.md`
- `.claude/commands/sync-spec.md`
- `.claude/commands/impact.md`
- `.claude/commands/plan.md`
- `.claude/commands/compliance.md`
- `.claude/commands/tdd.md`
- `.claude/commands/code-review.md`
- `.claude/commands/security-review.md`
- `.claude/commands/verify.md`
- `.claude/commands/regression.md`
- `.claude/commands/quality-gate.md`
- `.claude/commands/phase-assess.md`
- `.claude/commands/prepare-deploy.md`
- `.claude/commands/deploy.md`
- `.claude/commands/broadcast.md`
- `.claude/commands/learn.md`
- `.claude/commands/checkpoint.md`

### State and memory seeds

- `docs/SYSTEM_STATE.md`
- `quality/criteria.md`
- `.github/memories/memory-episode-template.md`
- `knowledge/INDEX.md`
- `decisions/README.md`

## Rewrite strategy

- Replaced product-specific paths with repo-discovery instructions.
- Removed host-, platform-, regulatory-, and integration-specific assumptions unless they were reusable patterns.
- Preserved stage order, evidence-first gating, and self-improvement semantics.
- Added an explicit environment-regrowth layer so the kit can become specific again in a new repo.
- Kept the lean baseline small enough to transplant without cloning every domain-specific lead.

