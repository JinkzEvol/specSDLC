---
description: "Portable spec SDLC workflow with evidence-driven gates."
applyTo: "**"
---

# SDLC Workflow

Use `SDLC Orchestrator` when work spans multiple stages, crosses domains, or the correct owner is unclear.

## Pipeline

External signal -> spec sync -> change impact -> planning -> spec guardian -> TDD
-> code review -> security review -> verify -> quality gate
-> phase assessment -> regression -> deployment -> broadcast -> learn

## Stage rules

1. Update or confirm specs before implementation.
2. Run blast-radius analysis before planning when scope is non-trivial.
3. Run spec compliance before coding.
4. Use TDD for implementation and bug fixes.
5. Gather domain evidence before formal gates.
6. Treat missing evidence as gate failure.
7. Update state after gates and deployment.
8. Promote durable lessons into memory, knowledge, decisions, instructions, or agents.

## Domain lead rule

Domain leads prepare evidence and approvals. Formal stage agents issue the stage verdict.

## Default bias

If there is any real doubt, start with the orchestrator.

