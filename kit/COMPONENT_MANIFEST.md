# Component Manifest

## Core control plane

- `.github/agents/sdlc-orchestrator.agent.md`
- `.github/agents/build-lead.agent.md`
- `.github/instructions/sdlc-workflow.instructions.md`
- `.github/instructions/environment-regrowth.instructions.md`
- `.claude/commands/orchestrate.md`

## Spec creators

- `.github/agents/change-impact.agent.md`
- `.github/agents/planner.agent.md`
- `.github/agents/spec-guardian.agent.md`
- `.github/agents/architect.agent.md`
- `.github/agents/database-reviewer.agent.md`

## Stage operatives

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

## Domain leads

- `.github/agents/platform-lead.agent.md`
- `.github/agents/security-lead.agent.md`
- `.github/agents/quality-lead.agent.md`
- `.github/agents/observability-lead.agent.md`

## Prompt surface

- `.github/prompts/orchestrate.prompt.md`
- `.github/prompts/receive-feature-signal.prompt.md`
- `.github/prompts/sync-external-spec.prompt.md`
- `.github/prompts/plan-feature.prompt.md`
- `.github/prompts/verify-phase.prompt.md`
- `.github/prompts/prepare-for-deployment.prompt.md`
- `.github/prompts/execute-deployment.prompt.md`
- `.github/prompts/broadcast-state.prompt.md`

## Command surface

The slash commands mirror the pipeline phases. Each command names the agent and prompt it routes to, the files it must read first, its stop conditions, and an evidence-packet output schema.

- `.claude/commands/orchestrate.md` — next best action, control plane
- `.claude/commands/receive-signal.md` — pipeline entry, intake
- `.claude/commands/sync-spec.md` — spec hierarchy update
- `.claude/commands/impact.md` — blast radius and change impact
- `.claude/commands/plan.md` — implementation plan
- `.claude/commands/compliance.md` — pre-code spec guardian gate
- `.claude/commands/tdd.md` — test-driven implementation
- `.claude/commands/code-review.md` — correctness and lane discipline
- `.claude/commands/security-review.md` — auth, secrets, trust boundaries
- `.claude/commands/verify.md` — build, tests, structural checks
- `.claude/commands/regression.md` — baseline regression
- `.claude/commands/quality-gate.md` — binary pass/fail gate
- `.claude/commands/phase-assess.md` — phase-exit assessment
- `.claude/commands/prepare-deploy.md` — deployment readiness
- `.claude/commands/deploy.md` — deployment execution
- `.claude/commands/broadcast.md` — state broadcast + state file refresh
- `.claude/commands/learn.md` — promote durable lessons
- `.claude/commands/checkpoint.md` — preserve clean evidence-backed snapshots

## State and learning layer

- `docs/SYSTEM_STATE.template.md`
- `docs/ENVIRONMENT_PROFILE.template.md`
- `docs/BOOTSTRAP_CHECKLIST.md`
- `.github/memories/memory-episode-template.md`
- `knowledge/INDEX.md`
- `knowledge/sdlc/rules.md`
- `decisions/README.md`
- `quality/criteria.md`

