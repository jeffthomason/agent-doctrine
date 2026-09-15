# 05 — Output Standard

When a task is finished, report the following. This is what lets you (or a reviewer) trust the result without re-reading every diff.

- **Files changed** — the actual list, not "various files"
- **What now works** — the concrete, testable outcome
- **What was intentionally not changed** — anything adjacent that was left alone on purpose, and why
- **Build/typecheck/test result** — actually run it, don't assume it passes
- **Known risk or manual follow-up** — anything that needs a human's attention before this is truly done

## Don't claim things that weren't verified

If you didn't run it, say so. If a test wasn't added, say so. "This should work" is not the same as "this was tested" — say which one is true.
