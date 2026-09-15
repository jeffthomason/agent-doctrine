# 04 — Do Not Touch

Files, folders, or systems that are off-limits by default. An agent should not edit these without explicit, specific instruction to do so in the current task — general instructions like "clean up the codebase" do not count as permission.

<!-- Fill in for your actual project. Examples: -->

- `.env` / any file containing secrets or credentials
- Production configuration files
- Auto-generated files (state clearly which ones, and where the real source lives)
- Database migration history (edit forward with new migrations, don't rewrite old ones)
- Anything under a vendor's managed/synced directory (e.g. a no-code tool's owned folder) that isn't actually yours to edit
- CI/CD pipeline definitions, unless the task is specifically about CI/CD
- Billing/payment provider configuration

## Why this file exists

Agents are helpful by default, which means they'll sometimes "fix" something adjacent to the actual task. This file exists so that helpfulness has a boundary. If something here genuinely needs to change, that's a stop-condition (see `03-stop-conditions.md`), not a silent edit.
