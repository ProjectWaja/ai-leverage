# ai-leverage

**Most people use AI at a fraction of its leverage. This is the map for the rest of the climb.**

A practical, opinionated guide to *how to actually get good* at working with an AI coding assistant — built around Claude Code, but the principles transfer to any capable model. Each level shows where most people get stuck, the one unlock that moves you up, and exactly what it looks like in practice.

---

## The premise

The gap between a beginner and an expert using the same AI model is enormous — far bigger than the gap between two models. Same Claude, same prompt budget, wildly different results. The difference isn't the tool. It's the *operating skill*.

Most people plateau at Level 0 or 1: they treat a world-class collaborator like a vending machine, get mediocre output, and conclude "AI isn't that good yet." They're not wrong about their results. They're wrong about the cause.

This repo maps the climb from *fancy autocomplete* to *AI as a system you operate*. Seven levels. Each one is a real unlock you can practice today.

---

## The map

| Level | Name | Where most people are | The unlock |
|------:|------|-----------------------|------------|
| **0** | [The Vending Machine](levels/0-vending-machine.md) | One-shot prompt, copy the answer, blame the AI when it's wrong | *(this is the floor — the rest is up)* |
| **1** | [The Conversation](levels/1-conversation.md) | Give up after one bad answer | Iterate. Treat it as dialogue, feed back errors, steer |
| **2** | [Context Engineering](levels/2-context-engineering.md) | Re-explain the project every single time | Persistent context: `CLAUDE.md`, real files, memory |
| **3** | [Workflow Discipline](levels/3-workflow-discipline.md) | "Just start coding," debug for hours | Plan before code, verify after, commit clean |
| **4** | [Quality Gates](levels/4-quality-gates.md) | *You* are the only thing checking the output | The AI checks its own work and knows when to stop |
| **5** | [Orchestration](levels/5-orchestration.md) | One task, one chat, watch it work | Delegate and parallelize: subagents, hooks, schedules |
| **6** | [Authorship](levels/6-authorship.md) | Consume AI as-is | Build your own leverage: skills, MCP, custom agents |

Each level builds on the one below it. You don't skip — but you climb faster than you think once you see the pattern.

---

## How to read this

- **Start at your real level, not your aspirational one.** Use the self-check below.
- **Each chapter is self-contained**: the bad habit, the unlock, a concrete before/after, and the specific Claude Code feature or skill that gets you there.
- **The capstone** — [the same task at every level](examples/same-task-every-level.md) — takes one ordinary request ("add login to my app") and shows how it plays out from Level 0 to Level 6. Read it last; it ties everything together.

---

## Which level are you? (60-second self-check)

Answer honestly. Your level is the **highest** number where you can say "yes, I do that consistently."

- **0** → I paste a prompt, take what comes out, and move on.
- **1** → When the answer is wrong, I tell it what's wrong and we go again.
- **2** → My project has a `CLAUDE.md` (or equivalent) so I don't re-explain conventions, and I point the AI at real files instead of pasting snippets.
- **3** → For non-trivial work I get a plan first, and I verify the result before calling it done.
- **4** → My setup catches its own mistakes — bad output gets flagged before I see it, and runaway debug loops get interrupted.
- **5** → I routinely run work in parallel, delegate sub-tasks to subagents, and automate repeated steps with hooks or schedules.
- **6** → I've built my own skills / tools / MCP servers that encode my standards, and I share them.

Most working developers are at **1**. Most people who think they're "good with AI" are at **2–3**. Levels **4–6** are where the compounding returns live.

---

## Where the skills come in

Levels 3 and up are easier to *hold* when the discipline is encoded, not remembered. That's what [**claude-skillcraft**](https://github.com/ProjectWaja/claude-skillcraft) is — a companion pack of 12 Claude Code skills, organized into the same tiers this guide describes:

- **Level 3 (Workflow)** → `plan-first`, `ship-cycle`, `verify-build`, `clean-commit`, `task-resume`
- **Level 4 (Quality)** → `output-guard`, `simplify-code`, `debug-circuit`, `craft-principles`
- **Level 6 (Authorship, applied beyond code)** → `pm-docs`, `sprint-flow`, `meeting-driver`

This guide explains *why* each unlock matters. Skillcraft is *how* you make it automatic. You can read this with no skills installed — the unlocks are habits first, tools second.

---

## A note on models

Everything here is written against [Claude Code](https://claude.com/claude-code) because that's what we use, and because it has first-class support for the higher-level unlocks (skills, subagents, hooks, MCP). But Levels 0–4 are model-agnostic habits. If you're on a different assistant, read past the product names — the climb is the same.

---

## Contributing

This is a living map. If a level is missing a sharper example, or you've found an unlock we haven't named, see [CONTRIBUTING.md](CONTRIBUTING.md). Real before/after transcripts are the most valuable thing you can add.

## License

MIT. See [LICENSE](LICENSE).

---

*Built by [ProjectWaja](https://github.com/ProjectWaja). Companion to [claude-skillcraft](https://github.com/ProjectWaja/claude-skillcraft).*
