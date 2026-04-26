---
description: "Portable deployment readiness and execution checklist."
applyTo: "**"
---

# Deployment Checklist

## Normalize scope first

- target environment
- deploy boundary
- intended outcome
- rollout limits

## Pre-deploy checks

- real deploy commands are known
- secrets and auth requirements are clear
- config parity across environments is verified
- migrations or infra changes are scoped correctly
- verification method matches the service type

## Safe fix policy

Safe fixes are small, reversible deployment corrections that are clearly implied by existing repo intent.

Do not make destructive or scope-expanding changes under a safe-fix label.

## Reporting minimums

- environment
- scope
- blockers
- warnings
- fixes applied
- verdict
- next actions

