# Level 5 — Orchestration

> *One assistant, one task, one chat is the slow path. Run a team.*

**Your climb:** [0](0-vending-machine.md) · [1](1-conversation.md) · [2](2-context-engineering.md) · [3](3-workflow-discipline.md) · [4](4-quality-gates.md) · **5** · [6](6-authorship.md)

| At a glance | |
|---|---|
| **The trap** | One task, one chat — independent work runs in sequence; chores get done by hand. |
| **The unlock** | Conduct, don't labor: parallelize, delegate to subagents, automate with hooks and schedules. |
| **Make it automatic** | Subagents · hooks · `/loop` · scheduled routines · MCP |

---

## Where most people are

You're genuinely good now: great context, real workflow, quality gates. But you operate the AI like a single craftsperson working one bench. You ask, it works, you wait, you read, you ask again. Independent tasks queue up behind each other. Repetitive chores get done by hand every time. You've hit the ceiling of *one worker doing one thing*.

## The unlock

Stop being a worker and start being a conductor. Four moves:

**1. Parallelize independent work.** If two tasks don't depend on each other, they shouldn't run in sequence. Fire off independent searches, edits, or investigations at the same time. Wall-clock time drops to the length of the *slowest* task, not the *sum* of all of them.

**2. Delegate to subagents.** Spin up focused agents for self-contained jobs — "research how auth works across these 30 files," "audit this migration for safety" — and let them churn while you stay on the main thread. They protect your main context from noise and do real work in parallel.

**3. Automate the repeated steps with hooks.** A hook is a command the *harness* runs automatically on an event — format on every save, run tests after every edit, block a commit that fails lint. This is automation the model can't forget to do, because the model isn't the one doing it.

**4. Put work on a schedule or a loop.** Recurring tasks — a nightly PR triage, a "poll the deploy until it's green," a weekly dependency check — don't need you to babysit them. Schedule them or loop them and get notified.

## The principle

> Your leverage stops scaling with how well you direct *one* worker and starts scaling with how well you *compose many*.

The mental shift is from *doing* to *orchestrating*: your job becomes decomposition (what can run independently?), delegation (who does each piece?), and integration (assembling the results) — not execution.

## Before / After

**Before:**
```
You: check how the API client handles retries
*wait*
You: now check how it handles auth refresh
*wait*
You: now check the error-mapping layer
*wait — three sequential investigations, context cluttered with all three*
```

**After:**
```
You: *launches 3 Explore subagents in parallel* — one per subsystem.
    Each reports back a tight summary. Main context stays clean.
    Meanwhile a hook reruns the test suite on every edit, and a scheduled
    job triages new PRs each morning before you log on.
```

## What it looks like in Claude Code

- **Parallel tool calls** — multiple independent operations in a single step.
- **Subagents** (the `Agent` tool / `Explore`, `Plan`, `general-purpose` types) — delegate self-contained tasks; run them in the background.
- **Hooks** — shell commands the harness runs on events (`PostToolUse`, `PreToolUse`, `Stop`, …). Configure via the **`update-config`** skill or `settings.json`.
- **`/loop`** — run a prompt or command on a recurring interval.
- **Scheduled agents / routines** (the **`schedule`** skill) — cron-style remote runs.
- **MCP servers** — connect the assistant to external systems (Gmail, Calendar, Drive, your own services) so delegated work can reach beyond the repo.

## The tell you're ready to level up

You're orchestrating well — but you keep re-typing the same instructions to set up each agent, each gate, each routine. Your standards live in your head and your habits, re-issued by hand. The final unlock is to stop *operating* the system every time and start *building* it.

## The unlock → [Level 6: Authorship](6-authorship.md)

Encode your leverage into tools you (and others) can reuse: skills, MCP servers, custom agents.

---

⬅️ [Level 4](4-quality-gates.md) · ⬆️ [The map](../README.md) · ➡️ [Level 6 — Authorship](6-authorship.md)
