# Lean Spec SDLC Components

This folder is a portable, lean transplant kit derived from the live SDLC system in this repository.

It is designed to be copied into another repo and then regrow repo-specific behavior by detecting the local environment instead of assuming any single product's structure.

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

1. `docs/ENVIRONMENT_PROFILE.md` if present
2. `docs/SYSTEM_STATE.md` if present
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
3. Fill out `docs/ENVIRONMENT_PROFILE.md`.
4. Update `docs/SYSTEM_STATE.md`.
5. Adjust agent lists to match real domains in the target repo.
6. Run the orchestrator first for the first real feature or bug.

## Key outputs in this package

- [SOURCE_MAP.md](SOURCE_MAP.md)
- [COMPONENT_MANIFEST.md](COMPONENT_MANIFEST.md)
- [ASSEMBLY_REPORT.md](ASSEMBLY_REPORT.md)
- [SWOT_ANALYSIS.md](SWOT_ANALYSIS.md)

