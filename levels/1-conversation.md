# Level 1 — The Conversation

> *The first answer is a draft, not a delivery.*

## Where most people are

You've realized you can reply. When the code is wrong, you paste the error back and ask it to fix it. This alone puts you ahead of most people — but at Level 1 the conversation is still *reactive*. You're patching one symptom at a time, and you give up if two or three rounds don't converge.

## The unlock

Treat the exchange as a steering problem, not a slot machine you keep pulling. Three habits separate a good conversation from a frustrating one:

**1. Feed back the *real* signal.** Don't say "that didn't work." Paste the exact error, the unexpected output, the failing input. The model debugs what you show it, not what you summarize.

**2. Give context up front, not under interrogation.** Before the first answer, say what you're building, the constraints, the stack, and what "done" means. Two extra sentences of context beats five rounds of correction.

**3. Steer, don't just reject.** "No" wastes a turn. "No — it should stream the response instead of buffering, and keep it under 50 lines" spends the same turn moving forward.

## Before / After

**Before (Level 0 carried over):**
```
You: write a rate limiter
AI: [generic in-memory token bucket]
You: doesn't work
AI: [slightly different generic token bucket]
You: still doesn't work
You: *gives up, writes it by hand*
```

**After (Level 1):**
```
You: Write a rate limiter for an Express API. Redis-backed (we run multiple
     instances), 100 req/min per API key, return 429 with a Retry-After header.
     Keep it to one middleware function.
AI: [targeted implementation matching all four constraints]
You: Good — but Retry-After should be seconds remaining in the window, not 60.
AI: [fixes exactly that]
```

Same model. Same number of messages. The difference is the question carried the context, and each reply carried real signal.

## The tell you're ready to level up

You notice you're explaining the *same* things — your stack, your conventions, your folder layout — at the start of every new chat. That repetition is the friction Level 2 removes.

## The unlock → [Level 2: Context Engineering](2-context-engineering.md)

Stop re-explaining your project from scratch. Make the context *persistent* so every conversation starts where the last one left off.

---

⬅️ [Level 0](0-vending-machine.md) · ⬆️ [The map](../README.md) · ➡️ [Level 2 — Context Engineering](2-context-engineering.md)
