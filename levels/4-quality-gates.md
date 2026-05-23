# Level 4 — Quality Gates

> *You shouldn't be the only thing standing between bad output and your codebase.*

**Your climb:** [0](0-vending-machine.md) · [1](1-conversation.md) · [2](2-context-engineering.md) · [3](3-workflow-discipline.md) · **4** · [5](5-orchestration.md) · [6](6-authorship.md)

| At a glance | |
|---|---|
| **The trap** | *You* are the single point of failure — the only thing checking the output. |
| **The unlock** | Encode judgment as gates: self-review, simplify, and a circuit-breaker on debug loops. |
| **Make it automatic** | skillcraft Tier 2 — `output-guard`, `simplify-code`, `debug-circuit`, `craft-principles` · plus hooks |

---

## Where most people are

You've got a workflow (Level 3), but you're the single point of failure in it. Every plan, every diff, every "hmm that looks over-complicated," every "you've now tried four variations of the same broken fix" — that's all you, manually, every time. It works until you're tired, rushed, or reviewing the fortieth diff of the day. Then things slip through.

## The unlock

Encode your judgment as *gates* the work has to pass through, so quality doesn't depend on your attention being at full strength. Four gates matter most:

**1. Output validation.** Before generated code is accepted, it gets checked against correctness, security, and style rules — automatically. The first reviewer of the AI's output should be the AI, against an explicit standard.

**2. Simplicity enforcement.** Models, like people, over-engineer when nervous: premature abstractions, speculative config, dead code "just in case." A simplicity gate flags it. Three plain lines beat a clever framework.

**3. A debug circuit breaker.** The most expensive failure mode is the death-loop: try a fix, fail, try a near-identical fix, fail, repeat. A circuit breaker forces a step back after a few failed attempts — re-examine assumptions instead of brute-forcing. This single gate saves more time than any other.

**4. First-principles enforcement.** Readability, testability, minimal dependencies — stated explicitly and checked, not left to chance.

## The principle

> Quality that depends on you being sharp isn't quality — it's luck with a good track record.

The move from Level 3 to Level 4 is the move from *I check the work* to *the work is checked.* You're still the final authority; you're just no longer the only line of defense.

## Before / After

**Before:**
```
AI: *produces a working feature with a needless 3-layer abstraction,
    an unused config flag, and a swallowed error*
You: *merges it because it works and you're on diff #40 today*
*the swallowed error becomes a 2am incident next month*
```

**After (gates active):**
```
AI: *produces the feature, then self-reviews:*
    ⚠ simplify-code: the StrategyFactory wraps a single implementation —
      inlining it. ⚠ output-guard: error on line 42 is swallowed; surfacing it.
    *delivers the simpler, safer version*
```

## What it looks like in Claude Code

**[claude-skillcraft](https://github.com/ProjectWaja/claude-skillcraft) Tier 2** is exactly this set of gates:

- **[`output-guard`](https://github.com/ProjectWaja/claude-skillcraft/tree/main/skills/output-guard)** — validates generated code against correctness, security, and style rules before it's accepted.
- **[`simplify-code`](https://github.com/ProjectWaja/claude-skillcraft/tree/main/skills/simplify-code)** — flags over-engineering, premature abstractions, and dead code.
- **[`debug-circuit`](https://github.com/ProjectWaja/claude-skillcraft/tree/main/skills/debug-circuit)** — the circuit breaker; forces a reset after repeated failed attempts.
- **[`craft-principles`](https://github.com/ProjectWaja/claude-skillcraft/tree/main/skills/craft-principles)** — enforces readability, simplicity, testability, minimal dependencies.

Native features in the same spirit: **hooks** (run a linter/test/format command automatically on every edit — a gate the harness enforces, not the model) and the **`/code-review`** and **`/security-review`** commands.

## The tell you're ready to level up

The work is reliable now — and you start noticing you're the *bottleneck*, not the failure point. The AI is idle while you read its last answer; tasks that don't depend on each other still run one at a time; the same five-step chore happens by hand again. You've maxed out a single worker. Time to run a team.

## The unlock → [Level 5: Orchestration](5-orchestration.md)

Delegate and parallelize. Stop running one task in one chat.

---

⬅️ [Level 3](3-workflow-discipline.md) · ⬆️ [The map](../README.md) · ➡️ [Level 5 — Orchestration](5-orchestration.md)
