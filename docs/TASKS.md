# OpsPilot — Dependency-Ordered Task Backlog

Task size: S (small), M (medium), L (large). Only tasks with satisfied dependencies and disjoint file ownership should execute in parallel. **Do not start the whole backlog at once.**

| ID | Task | Depends on | Size | Parallel-safe |
| --- | --- | --- | --- | --- |
| P00 | ADRs: monorepo, DB ORM, validation, auth boundary; write threat model | — | S | No (design gate) |
| P01 | Repo skeleton: pnpm workspace, NestJS API, Next.js web, Docker Compose, lint/typecheck | P00 | M | No |
| P02 | CI workflow, env example and developer setup guide | P01 | S | Yes with P03 after contracts |
| P03 | Canonical Task DTO/schema and PostgreSQL migration | P01 | M | No (shared contracts) |
| P04 | Manual task REST CRUD, status transitions, input validation | P03 | M | Yes with P05 once contracts fixed |
| P05 | Dashboard list/create/edit/detail flows | P03 | M | Yes with P04 (mock API contract) |
| P06 | Integration tests, UI smoke and end-to-end V0 review | P02,P04,P05 | M | No (release gate) |
| P07 | Work calendar: hours, leave, meetings and deduplication | P06 | M | Yes with P08 after model review |
| P08 | External source models + synthetic Jira Software/JSM adapters | P06 | M | Yes with P07 |
| P09 | Capacity budgets and deterministic allocation engine | P07,P08 | L | No |
| P10 | Capacity dashboard, conflict explanations and date-range views | P09 | M | No |
| P11 | Authorized Jira read-only sync with rate limiting/pagination | P08,P10 | L | Human approval |
| P12 | AgentRunner contract + MockRunner and immutable execution records | P06 | M | Yes with P07/P08 |
| P13 | Approval policies and persisted state machine | P12 | L | No |
| P14 | Sandbox CLI adapter, bounded resources, command policy | P13 | L | Human security review |
| P15 | Agent runs/approval dashboard and audit evidence | P13 | M | Yes with P14 after contracts |
| P16 | Parallel Code integration feasibility spike (document supported API only) | P12 | S | Yes |
| P17 | Authenticated alternative task API/CLI | P06 | M | Yes with P12 |
| P18 | Optional LLM suggestions and evaluation harness | P11,P13 | L | Human data review |
| P19 | Staging demo, docs, measurements and release-hardening | P10,P15 | L | No |

## Standard task template (copy into issues)
**Goal:** One observable, user-visible outcome.

**Files/modules:** Specify ownership before start; avoid conflicting parallel changes.

**Dependencies:** IDs and merged contracts required.

**Acceptance criteria:** Given/when/then behavior, edge cases, rejected inputs and restart behavior.

**Tests:** Unit, integration and UI as appropriate; all commands documented.

**Safety:** Synthetic fixtures only unless separately authorized; no secrets or privileged writes.

**Deliverable:** One reviewed PR with summary, screenshots/logs, tests run, limitations and next steps.

## Start here
1. Execute **P00** only; propose 2–4 ADRs and an initial threat model.
2. Review P00 and choose the minimal stack.
3. Execute P01, then P02/P03, then P04/P05, then P06.
4. Keep V1/V2/V3 tasks parked until V0 is green.
