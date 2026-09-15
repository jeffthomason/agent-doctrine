# 03 — Stop Conditions

Stop and ask for direction before proceeding if a task requires any of the following. Guessing on these is how projects end up with silent security holes, surprise bills, or unrecoverable data loss.

<!-- This starter list covers common cases. Add project-specific ones — e.g. anything touching money, auth, or physical/real-world effects belongs here. -->

- New payment or billing logic
- New third-party service credentials or API keys
- Changes to the permission/role model
- Database schema changes or migrations that could affect existing data
- Anything that would break an existing public route, API contract, or integration
- Introducing a new major dependency, framework, or backend provider
- Large-scale rewrites of a system that currently works
- Anything irreversible (deleting data, deleting infrastructure, revoking access)
- Public-facing legal/policy text (terms of service, privacy policy, pricing)

## What "stop" actually means

Stop before implementing, not after. Describe what you're about to do and why, and wait for confirmation — don't do it and mention it in the output summary as a fait accompli.
