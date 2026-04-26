# Lean Spec SDLC Components

This folder is a portable, lean transplant kit derived from the live SDLC system in this repository.

It is designed to be copied into another repo and then regrow repo-specific behavior by detecting the local environment instead of assuming GxP Sentinel structure.

## What is included

- `.github/agents/` for orchestration, planning, review, gates, deployment, and learning
- `.github/prompts/` for structured workflow entrypoints
- `.github/instructions/` for SDLC order, standards, deployment checks, and environment regrowth
- `.claude/commands/` for slash-command entrypoints
- `docs/` templates for system state and environment profiling
- `.github/memories/`, `knowledge/`, `decisions/`, and `quality/` seed files for the self-improvement loop
- assembly documentation, source mapping, and outcome analysis

## Design goals

1. Preserve spec-first orchestration.
2. Keep stage agents narrow.
3. Keep domain leads evidence-focused.
4. Let the package start generic and regain specificity by reading the target repo.

## Regrowth model

On first use in a new repo, the transplanted system should read:

1. `docs/ENVIRONMENT_PROFILE.md` if present, otherwise `docs/ENVIRONMENT_PROFILE.template.md`
2. `docs/SYSTEM_STATE.md` if present, otherwise `docs/SYSTEM_STATE.template.md`
3. root `README*`
4. package manifests such as `package.json`, `pnpm-workspace.yaml`, `pyproject.toml`, `Cargo.toml`, `go.mod`
5. CI and automation files such as `.github/workflows/*`, `Makefile`, `Taskfile.yml`
6. infra/runtime config such as Docker, Terraform, Helm, serverless, worker, or deployment files
7. test config and test directories
8. architecture and product docs under `docs/`

That evidence should be written back into `docs/ENVIRONMENT_PROFILE.md` and then used by the agents instead of hardcoded assumptions.

## Suggested transplant flow

1. Copy this folder tree into the target repo root.
2. Rename or merge the inner directories into the repo's real `.github/`, `.claude/`, `docs/`, `knowledge/`, `decisions/`, and `quality/` paths.
3. Create `docs/ENVIRONMENT_PROFILE.md` from `docs/ENVIRONMENT_PROFILE.template.md` and fill it out.
4. Create `docs/SYSTEM_STATE.md` from `docs/SYSTEM_STATE.template.md` and update it.
5. Adjust agent lists to match real domains in the target repo.
6. Run the orchestrator first for the first real feature or bug.

## Routing matrix

- `/orchestrate` -> prompt: n/a -> agent: `sdlc-orchestrator` -> state: `docs/SYSTEM_STATE.md`, `docs/ENVIRONMENT_PROFILE.md` -> output: routed stage plan and next-agent decision
- `/intake` -> prompt: `receive-feature-signal` -> agent: `sdlc-orchestrator` -> state: `docs/SYSTEM_STATE.md` -> output: intake accepted, queued, or blocked
- `/sync-spec` -> prompt: `sync-external-spec` -> agent: `spec-guardian` -> state: `docs/SYSTEM_STATE.md` and spec hierarchy -> output: spec updates with compliance handoff
- `/plan` -> prompt: `plan-feature` -> agents: `planner`, `change-impact`, `spec-guardian` -> state: planning location and `docs/SYSTEM_STATE.md` -> output: scoped implementation plan with control points
- `/tdd` -> prompt: n/a -> agent: `tdd-guide` -> state: tests and implementation files -> output: RED/GREEN/REFACTOR evidence
- `/verify` -> prompt: `verify-phase` -> agent: `verify` -> state: verification artifacts and `docs/SYSTEM_STATE.md` -> output: verification verdict with failure evidence
- `/quality-gate` -> prompt: n/a -> agent: `quality-gate` -> state: `quality/criteria.md` and `docs/SYSTEM_STATE.md` -> output: binary pass or fail gate verdict
- `/checkpoint` -> prompt: n/a -> agent: `phase-implementation-assess` -> state: `docs/SYSTEM_STATE.md` -> output: transition readiness checkpoint
- `/prepare-deploy` -> prompt: `prepare-for-deployment` -> agent: `deployment` -> state: `docs/SYSTEM_STATE.md` and deployment notes -> output: readiness decision and blockers
- `/execute-deploy` -> prompt: `execute-deployment` -> agent: `deployment` -> state: `docs/SYSTEM_STATE.md` and deployment artifacts -> output: deployment execution verdict
- `/broadcast` -> prompt: `broadcast-state` -> agent: `build-lead` -> state: `docs/SYSTEM_STATE.md` -> output: stakeholder state broadcast
- `/learn` -> prompt: n/a -> agent: `learn` -> state: `.github/memories/`, `knowledge/`, `decisions/`, `quality/criteria.md` -> output: durable lessons and proposed system updates

## Key outputs in this package

- [SOURCE_MAP.md](SOURCE_MAP.md)
- [COMPONENT_MANIFEST.md](COMPONENT_MANIFEST.md)
- [ASSEMBLY_REPORT.md](ASSEMBLY_REPORT.md)
- [SWOT_ANALYSIS.md](SWOT_ANALYSIS.md)
