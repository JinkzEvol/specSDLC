---
description: "Execute a scoped deployment with readiness checks and controlled reporting."
mode: "agent"
---

# Execute Deployment: {{input}}

Run the deployment agent in execute mode.

Requirements:

- perform readiness checks first
- stay within requested scope
- separate blockers from warnings
- finish with a hard verdict and next actions

