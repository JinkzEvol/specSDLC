---
description: "Portable testing standards for spec SDLC, evidence-driven delivery."
applyTo: "**"
---

# Testing Standards

## Required ideas

- Write tests before or alongside risky implementation.
- Preserve or improve the current baseline.
- Test critical contracts, not just helpers.
- Cover failure paths, not only happy paths.
- Use the repo's real test commands from `docs/ENVIRONMENT_PROFILE.md`.

## Minimum expectations

- build or typecheck is green
- existing tests remain green
- changed behavior has direct test coverage
- gate-critical paths have meaningful verification

