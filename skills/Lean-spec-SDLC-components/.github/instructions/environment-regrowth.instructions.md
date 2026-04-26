---
description: "How transplanted SDLC assets regain repo-specific behavior after landing in a new repository."
applyTo: "**"
---

# Environment Regrowth

The transplanted SDLC system starts generic on purpose. It becomes specific by reading the target repository before making strong assumptions.

## Read in this order

1. `docs/ENVIRONMENT_PROFILE.md` if present
2. `docs/SYSTEM_STATE.md` if present
3. root `README*`
4. `docs/` product, architecture, phase, and operations docs
5. package manifests and toolchain files
6. CI and automation files
7. deployment and infrastructure config
8. tests and coverage config

## Build the environment profile

Capture and keep current:

- repo purpose and primary domain
- runtime and deployment model
- source roots and test roots
- spec hierarchy
- typecheck, build, test, coverage, and deploy commands
- quality baselines and gate expectations
- domain leads actually needed
- critical platform or compliance limits

## Rules

- Prefer evidence from the repo over inherited assumptions.
- If a source-era concept does not exist in the target repo, replace it with the local equivalent.
- If a command is unknown, mark it unverified instead of inventing one.
- Prune irrelevant domain leads quickly.
- Add product-specific leads only when the repo proves they are needed.

