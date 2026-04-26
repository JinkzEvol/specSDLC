# Parallel Agent Work Partitioning Protocol

Operator-facing companion to `kit/.github/instructions/sdlc-workflow.instructions.md`.

This protocol partitions a repo into ownership lanes so multiple AI coding agents can work in parallel without merge collisions, contract drift, or cross-lane rework. It is agnostic to product domain — the lane list is filled in per repo from the environment profile.

## Work Packet Header

Every implementation packet must declare:

```text
Primary lane:
Allowed edit paths:
Forbidden edit paths:
Contracts consumed:
Contracts changed:
Coordination files:
Phase:
User-visible outcome:
Files allowed to change:
Files not allowed to change:
Dependency budget:
Tests to write first:
Stop conditions:
```

If any field is unclear, stop and produce a packet variance note instead of editing code.

## Work Lanes

A lane is a single ownership area defined by:

- the kind of asset it owns (UI, contracts, data, infra, docs, tests, CI, etc.)
- the file paths it primarily edits
- the contracts it may consume but not silently change

The lane list is repo-specific. Derive it from the actual repo structure recorded in `docs/ENVIRONMENT_PROFILE.md`. Every lane gets a stable lane ID (e.g. `LANE-PLATFORM`, `LANE-UI`, `LANE-CONTRACTS`) and is documented in this file, not invented per-packet.

### Generic lane template

| Lane ID | Owns | Primary Paths | May Consume |
|---|---|---|---|
| `LANE-PLATFORM` | Root workspace manifests, repo-wide scripts, shared config, bootstrap wiring | manifest files, root config | read-only inputs from all lanes |
| `LANE-UI` | User-facing app(s), client rendering, presentation layer | app source paths | shared contracts |
| `LANE-CONTRACTS` | Schemas, shared types, contract fixtures | contract package paths | none |
| `LANE-API` | Backend routes, request handlers, auth bridge | service/edge/worker paths | shared contracts, generated types |
| `LANE-INTEGRATIONS` | External-service wrappers, mock providers, integration fixtures | client/wrapper package paths | shared contracts |
| `LANE-CORE` | Domain logic, orchestration, pipelines | core service paths | shared contracts, integration clients |
| `LANE-DATA` | Schema, migrations, seeds, row-level rules | database/migration paths | system spec |
| `LANE-EVAL` | Examples, eval runners, adversarial fixtures | examples/, eval app paths | traces, shared contracts |
| `LANE-VERIFY` | Contract tests, CI, architecture consistency checks | tests/, ci/, workflow paths | all contracts read-only |
| `LANE-SPEC` | Specs, build packets, status docs, ADRs, quality rules | docs/, decisions/, knowledge/, quality/ | all evidence packets |

Replace, rename, add, or delete rows to fit the target repo. Add lanes for product-specific domains (mobile, desktop, ML, hardware, firmware, embedded, etc.) when their asset boundaries don't fit the template.

### Workflow path note

Some hosts treat `.github/workflows/**` as the canonical CI path. If your bootstrap uses a different casing or location, document it here as the intentional seed and treat any later migration as its own coordination task.

## Core Rules

1. One primary lane per task.
2. Cross-lane implementation edits are prohibited unless the packet is marked `integration_packet: true` and explicitly human-approved.
3. Shared contracts are owned by `LANE-CONTRACTS` (or your repo's equivalent).
4. Consumer lanes may not silently change shared contracts to make local tests pass.
5. Prefer additive changes over rewrites.
6. No broad refactors, formatting sweeps, folder restructures, or dependency upgrades unless the packet explicitly calls for them.
7. Only `LANE-SPEC` may mutate `docs/status/**` directly. All other lanes must emit evidence packets that are consumed by the next spec-lane status packet.

## Coordination Files

Treat these as high-conflict files. Touching one demands a packet declaration and a minimal diff:

- root package manifests (e.g. `package.json`, `pnpm-workspace.yaml`, `pyproject.toml`, `Cargo.toml`, `go.mod`)
- root lockfiles (e.g. `pnpm-lock.yaml`, `package-lock.json`, `poetry.lock`)
- shared TypeScript / linting / test config (e.g. `tsconfig.base.json`, `eslint.config.js`, `vitest.workspace.ts`)
- runtime config that crosses environments (e.g. `wrangler.jsonc`, `serverless.yml`, `Dockerfile`, `docker-compose.yml`)
- platform / database config (e.g. `supabase/config.toml`, `prisma/schema.prisma`)
- CI / automation (`.github/workflows/**`, `Makefile`, `Taskfile.yml`)
- the root `README.md`

If a task touches one, declare it in the packet and keep the diff as small as possible.

## Contract-First Flow

Cross-lane changes must move in this order:

1. contract packet
2. producer packet
3. consumer packet
4. integration packet
5. verify packet

Example: adding a new shared schema means the contracts lane defines the schema first, then the producer emits it, then the consumer reads it, then verify checks the round trip.

## Dependency Budget

A packet may add at most one new runtime dependency. The packet must record:

- purpose
- package name
- exact pinned version
- alternatives considered
- security impact
- affected deployable
- removal plan if the dependency proves unnecessary

## Stop Conditions

Stop and emit a packet variance note if:

- the task requires touching files outside the allowed paths
- the required contract does not exist yet
- the task would change auth, integrations, and UI in the same packet
- ownership of a trust boundary or contract is unclear
- a test would need to be skipped to pass
- frontend code appears to require service-role secrets or core internals
- the next best action is unclear given current `docs/SYSTEM_STATE.md`

## Required Evidence Packet

Every implementation response must end with:

```text
Changed paths:
Primary lane:
Contracts consumed:
Contracts changed:
Tests added:
Tests run:
Coordination files touched:
Known risks:
Spec variances:
Next recommended packet:
```

## Recommended Bootstrap Packet Order

When bootstrapping a new repo with this kit, sequence packets so each lane lands a thin vertical slice before any lane is fully fleshed out. A typical order:

1. `BOOT-001` — Workspace skeleton and shared config (`LANE-PLATFORM`)
2. `BOOT-002` — First shared contract (`LANE-CONTRACTS`)
3. `BOOT-003` — Minimal UI shell (`LANE-UI`)
4. `BOOT-004` — Mock integration wrapper (`LANE-INTEGRATIONS`)
5. `BOOT-005` — Health and demo endpoint (`LANE-API`)
6. `BOOT-006` — First example or golden flow (`LANE-EVAL`)
7. `BOOT-007` — Contract consistency checks (`LANE-VERIFY`)
8. `BOOT-008` — Status and gate evidence baseline (`LANE-SPEC`)

Renumber, rename, or replace these to match your real first milestone.
