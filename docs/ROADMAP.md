# OpsPilot — Implementation Roadmap

The [product specification](PROJECT.md) is the scope source of truth. Dates are estimates, not commitments. Implement in vertical slices with documented acceptance criteria; no real organizational data until approved.

## Milestone 0 — Secure foundation and design
- [ ] Architecture decision records for modular monolith, storage, auth boundary, API contracts, tenant scope.
- [ ] Threat model for untrusted issue content, secret storage, agent execution and approvals.
- [ ] Local developer experience: monorepo, lint/typecheck, Docker Compose PostgreSQL, CI.
**Exit:** Clean setup with reproducible CI, no secrets and documented local startup.

## Milestone 1 — V0: First runnable vertical slice
- [ ] Health endpoint + OpenAPI.
- [ ] Task entity and migration; create/list/detail/update/complete.
- [ ] Basic responsive dashboard and task forms.
- [ ] Validation, API tests, UI smoke test and CI.
**Exit:** New manual task persists across restarts, can be completed, invalid input rejected; CI green.

## Milestone 2 — V1: Useful personal planner
- [ ] Work calendar and net capacity incl. leave/meetings overlap.
- [ ] Configurable incident budget (default 30%) and sprint budget.
- [ ] Deterministic daily allocation with due dates, dependencies and explainable overload reports.
- [ ] Mock Jira Software + JSM ingestion; source identity and deduplication.
- [ ] Authorized **read-only** real Jira integration, isolated from demo fixtures.
**Exit:** Valid cross-month sprint planning, no invented SLAs, reliable reconciliation, actionable dashboard.

## Milestone 3 — V2: Safe agent operation
- [ ] Mock AgentRunner and persisted execution state machine.
- [ ] Human approval requests tied to action fingerprint, expiry and actor permissions.
- [ ] Audit events, timeouts, bounded retries, sandbox boundaries.
- [ ] One reviewed local CLI adapter; integrate Parallel Code only if supported and verified.
**Exit:** Synthetic agent task pauses, survives restart, denies unauthorized approval, resumes with audit evidence; no production changes.

## Milestone 4 — V3: Other channels and intelligence
- [ ] Authenticated CLI/API task intake and draft confirmation.
- [ ] Optional chat/email webhook adapters with authentication and replay protection.
- [ ] AI-generated suggestions tied to source references, evaluation tests and bounded permissions.
**Exit:** Secure multi-channel draft intake, evidence-backed suggestions, approvals remain explicit.

## Working method
- Prefer one feature branch or isolated worktree per task.
- Never parallelize tasks sharing schema/contracts until interfaces are merged.
- Report changed files, tests, risks and scope on each PR.
- No automatic merges, corporate system modifications or production deploy without explicit user approval.
