# Capstone: the same task at every level

One ordinary request — **"add login to my app"** — played out at each of the seven levels. Same person, same app, same model. Watch what changes as the *operating skill* climbs.

> Read the [level chapters](../README.md#the-map) first if you haven't. This is the payoff that ties them together.

---

## The task

> *"Add email/password login to my web app."*

A real feature: a form, a backend check, a session, protected routes. Below, the **same** request, leveled up.

---

## Level 0 — The Vending Machine

```
You: add email password login
AI:  [generic 80-line auth snippet with an in-memory user array
      and a hardcoded JWT secret]
You: *pastes it in*
```

**What happens:** It "works" in the demo. The user array resets on restart, the secret is `"secret"`, passwords are stored in plaintext, and none of it matches your stack. You ship it or you fight it. Either way you blame the tool.

**Cost:** A security incident waiting to happen, or hours of rework.

---

## Level 1 — The Conversation

```
You: Add email/password login to my Express + Postgres app. Hash passwords
     with bcrypt, issue an httpOnly session cookie, and return 401 on bad
     credentials. Keep the secret in an env var.
AI:  [implementation matching the stack and the four constraints]
You: Good — the cookie needs SameSite=Lax and Secure in production.
AI:  [fixes exactly that]
```

**What changed:** The request carried context and constraints; corrections carried real signal. The result actually fits — but you re-typed your whole stack to get here, and you'll do it again next feature.

---

## Level 2 — Context Engineering

Your repo now has a `CLAUDE.md`: *"Express + Postgres (via Prisma). Auth uses httpOnly cookies. Secrets in env. Never log credentials. Route handlers in `src/routes`, business logic in `src/services`."*

```
You: Add email/password login.
AI:  [reads CLAUDE.md and the existing files; produces a handler in
      src/routes, logic in src/services, Prisma for the user lookup,
      bcrypt + httpOnly cookie — matching conventions you never restated]
```

**What changed:** Zero preamble. The AI started pre-briefed and the code slotted into your architecture on the first try.

---

## Level 3 — Workflow Discipline

```
You: Add email/password login.
AI:  Plan first:
     • Scope: POST /auth/login, session middleware, login form, protected-route guard
     • Approach: bcrypt verify → signed httpOnly cookie → middleware reads it
     • Out of scope: signup, password reset (separate tasks)
     • Done when: valid creds set a session and reach /dashboard; bad creds 401;
       protected routes redirect when logged out; logout clears the cookie
     Approve?
You: Approve — also rate-limit the endpoint.
AI:  [builds to spec, then verifies each "done-when" criterion, and commits:
      "feat(auth): add email/password login with rate-limited endpoint"]
```

**What changed:** You agreed on *done* before any code existed, caught the rate-limit gap in the plan (not in prod), and got clean history. → encoded by [`plan-first`](https://github.com/ProjectWaja/claude-skillcraft/tree/main/skills/plan-first), [`verify-build`](https://github.com/ProjectWaja/claude-skillcraft/tree/main/skills/verify-build), [`clean-commit`](https://github.com/ProjectWaja/claude-skillcraft/tree/main/skills/clean-commit).

---

## Level 4 — Quality Gates

```
AI:  [builds login per the plan, then self-reviews before handing it back:]
     ⚠ output-guard: error path leaks whether the email exists (user
       enumeration) — returning a uniform 401 for both cases.
     ⚠ output-guard: login attempt logged with the password in the payload —
       redacting before log.
     ⚠ simplify-code: AuthStrategyFactory wraps one strategy — inlined.
     [delivers the corrected, simpler version]
```

**What changed:** Three real problems — a security leak, a credential-logging bug, and needless abstraction — caught by the system *before you ever saw the diff*, not by you on review. → [`output-guard`](https://github.com/ProjectWaja/claude-skillcraft/tree/main/skills/output-guard), [`simplify-code`](https://github.com/ProjectWaja/claude-skillcraft/tree/main/skills/simplify-code). A test-runner **hook** reruns the suite on every edit; [`debug-circuit`](https://github.com/ProjectWaja/claude-skillcraft/tree/main/skills/debug-circuit) would break a fix-fail-repeat loop if one started.

---

## Level 5 — Orchestration

```
You: Add email/password login.
AI:  Decomposing into independent tracks, running in parallel:
     → subagent A: backend (handler, service, middleware, rate limit)
     → subagent B: frontend (form, validation, protected-route guard)
     → subagent C: tests (happy path, bad creds, logged-out redirect, lockout)
     [assembles the three results; the pre-commit hook blocks the merge until
      lint + tests pass; a scheduled job will flag the new endpoint in
      tomorrow's security sweep]
```

**What changed:** Three independent slices ran at once instead of in sequence, and enforcement (lint, tests, security sweep) is automated rather than remembered. You conducted; you didn't type every step.

---

## Level 6 — Authorship

You've done auth three times across projects. So you stop *redoing* it and *encode* it:

```
You: *authors an `auth-feature` skill capturing the whole pattern* —
     uniform 401s, httpOnly + SameSite cookies, bcrypt, rate limiting,
     no credential logging, the standard test matrix. Publishes it to the team.

Now, on every project, by anyone:
Teammate: Add email/password login.
AI:        [applies the auth-feature skill — every hard-won lesson from
            Levels 1–4 baked in, automatically, on the first try]
```

**What changed:** Your expertise stopped being something you *re-perform* and became something the system *applies*. The security leak from Level 4 can't recur — the skill forbids it. Everyone who installs it inherits your standard. That's leverage that compounds. → this is exactly what [claude-skillcraft](https://github.com/ProjectWaja/claude-skillcraft) is: disciplines turned into installable skills.

---

## The whole climb in one line

| Level | The login task is… |
|------:|--------------------|
| 0 | …insecure, generic, and yours to fix |
| 1 | …correct, after you steer it there |
| 2 | …correct *and* fits your project, with no preamble |
| 3 | …planned, scoped, and verified before "done" |
| 4 | …self-checked for security and simplicity before you see it |
| 5 | …built in parallel, with enforcement automated |
| 6 | …a reusable skill anyone can apply, getting all of the above for free |

Same model. Same task. The only variable that moved was **you**.

---

⬆️ [Back to the map](../README.md)
