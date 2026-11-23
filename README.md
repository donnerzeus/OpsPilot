# OpsPilot

**AI-Native Work & Engineering Orchestration Platform**  
Status: Planning / pre-MVP · Started November 2026

OpsPilot is a local-first, human-supervised work orchestration platform that combines Jira sprint work, service-management incidents and custom tasks. It helps plan monthly capacity, manage deadlines and SLAs, and later coordinate coding agents with explicit approval checkpoints.

> **Safety:** No real organizational data, credentials, agent executions or production integrations are enabled in the initial release. Public fixtures are synthetic.

## What it aims to do

- **Unified inbox:** Jira Software, Jira Service Management and manual tasks; eventually chat, email, CLI and webhooks.
- **Capacity planner:** configurable working calendar, leave/meetings, incident allocation (default 30%) and remaining sprint capacity.
- **Prioritization:** deadlines, SLA, dependencies, effort estimates and over-capacity warnings.
- **Agent orchestration:** pluggable Claude Code, Codex, Gemini CLI runners and potential Parallel Code integration, subject to supported interfaces.
- **Human-in-the-loop:** explicit approvals for risk-bearing changes, auditable decisions and safe workflow resumption.

## Planned stack

TypeScript · NestJS · Next.js · PostgreSQL · Docker Compose · GitHub Actions. Redis/BullMQ and OpenTelemetry will be added when the corresponding asynchronous workflows need them.

## Development milestones

| Phase | Outcome |
| --- | --- |
| V0 | Custom task CRUD, persistent Postgres storage, basic dashboard and CI |
| V1 | Read-only Jira integration, capacity and scheduling planner |
| V2 | Safe agent runners, workflow approvals and audit trail |
| V3 | Authenticated alternate task intake and AI-assisted suggestions |

## Project documents

- [Product and technical specification](docs/PROJECT.md)
- [Implementation roadmap](docs/ROADMAP.md)
- [Dependency-ordered task backlog](docs/TASKS.md)
- [Security principles](docs/SECURITY.md)
- [Architecture decisions](docs/decisions/README.md)

## Getting started

The project is in planning; application scaffolding has not been implemented yet. Read [the roadmap](docs/ROADMAP.md) and implement the first vertical slice before adding integrations or AI execution.

## Security and contribution notes

Never commit tokens, session data or organizational ticket content. Use synthetic demo data and mock adapters. Any organization integration requires explicit authorization and an approved environment. No automatic PR merge, production deployment or privileged action without human approval.

## License

Not decided yet.
