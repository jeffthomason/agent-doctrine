# ADR-000: Example — Use Managed Postgres Instead of Self-Hosted

- Status: Accepted
- Date: 2026-01-15
- Decision owner: (you)

## Context

The project needs a production database. The team is solo/small and does not want to own database ops (backups, patching, failover) on top of everything else.

## Decision

Use a managed Postgres provider (e.g. Supabase, Neon, RDS) for production. Local development uses a Docker Postgres instance with the same schema, kept in sync via migrations.

## Alternatives considered

### Option A: Self-hosted Postgres on a VPS

Full control, lowest recurring cost, but adds real operational burden (backups, security patching, uptime) that a solo team can't reliably absorb right now.

### Option B: Managed Postgres provider

Higher monthly cost than self-hosting, but removes ops burden entirely and includes backups/failover out of the box.

### Option C: Use a non-relational database instead

Would avoid the schema-migration overhead entirely, but the data is genuinely relational (users, orders, relationships between them), and forcing it into a document store would create more problems than it solves.

## Trade-offs

Option B costs more per month than self-hosting but removes a category of risk (data loss from a missed backup, downtime from a botched patch) that would be expensive in a different way — time and trust, not dollars. For a solo team, time is the scarcer resource.

## Consequences

All schema changes must go through versioned migrations, checked into the repo — no manual schema edits against production. Local dev must stay schema-compatible with production via the same migration files.

## Security, privacy, and cost impact

Managed provider handles encryption at rest and automated backups. Monthly cost scales with usage — revisit if it becomes a significant % of revenue.

## Revisit trigger

Revisit if monthly database cost exceeds $200 before the product has meaningful revenue, or if the managed provider's reliability becomes a recurring problem.
