# Architecture decision records

Add numbered ADRs here. Initial candidates:

- ADR-001: pnpm monorepo + NestJS/Next.js modular monolith rather than microservices.
- ADR-002: PostgreSQL and one migration/ORM tool (evaluate Prisma vs Drizzle).
- ADR-003: REST/OpenAPI and versioned shared DTO contracts.
- ADR-004: single-user local development boundary now; OIDC and object-level authorization before shared deployment.

Each ADR must capture context, options, decision, tradeoffs and consequences. Do not choose a production auth shortcut merely to accelerate V0.
