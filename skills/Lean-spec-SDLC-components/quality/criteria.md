# Quality Criteria

Use this file for recurring blocking or warning criteria that the quality gate should apply.

## Category: Build Integrity

### Criterion: Build or typecheck must pass
- Severity: blocking
- Source: verification gate
- Last triggered: never

### Criterion: Test baseline must not regress
- Severity: blocking
- Source: testing standards
- Last triggered: never

## Category: Spec Compliance

### Criterion: Spec guardian must report no blocking contradictions
- Severity: blocking
- Source: stage 3
- Last triggered: never

## Category: Security

### Criterion: No hardcoded secrets
- Severity: blocking
- Source: security standards
- Last triggered: never

## Category: Code Quality

### Criterion: Critical files stay maintainable
- Severity: warning
- Source: coding standards
- Last triggered: never

## Category: Platform Fit

### Criterion: Runtime and deployment constraints are respected
- Severity: blocking
- Source: deployment checklist
- Last triggered: never
