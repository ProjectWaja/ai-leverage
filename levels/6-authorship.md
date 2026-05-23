# Level 6 — Authorship

> *Stop consuming AI as it ships. Build the leverage you wish it had.*

**Your climb:** [0](0-vending-machine.md) · [1](1-conversation.md) · [2](2-context-engineering.md) · [3](3-workflow-discipline.md) · [4](4-quality-gates.md) · [5](5-orchestration.md) · **6**

| At a glance | |
|---|---|
| **The trap** | Your expertise gets *re-performed* every session; teammates inherit none of it. |
| **The unlock** | Encode judgment into reusable artifacts: skills, MCP servers, custom agents. |
| **Make it automatic** | Author skills (SKILL.md) · build MCP · custom agents — *this is what [claude-skillcraft](https://github.com/ProjectWaja/claude-skillcraft) is* |

---

This is the top of the climb, and it's a different kind of activity from everything below. Levels 0–5 are about getting better at *using* the system. Level 6 is about *extending* it — encoding your standards, your domain, and your workflow into tools that apply themselves, every time, for everyone.

## Where most people are

You're an excellent operator. You orchestrate subagents, you've got hooks and schedules running, your context is immaculate. But everything that makes you good lives in your head and your habits. You re-establish your standards each session by being disciplined. When a teammate uses the same AI, they get none of it. Your expertise doesn't *compound* — it gets *re-performed*.

## The unlock

Turn your repeated judgment into reusable artifacts. The moment you write something down as a tool, it stops costing you attention and starts working for everyone who installs it.

**1. Author skills.** A skill is a written instruction set the assistant loads when it's relevant — "always plan before coding," "validate output against these rules," "estimate construction bids this way." The discipline you used to *remember* becomes discipline the assistant *applies automatically*. This is the single most leveraged thing you can build, because it's just well-structured markdown — see the [SKILL.md open standard](https://agentskills.io).

**2. Build MCP servers.** When the assistant needs to reach a system that doesn't exist yet — your internal API, a proprietary database, a domain tool — you build the bridge. Now delegated work can touch the things only your organization has.

**3. Compose custom agents.** Package a role — a security reviewer, a domain expert, a release manager — with its own tools and instructions, and invoke it on demand.

**4. Encode a domain, not just a workflow.** The highest form of this is taking expertise the model *doesn't* have — how your trade estimates jobs, how your team runs sprints, how your industry handles compliance — and making it executable. That's leverage no off-the-shelf model can match, because it's *your* knowledge, made repeatable.

## The principle

> A user gets better results. An author changes what "results" are possible — for themselves and everyone downstream.

This is also where you elevate your use of the assistant *itself*: you stop asking "how do I get Claude to do X?" and start asking "what should I build so that doing X is automatic from now on?"

## What it looks like in Claude Code

- **Authoring skills** — the [SKILL.md format](https://agentskills.io); drop them in `~/.claude/skills/` or share a pack.
- **[claude-skillcraft](https://github.com/ProjectWaja/claude-skillcraft)** is itself a Level-6 artifact: 12 skills that encode the disciplines from Levels 3–4 so nobody has to remember them. Its **PM Bridge** tier shows authorship applied *beyond code* — product thinking made executable:
  - **[`pm-docs`](https://github.com/ProjectWaja/claude-skillcraft/tree/main/skills/pm-docs)** — generate PRDs, one-pagers, decision logs, launch checklists from conversation context.
  - **[`sprint-flow`](https://github.com/ProjectWaja/claude-skillcraft/tree/main/skills/sprint-flow)** — story breakdown, acceptance criteria, sprint planning, retros.
  - **[`meeting-driver`](https://github.com/ProjectWaja/claude-skillcraft/tree/main/skills/meeting-driver)** — agendas, time-boxes, action items, follow-up tracking.
- **MCP servers** — the open protocol for connecting assistants to external tools and data.
- **Custom subagents** — defined roles with scoped tools and instructions.

## You don't "finish" Level 6

Authorship isn't a final boss you beat. It's a flywheel: you build a skill, it reveals the next disciplines worth encoding, you build those, your tools get sharper, and the floor under everyone who uses them rises. The best practitioners spend most of their time here — not because the lower levels stopped mattering, but because they've made the lower levels automatic and now invest in the leverage that compounds.

Build something. Share it. That's the whole game.

---

⬅️ [Level 5](5-orchestration.md) · ⬆️ [The map](../README.md) · 🏁 [Capstone: the same task at every level](../examples/same-task-every-level.md)
