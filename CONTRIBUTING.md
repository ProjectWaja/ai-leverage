# Contributing to ai-leverage

This is a living map of how to get good at working with AI. The best contributions make a level *sharper*, not longer.

## What we're looking for

- **Real before/after transcripts.** The single most valuable thing you can add. A concrete "here's the dumb way, here's the leveled-up way" beats any amount of theory.
- **A missing unlock.** Found a habit that reliably moves people up a level and isn't named here? Propose it.
- **Sharper examples.** If a chapter's example is vague or dated, replace it with a crisper one.
- **Corrections.** Product features change. If a Claude Code feature reference is wrong or outdated, fix it.
- **Translations / other assistants.** Levels 0–4 are model-agnostic. A "here's how this maps to tool X" appendix is welcome.

## What we're *not* looking for

- Hype. No "AI will replace everyone" takes. This guide is about practical leverage.
- Tool spam. Links to a feature must explain *which unlock it serves*, not just exist.
- Level inflation. Don't add levels for the sake of it. Seven is deliberate; a new one has to earn its place.

## Style guide

- **Concrete over abstract.** "Functions under 50 lines" beats "write clean code."
- **Show the before.** Every unlock is more convincing next to the habit it replaces.
- **Second person, direct.** "You paste the error back" — talk to the reader.
- **Keep chapters tight.** Each level should read in a couple of minutes. If it's sprawling, cut.
- **One idea per level.** If a chapter has two unlocks, it's probably two levels (or one is in the wrong place).

## How to submit

1. Fork the repo.
2. Branch: `docs/level-N-better-example` or `feat/new-unlock`.
3. Edit the relevant file in `levels/` or `examples/`, and update the map table in `README.md` if structure changes.
4. Open a PR explaining what got sharper and why.

## Relationship to claude-skillcraft

This repo is the *map*; [claude-skillcraft](https://github.com/ProjectWaja/claude-skillcraft) is the *gear*. If your contribution is a new **skill** (an executable discipline), it belongs in skillcraft. If it's an explanation of *why* an unlock matters, it belongs here. When in doubt, open an issue and we'll point you to the right repo.

## Code of conduct

Be constructive, be specific, be kind. That's it.
