---
name: sdlc-system-transplant
description: "Portable playbook for transplanting an SDLC orchestration system into another repo. Explains spec creators, SDLC operatives, supervisors/viewers, prompts, tools, harness enhancements, memories, self-improvement, and the orchestrate kickoff flow."
---

# SDLC System Transplant

Use this skill when you want to move a mature SDLC orchestration system from one repository to another, preserve the enforcement model, and keep the new repo aligned with spec-first delivery.

This skill is both an explanation and a transplant guide. It describes how the system works, how the orchestration entrypoint behaves, and what to copy or adapt in the next repository.

## Companion Component Pack

This skill now has a companion transplant pack at:

- `./Lean-spec-SDLC-components/`

That folder contains the lean portable agents, prompts, commands, instructions, state templates, memory scaffolds, source map, assembly report, and SWOT analysis needed to bootstrap the workflow in another repository.

## Lean Baseline Exclusions

The lean kit intentionally omits some specialist leads from the full-source narrative:

- `Extraction Lead` (add when ingestion or parsing pipelines become a first-class domain)
- `Enrichment Lead` (add when enrichment tables, queue write paths, or backfills are active)
- `MCP Lead` (add when tool contracts and runtime MCP surfaces need dedicated ownership)
- `Regulatory Ethics Lead` (add when regulated or ethics-sensitive criteria require explicit gate ownership)

Add these only when the target repository shows recurring work in those areas.

## 1. What The System Is

This system is a layered agent workflow for production-grade engineering work.

It separates work into four cooperating layers:

- Spec creators define the work before implementation starts.
- SDLC operatives execute the required stage work.
- Supervisors/viewers review evidence, approve gates, and watch for regressions.
- The orchestration layer decides which agent should act next and in what order.

The design goal is simple:

- keep specs ahead of code
- keep execution stage-aware
- keep gate approvals evidence-driven
- keep lessons durable through memories, instructions, and agent updates

## 2. The Main Roles

### Spec Creators

Spec creators shape the work before implementation.
They are used when the right answer is not code yet, but scope, risk, and acceptance.

Typical spec creators include:

- `SDLC Orchestrator` when the request spans multiple stages or the owner is unclear
- `Change Impact` when you need blast-radius analysis
- `Planner` when you need an implementation plan with Critical Control Points
- `Spec Guardian` when you need spec compliance checking before implementation
- `Architect` when you need system design or platform reasoning
- `Database Reviewer` when the change touches schema, migrations, or SQL design
- `Security Reviewer` when the change touches auth, secrets, tenant isolation, or public exposure

What they do:

- convert a request into a scoped plan
- identify affected specs, tests, and dependencies
- surface blockers early
- prevent implementation from outrunning the spec

### SDLC Operatives

SDLC operatives do the stage work once the scope is known.
They are the agents that execute the workflow.

Typical operatives include:

- `TDD Guide` for RED/GREEN/REFACTOR discipline
- `Verify` for typecheck, tests, and routing completeness
- `Quality Gate` for binary pass/fail gate assessment
- `phase-implementation-assess` for phase transitions and hard gatekeeping
- `Regression Sentinel` for baseline regression detection
- `deployment` for staged deployment readiness and execution
- `Learn` for post-deployment knowledge extraction
- `Postmortem Agent` for incident analysis and durable lesson capture
- `Process Engineer` for log-based process mining and bottleneck diagnosis

What they do:

- execute a single stage or a tightly defined stage family
- produce hard evidence
- keep the workflow honest about pass/fail boundaries
- convert failures into reusable learning

### Supervisors / Viewers

Supervisors and viewers own evidence quality, domain approval, and operational oversight.
They are not replacements for the stage agents; they prepare, review, and troubleshoot the work so the stage agents can make reliable decisions.

Typical supervisors/viewers include:

- `Build Lead` for go/no-go, waivers, workstream readiness, and cross-spec coordination
- `Extraction Lead` for OCR, parser, prompt-template, and extractor handoff integrity
- `Enrichment Lead` for enriched tables, views, backfill, and queue-driven write paths
- `MCP Lead` for tool contracts, data domains, feature flags, tiering, and runtime surface
- `Security Lead` for auth, RLS, secrets, tenant isolation, and exposure restrictions
- `Platform Lead` for Wrangler, queues, cron, bindings, D1, KV, and deploy blockers
- `Observability Lead` for logs, error codes, soak evidence, and runtime visibility
- `Quality Lead` for acceptance evidence, CT coverage, golden sets, and regression readiness
- `Regulatory Ethics Lead` for safety language, forbidden attributes, and ethics review evidence

What they do:

- gather evidence before a gate
- confirm the right domain owns the decision
- keep approvals tied to real proof
- coordinate cross-domain blockers without hijacking stage execution

## 3. How The Orchestrate Kickoff Works

The orchestrate entrypoint is the cleanest way to start when the work is bigger than a single stage.

### Kickoff flow

1. Read the live system state first.
2. Identify whether the request is feature work, a bug fix, a refactor, a release, or an incident.
3. Decide whether the work is narrow or multi-stage.
4. If the domain is unclear, invoke `Change Impact` to map the blast radius.
5. Invoke the owning domain lead or leads to gather evidence.
6. Use `Planner` only when the next step is actually planning.
7. Use `Spec Guardian` before implementation starts.
8. Move into `TDD Guide`, review, security review, verify, quality-gate, phase assessment, regression, deployment, broadcast, and learning as needed.
9. If a durable lesson emerges, route it into memories, instructions, or agent files.

### Default rule

If there is any real doubt about scope, ownership, or stage sequencing, start with `SDLC Orchestrator`.

That means:

- do not jump straight to `Planner` if the request really spans planning plus implementation plus gates
- do not jump straight to `Verify` if the change still needs scope or evidence gathering
- do not let a domain lead absorb the whole lifecycle when the work crosses stages

### Orchestrator behavior

`SDLC Orchestrator` is the control plane, not the implementation stage.
It should:

- choose the right starting agent
- enforce stage order
- call the owning domain leads first when evidence is needed
- call the formal stage agents last when a verdict is needed
- route durable lessons into the right system files when the user wants follow-through

## 4. Prompts, Commands, And Entry Points

A strong orchestration system has both agents and commands.

### Common prompts

Use prompts for structured entry points that deserve a consistent workflow.
Examples:

- feature intake and external signal routing
- spec synchronization
- planning
- verify-phase checks
- deployment readiness and execution
- broadcast-state updates

### Common commands

Commands are the user-facing hooks into the system.
A good transplant usually includes commands such as:

- `/orchestrate` for the SDLC Orchestrator
- `/plan` for planning-only work
- `/tdd` for test-first implementation
- `/verify` for build and test verification
- `/quality-gate` for binary gate assessment
- `/checkpoint` for workflow checkpoints
- `/learn` for post-deployment learning extraction

### Best practice

Keep command intent narrow.
If a request spans multiple stages, route to orchestration instead of making every command do everything.

## 5. Tool Model

The system uses tools to make the agents effective and precise.

### Common tool groups

- `read` and `search` for evidence gathering
- `edit` for narrow, explicit file changes
- `execute` or terminal access for validation and controlled command execution
- `todo` for progress tracking
- `agent` for delegation to other agents

### Tool discipline

- Read before editing.
- Edit only after the workflow is scoped.
- Use execution tools for validation, not speculation.
- Prefer delegation over overloading a single agent.
- Keep supervisor agents focused on evidence and approvals, not broad execution.

## 6. Harness Enhancements That Make The System Work

The agent layer is only part of the harness.
The rest of the system is what makes the workflow discoverable and enforceable.

### Core harness assets

- `docs/SYSTEM_STATE.md` or the repo equivalent as the live state record
- `docs/` or equivalent spec hierarchy for PRD, architecture, phase specs, and plans
- `.github/instructions/` or equivalent workflow instructions
- `.github/prompts/` or equivalent stage prompts
- `.github/agents/` or equivalent agent definitions
- `.claude/commands/` for slash-command entry points
- `knowledge/` for durable patterns and rules
- `decisions/` for architecture and process decisions
- `quality/criteria.md` for reusable gate criteria
- `.github/memories/` for incident and lesson history

### Why harness enhancements matter

Without the harness, the agents are just text files.
With the harness, they become a workflow system:

- prompts create consistent entry points
- commands make the workflow easy to start
- instructions keep the whole system aligned
- memories preserve lessons
- decisions preserve rationale
- quality criteria preserve repeated failure patterns
- system state gives the next session a factual starting point

## 7. Memories And Self-Improvement

The self-improvement loop is what keeps the system from forgetting its own lessons.

### Memory layer

Use memories for concrete lessons and repeatable incident classes.
Good memory artifacts capture:

- what happened
- what actually failed
- what the root cause was
- what was fixed
- what remains unverified
- what should be remembered next time

### Knowledge layer

Use `knowledge/` for durable patterns, hypotheses, and rules.
Examples:

- a recurring deployment failure mode
- a repeated telemetry blind spot
- a reliable stage sequencing rule
- a domain-specific troubleshooting pattern

### Decisions layer

Use `decisions/` for choices that affect future work.
Examples:

- why one agent owns a domain boundary
- why a workflow uses a particular sequencing rule
- why a gate needs a particular evidence packet

### Quality criteria layer

Use `quality/criteria.md` for failure patterns that should become recurring checks.
This is where repeated problems turn into gates.

### Self-improvement flow

1. An incident or release exposes a repeatable pattern.
2. A postmortem or process analysis identifies the durable lesson.
3. The lesson is written to memory, knowledge, decisions, or quality criteria.
4. If the pattern affects workflow or ownership, the relevant agent or instruction is updated.
5. The orchestrator uses that updated system on the next run.

### Best practice

Do not update broad workflow files for one-off noise.
Only promote lessons when the evidence says the issue is durable enough to matter again.

## 8. How To Transplant The System Into Another Repo

This is the practical transplant sequence.

### Step 1: Create the orchestration entrypoint

Add the orchestrator command and make it the default entrypoint for ambiguous work.

Minimum pieces:

- `SDLC Orchestrator` agent
- `/orchestrate` command
- a workflow instruction file that explains when to use orchestrator vs direct agents

### Step 2: Create the stage agents

Add the minimum set of stage agents for your repo.
The usual baseline is:

- `Planner`
- `Spec Guardian`
- `TDD Guide`
- `Code Reviewer`
- `Security Reviewer`
- `Verify`
- `Quality Gate`
- `Regression Sentinel`
- deployment agent
- `Learn`
- `Postmortem Agent`
- `Process Engineer`

### Step 3: Add domain supervisors

Add domain leads only for the areas the repo actually owns.
Do not clone unnecessary domains.

Typical domains:

- build / release
- data / database
- platform / deploy
- observability / logs
- quality / acceptance
- security / auth
- product-domain specialists

### Step 4: Wire the docs

Add or update the instruction files that describe:

- SDLC order
- when to use orchestrator
- how stage agents differ from domain leads
- how lessons flow into memory and agent updates

### Step 5: Add memory and learning paths

Create the persistence layer for lessons:

- `knowledge/`
- `decisions/`
- `quality/`
- `memories/`

### Step 6: Make the command inventory discoverable

Add the command list so the workflow is easy to start:

- `/orchestrate`
- `/plan`
- `/verify`
- `/quality-gate`
- `/learn`
- any repo-specific entry points

### Step 7: Add a state file

Keep one live source of truth for:

- current phase
- blockers
- deployment state
- gate state
- current release or sprint

### Step 8: Add self-improvement rules

Define when a lesson becomes:

- a memory
- a knowledge rule
- a decision record
- a quality criterion
- an agent update
- an instruction update

## 9. Best Practices To Preserve

These are the rules worth carrying into the next repo.

- Keep the orchestrator as the default for multi-stage work.
- Keep direct stage agents narrow and explicit.
- Make domain leads evidence-focused, not workflow owners.
- Require domain leads to gather evidence before formal gates.
- Keep the formal stage agent as the last authoritative pass/fail step.
- Put durable lessons into memory, knowledge, or instructions instead of relying on chat history.
- Update the smallest file that truly owns the lesson.
- Use explicit default-bias language so users know where to start.
- Keep stage routing and domain routing separate.
- Treat the live state file as the first thing to read before making decisions.
- Use recurring incident patterns to drive agent and instruction updates.
- Prefer lean, role-specific agents over giant all-in-one agents.
- Preserve discoverability in descriptions, command names, and instruction headers.

## 10. What Not To Do

- Do not let planner become an orchestrator.
- Do not let build lead become a full lifecycle agent.
- Do not let change-impact suggest implementation.
- Do not make every agent aware of every other agent.
- Do not promote one-off mistakes into global workflow law.
- Do not skip the state file.
- Do not skip the memory layer when a lesson is durable.
- Do not replace formal stage agents with vague supervisory language.

## 11. Portable Transplant Checklist

Use this as the quick drop-in list for the next repo.

- [ ] Add `SDLC Orchestrator`
- [ ] Add `/orchestrate`
- [ ] Add planner/spec-guardian/tdd/review/verify/gate/regression/deploy/learn agents
- [ ] Add domain leads for the repo's real subsystems
- [ ] Add workflow instructions for stage order and routing
- [ ] Add live state file
- [ ] Add memories, decisions, knowledge, and quality files
- [ ] Add a command index or prompt surface
- [ ] Add self-improvement rules for recurring incidents
- [ ] Add default-bias language that tells users when to use orchestrator
- [ ] Keep the stage agents and domain leads distinct

## 12. Short Mental Model

Think of the system like this:

- `SDLC Orchestrator` decides the route.
- Spec creators define the route.
- SDLC operatives walk the route.
- Supervisors/viewers confirm the route is safe.
- Memories and knowledge preserve what the route taught you.

If the next repo needs the same discipline, transplant the route, the gatekeepers, and the learning loop together.
