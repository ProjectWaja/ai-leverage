# Level 2 — Context Engineering

> *Stop re-explaining your project. Make the context live in the project.*

## Where most people are

Every new conversation, you re-type the same preamble: "I'm using React with TypeScript, we use tabs not spaces, the API client is in `src/lib/api.ts`, don't use default exports..." Then you paste in two or three files so the model has something to work with. By the time you ask your actual question, you've burned ten minutes and half your patience.

You're doing the right thing — giving context — but you're doing it *by hand, every time*. That doesn't scale, and you'll inevitably forget to mention the one constraint that matters.

## The unlock

Move context out of your head and into the project, where the AI reads it automatically. Three mechanisms, roughly in order of impact:

**1. A `CLAUDE.md` at the repo root.** This is the single biggest Level-2 unlock. It's a file the assistant reads on every session — your conventions, architecture, commands, gotchas, and "never do X here." Write it once; every future conversation starts pre-briefed. Run `/init` in Claude Code to generate a first draft from your codebase, then prune it to what actually matters.

**2. Point at files, don't paste them.** Reference real paths and let the assistant read them. Pasted snippets go stale and lose surrounding context; a live file reference is always current and lets the model pull in neighbors when it needs to.

**3. Let it remember across sessions.** Durable facts — who you are, how you like to work, what this project is for — belong in persistent memory, not in a preamble you retype. The point is the same: say it once.

## The principle

> Context is not something you *provide*. It's something you *engineer* — once, deliberately, so it's there by default.

A good `CLAUDE.md` is the highest-leverage file in your repo. It silently improves every single interaction, forever, for everyone on the team.

## Before / After

**Before:**
```
You: [pastes 3 files, 200 lines]
     I'm using Next.js app router, TS strict mode, Tailwind, and we put
     server actions in app/actions. Don't use any. Now, add a contact form...
```
*(...repeated, verbatim, at the start of every session)*

**After — `CLAUDE.md` exists:**
```
You: Add a contact form with server-side validation.
AI: [already knows the router, the strict-mode rules, where actions live,
     and reads the actual files it needs — produces code that fits on the
     first try]
```

## What it looks like in Claude Code

- **`/init`** — scaffolds a `CLAUDE.md` by analyzing your codebase.
- **`CLAUDE.md`** (repo root, or nested per-directory) — auto-loaded project context.
- **`@path/to/file`** references and the assistant's own file reading — live context over stale paste.
- **Memory** — persistent facts about you and the project across sessions.

## The tell you're ready to level up

The AI now *understands* your project — but it still dives straight into code on big asks, and you still discover problems only after it's "done." Context fixed *what* it knows. Next you fix *how it works*.

## The unlock → [Level 3: Workflow Discipline](3-workflow-discipline.md)

Plan before code. Verify after. Turn ad-hoc generation into a repeatable loop.

---

⬅️ [Level 1](1-conversation.md) · ⬆️ [The map](../README.md) · ➡️ [Level 3 — Workflow Discipline](3-workflow-discipline.md)
