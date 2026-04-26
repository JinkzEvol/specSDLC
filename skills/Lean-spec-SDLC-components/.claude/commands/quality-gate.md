---
description: Run the binary quality gate using verification and compliance evidence.
mode: "command"
invokes:
  agent: ".github/agents/quality-gate.agent.md"
---

# Quality Gate

Invoke `.github/agents/quality-gate.agent.md` for the gate verdict.
Binary pass or fail gate after verify.

Use the active specs, review outputs, security findings, and `quality/criteria.md` to decide whether work can advance.
