# Level 3 — Workflow Discipline

> *Process beats vibes. Plan before code, verify after, commit clean.*

This is the first level where most people feel a *qualitative* jump — where AI stops being a faster way to write code and starts being a more reliable way to ship it.

## Where most people are

The context is dialed in (Level 2), so the AI produces code that fits your project. But you still operate on vibes: you ask for a feature, it starts writing immediately, you skim the result, and you find out two hours later that it solved the wrong problem or quietly broke something else.

The failure isn't quality of code. It's *absence of process*. There was no agreed plan to check against and no verification step to catch the miss.

## The unlock

Wrap generation in a loop that a good engineer runs by instinct:

**1. Plan first.** For anything non-trivial, get a short written plan *before* a line of code — requirements restated, scope, approach, and a concrete definition of "done." You catch misunderstandings when they cost a sentence, not a rewrite. If the plan is wrong, the code was always going to be wrong.

**2. Verify after.** "It ran" is not "it works." After implementation, actively check the result against the acceptance criteria — run it, hit the edge cases, look for regressions. Tests verify code correctness; *you* (or a verification step) confirm feature correctness.

**3. Commit clean.** Atomic commits with messages that explain *why*. This isn't bookkeeping — clean history is what makes the next change safe, because you can reason about and revert one thing at a time.

**4. Survive interruptions.** Real work spans sessions. Capture state so you can resume exactly where you left off instead of reconstructing context from memory.

## Before / After

**Before:**
```
You: build a user dashboard
AI: *immediately writes 400 lines*
You: *2 hours later* ...this fetches the wrong endpoint and there's no
     loading state and it doesn't match our other pages
```

**After:**
```
You: build a user dashboard
AI: Before I write code — here's the plan:
    • Data: GET /api/me/stats (matches existing dashboard pattern)
    • Components: auth guard, data fetch w/ loading + error states, layout
    • Done when: renders for a logged-in user, handles loading/error/empty,
      matches the styling of /settings
    Approve or adjust?
You: approve, but add an empty state for new users
AI: *builds to the agreed spec, then verifies each criterion*
```

## What it looks like in Claude Code

This is exactly what **[claude-skillcraft](https://github.com/ProjectWaja/claude-skillcraft) Tier 1** encodes, so the discipline is automatic instead of remembered:

- **[`plan-first`](https://github.com/ProjectWaja/claude-skillcraft/tree/main/skills/plan-first)** — requires a written plan before any implementation. Kills the "just start coding" reflex.
- **[`ship-cycle`](https://github.com/ProjectWaja/claude-skillcraft/tree/main/skills/ship-cycle)** — the full branch → implement → test → review → merge loop, no skipped steps.
- **[`verify-build`](https://github.com/ProjectWaja/claude-skillcraft/tree/main/skills/verify-build)** — a post-implementation verification checklist that catches what tests miss.
- **[`clean-commit`](https://github.com/ProjectWaja/claude-skillcraft/tree/main/skills/clean-commit)** — atomic commits, conventional messages, PR discipline.
- **[`task-resume`](https://github.com/ProjectWaja/claude-skillcraft/tree/main/skills/task-resume)** — session continuity; pick up exactly where you left off.

Native Claude Code features in the same spirit: **plan mode** (design before editing) and **`/init`** for the context that makes plans accurate.

## The tell you're ready to level up

You have a process — but *you* are still the only thing enforcing it. You're the plan reviewer, the code reviewer, the "wait, that's over-engineered" reviewer, and the "you've tried the same fix three times, stop" reviewer. That's a lot of you.

## The unlock → [Level 4: Quality Gates](4-quality-gates.md)

Push the checking into the system. Make the AI catch its own mistakes — and know when to stop.

---

⬅️ [Level 2](2-context-engineering.md) · ⬆️ [The map](../README.md) · ➡️ [Level 4 — Quality Gates](4-quality-gates.md)
