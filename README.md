# spec SDLC

A portable, spec-driven SDLC system for AI-assisted software delivery — built around narrow agents, evidence-driven gates, and a transplant kit that regrows itself in any repo.

> Spec SDLC is the methodology. The kit in this repo is the implementation.

## What's in this repo

| Path | What it is |
|---|---|
| [`spec-sdlc-explainer.html`](./spec-sdlc-explainer.html) | Self-contained visual explainer — open it in a browser. Walks through the four-layer architecture, all 22 agents, the 15-stage pipeline, the lane-partitioning technique, a worked transplant example, and the self-improvement loop. |
| [`agent-work-partitioning.md`](./agent-work-partitioning.md) | Operator-facing protocol for partitioning a repo into ownership lanes so multiple AI coding agents can work in parallel without merge collisions or contract drift. |
| [`kit/`](./kit/) | The Lean Spec SDLC Components transplant kit — 55 files of agents, prompts, instructions, slash-commands, state templates, and seed knowledge/decisions/quality files. Designed to be copied into any target repo. |

## What "spec SDLC" actually is

Most SDLC systems ask one big agent to plan, code, review, gate, and deploy. The seams collapse, evidence gets skipped, and the system drifts.

Spec SDLC takes the opposite shape:

- **Specs are the source of truth.** Specs are written and updated *before* implementation. Implementation is judged against the spec, not against vibes.
- **Narrow agents with hard verdicts.** Each stage of the pipeline (change-impact, planning, spec-guardian, TDD, code review, security, verify, quality gate, etc.) is its own agent with its own scope and a strict pass/fail output.
- **Domain leads prepare evidence; stage agents issue verdicts.** Domain leads (build, platform, security, quality, observability) gather and curate evidence. Formal stage agents return verdicts. The two roles never blur.
- **The orchestrator is the control plane.** It sequences stages, calls the right specialist, and refuses to skip steps even when the work looks small.
- **Evidence-driven gates.** Missing evidence is gate failure — not "we'll come back to it."
- **Lanes for parallel-safe work.** The repo is partitioned into ownership lanes with declared edit boundaries, contract flow, and a dependency budget. Multiple agents can work in parallel without stepping on each other.
- **Self-improvement loop.** Lessons get promoted into memory, knowledge, decisions, instructions, or new agents through human-approved PRs — not chat history.

The HTML explainer in this repo is the friendliest way to see how all of that fits together.

## How the kit is meant to be used

The kit in [`kit/`](./kit/) is a *transplant package*. It ships generic, reads the target repo, then regrows repo-specific behavior. The flow:

1. Copy `kit/`'s contents into the root of your target repo, merging into the real `.github/`, `.claude/`, `docs/`, `knowledge/`, `decisions/`, and `quality/` paths.
2. Fill out `docs/ENVIRONMENT_PROFILE.md` from the templates so agents know your real toolchain instead of guessing.
3. Fill out `docs/SYSTEM_STATE.md` with your active phase, blockers, and deployment posture.
4. Adjust the agent list in [`kit/.github/agents/sdlc-orchestrator.agent.md`](./kit/.github/agents/sdlc-orchestrator.agent.md) to match the real domains in your repo.
5. Run the orchestrator against your first real feature or bug to validate routing.

For a deeper walk-through, see:

- [`kit/README.md`](./kit/README.md) — kit-level overview and design goals
- [`kit/COMPONENT_MANIFEST.md`](./kit/COMPONENT_MANIFEST.md) — full inventory
- [`kit/SOURCE_MAP.md`](./kit/SOURCE_MAP.md) — where each component came from
- [`kit/ASSEMBLY_REPORT.md`](./kit/ASSEMBLY_REPORT.md) — what was kept, what was deliberately omitted
- [`kit/SWOT_ANALYSIS.md`](./kit/SWOT_ANALYSIS.md) — strengths, weaknesses, threats
- [`kit/docs/BOOTSTRAP_CHECKLIST.md`](./kit/docs/BOOTSTRAP_CHECKLIST.md) — transplant runbook

## Pipeline at a glance

```
external signal -> spec sync -> change impact -> planning -> spec guardian -> TDD
              -> code review -> security review -> verify -> quality gate
              -> phase assessment -> regression -> deployment -> broadcast -> learn
```

Fifteen stages, each with a designated agent. The orchestrator picks the right entry point and refuses to skip ahead.

## The four layers

1. **Control plane** — the orchestrator and a small number of build/platform leads that route work and own evidence aggregation.
2. **Spec creators** — the agents and prompts that author and update specs.
3. **Stage operatives** — the narrow stage agents that issue verdicts.
4. **Domain leads** — security, quality, observability, platform, etc. — preparing evidence ahead of formal gates.

The explainer HTML walks each layer with the cards and the agent grid.

## Lanes

Lanes are how you split a repo so multiple agents can work in parallel without rework. The kit doesn't prescribe a fixed lane list — `agent-work-partitioning.md` shows the technique with an example 10-lane partition you can adapt.

Every implementation packet declares its primary lane, allowed and forbidden edit paths, contracts consumed and changed, coordination files, dependency budget, and stop conditions. Cross-lane edits require an explicit integration packet.

## Status

This is the published, version-controlled snapshot of the kit and its explainer. The kit lives here; downstream repos transplant it and regrow it locally.

## License

MIT — see [LICENSE](./LICENSE).
