# 02 — Agent Operating Rules

These rules exist to reduce agent mess, duplicate code, and accidental breakage. They apply to every task unless a more specific doctrine file overrides them.

## Start every task this way

Before changing code:

1. Find the relevant files (routes, components, modules — whatever the project's actual structure is).
2. Find existing utilities, hooks, or patterns that already do something similar. Reuse before you invent.
3. Identify whether the thing you're touching is live/production, mock/placeholder, or mixed.
4. Plan the smallest safe edit that accomplishes the task.
5. If the task is genuinely large, break it into an explicit plan before touching code — don't improvise a large change in one pass.

## Preferred implementation pattern

<!-- Fill in your project's actual structure. Example shape below — replace with your own. -->

- Route/page files: composition and layout only, not business logic.
- Data access layer: one place for queries/mutations, not scattered inline fetches.
- Shared components: reusable UI, not one-off duplicates of existing components.
- Utilities: shared formatting/normalization logic lives in one place, not copy-pasted per file.

Do not put large one-off logic directly into a component or route when a shared pattern already exists for it.

## Small diff rule

Do not bundle unrelated work into one change.

**Bad task shape:** "Wire up auth, the dashboard, the billing page, and fix the header."

**Good task shape:** "Replace the mock billing data on `/billing` with the real `subscriptions` query."

If a request is actually five tasks, say so and propose splitting it — don't silently do all five in one diff.

## Don't invent conventions

If the codebase already has a pattern for something (naming, error handling, state management), follow it — even if you'd personally prefer a different pattern. Consistency with the existing codebase beats a "better" one-off approach. If you think the existing pattern is genuinely wrong, say so explicitly and propose a change — don't just quietly do it differently in one place.

## Preserve working systems

If ten things work and one thing is broken, fix the one thing. Don't rewrite the other nine because you're already in the file. Prefer additive, isolated, reversible changes over broad rewrites unless there's clear evidence the broader system is the actual problem.
