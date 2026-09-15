# AGENTS.md

This is the entry point for any AI coding agent working in this repository. Read this file and the files it links to *before* planning or writing any code.

## Read in this order

1. `.ai/00-project-identity.md` — what this project is, who it's for, what it explicitly is not
2. `.ai/01-current-state.md` — what's actually built, what's in progress, what's deprecated
3. `.ai/02-agent-operating-rules.md` — how to approach a task, preferred implementation patterns
4. `.ai/03-stop-conditions.md` — situations where you must stop and ask instead of guessing
5. `.ai/04-do-not-touch.md` — files/systems that are off-limits by default
6. `docs/decisions/` — past architectural decisions and why they were made; check before re-deciding something that's already settled

## The short version, if you only read one paragraph

Make the smallest safe change that accomplishes the task. Don't invent conventions the codebase doesn't already use. Don't touch anything in `.ai/04-do-not-touch.md`. If a task requires something listed in `.ai/03-stop-conditions.md`, stop and ask before proceeding. When you finish, report using the format in `.ai/05-output-standard.md`.

## For tool-specific files

If your tool reads `CLAUDE.md`, `.cursor/rules/`, or another tool-specific format instead of `AGENTS.md` directly, that file should be a short pointer back to this one — not a duplicate. Keep one source of truth.
