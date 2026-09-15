# Agent Doctrine Template

A free, opinionated set of doctrine files that keep AI coding agents (Claude Code, Cursor, Codex, Copilot, Windsurf, etc.) from drifting, overstepping scope, and quietly burning your token budget on context they didn't need.

This isn't auto-generated from scanning your repo. It's distilled from three real, solo-built, shipped production codebases — refined project over project, not written in one sitting.

## Why this exists

If you've built anything real with an AI coding agent, you already know the failure mode: it works great for a few days, then it starts making up its own conventions, touching files it shouldn't, re-explaining decisions you already made, and quietly bloating every prompt with context it doesn't need. The fix isn't a smarter model. It's giving the agent a persistent, explicit doctrine to read before it plans anything — the same way you'd onboard a new engineer with a README instead of just pointing at the codebase and hoping.

That idea has a name now — **spec-driven development** — and by 2026 most major AI coding tools ship some version of it (GitHub Spec Kit, Amazon Kiro, Claude Code's own agent-doc conventions, and more). This template isn't trying to replace any of that. It's a smaller, opinionated starting point, free, that you can drop into a project in five minutes — built from what actually held up across real shipped work, not a framework designed top-down.

## How this is different from the auto-generators

There are already good free tools (`agentscribe`, `agentinit`, and others) that scan your codebase and auto-generate `AGENTS.md`/`CLAUDE.md`/`.cursorrules` from your stack. Those are genuinely useful for the *mechanical* part — detecting your linter, your package manager, your test runner.

This template is not that, and doesn't try to be. It focuses on the part auto-detection can't give you:

- **Explicit stop conditions** — the specific situations where an agent should stop and ask instead of guessing (new payment logic, schema changes, permission model changes, etc.)
- **Small-diff discipline** — a concrete "bad task shape vs. good task shape" pattern that keeps agents from bundling five unrelated changes into one unreviewable diff
- **Decision records with revisit triggers** — not just *what* was decided, but *why*, what alternatives were rejected and why, and the specific condition under which the decision should be reopened — so agents (and you) stop relitigating settled architecture
- **A do-not-touch boundary list** — the files/systems that are off-limits by default
- **An output standard** — what an agent reports when a task is done, so you're not left guessing what changed

Use this *alongside* a stack-detector if you want both — they solve different problems.

## Compatibility

This template follows the emerging [`AGENTS.md`](https://agents.md) convention so Claude Code, Cursor, Codex, and other tools that read `AGENTS.md` will pick it up automatically. Tool-specific files (`CLAUDE.md`, `.cursor/rules/`) can point back to it — see `AGENTS.md` for the router pattern.

## What's in here

```
AGENTS.md                        # Root router — lightweight, points agents at .ai/
.ai/
  00-project-identity.md         # What this project is, who it's for, what it is NOT
  01-current-state.md            # What's actually built vs. planned vs. deprecated
  02-agent-operating-rules.md    # How to start a task, preferred patterns, small-diff rule
  03-stop-conditions.md          # When to stop and ask instead of guessing
  04-do-not-touch.md             # Explicit off-limits files/systems
  05-output-standard.md          # What to report when a task is finished
docs/
  decisions/
    ADR_TEMPLATE.md              # Architecture Decision Record template with revisit triggers
    ADR-000-example.md           # Filled-out example
  CHANGELOG.md                   # Living log — decisions superseded, what replaced them
LICENSE                          # MIT
```

## Quick start

1. Copy `.ai/`, `AGENTS.md`, and `docs/` into your project root.
2. Fill in `.ai/00-project-identity.md` and `.ai/01-current-state.md` for your actual project — this is the only step that takes real effort, and it's worth it.
3. Trim `.ai/02-agent-operating-rules.md` and `.ai/03-stop-conditions.md` to your actual stack and constraints. Delete what doesn't apply.
4. When you make a real architectural decision, copy `docs/decisions/ADR_TEMPLATE.md` to a new numbered ADR instead of just deciding it in chat and forgetting why.
5. Point your tool of choice at it — most modern agents read `AGENTS.md` automatically, or symlink/copy to `CLAUDE.md` / `.cursor/rules/` as needed.

## Why "free"

This isn't a lead magnet for a paid tier. It's genuinely free, MIT-licensed, no signup, no catch. If it saves you tokens and headaches, great — that's the whole point. If you want to fork it, change the doctrine style entirely, or strip half of it out, do that. It's a starting point, not a framework you're locked into.

## Contributing

PRs welcome, especially if you've found doctrine patterns that hold up across real shipped projects — that's the bar, not theory. No formal process; open an issue or a PR.

---

Built by someone who kept reinventing the same doctrine file by hand across three separate solo-built production apps before finally writing down the version that actually stuck.
-Jeff