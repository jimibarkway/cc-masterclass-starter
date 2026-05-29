# CLAUDE.md

> **How to use this file**
> This is your project's brain. Claude Code reads it automatically every time you start a session, so you never have to re-explain yourself. Edit the bits in `<<...>>` first. Everything else can stay as-is until you have a reason to change it. Once you've filled it in, commit it.

## Project

**Name:** <<your-saas-name>>

**One-line description:** An AI-powered <<thing>> for <<specific job role>> who currently <<painful manual workaround>>.

**The user:** <<one paragraph on your ideal customer: who they are, what they do all day, what they're paid to do, where they hang out online>>.

**The promise:** <<the single sentence the customer would say to a friend if they loved your tool>>

## Stack

- **Frontend:** Next.js (App Router) + Tailwind + shadcn/ui
- **Backend:** Supabase (auth, Postgres, RLS), with the Supabase MCP installed via Claude Code
- **Payments:** Stripe (subscriptions, webhooks), with the Stripe MCP installed via Claude Code
- **Deployment:** Vercel (preview + production)
- **AI:** Anthropic API (`claude-sonnet-4-6` for product work, `claude-haiku-4-5-20251001` for cheap calls)
- **Backend automations:** Zapier SDK (anything that talks to a third-party app I'd otherwise integrate by hand)

See `docs/stack.md` for what each tool costs and when to upgrade.

## How to talk to me

I'm not a developer. I'm an architect. When I ask for something:

- Plan first. Use plan mode (or the `superpowers` brainstorm to write-plan flow) before you touch any code.
- Show me trade-offs. If there are two reasonable approaches, name both with one-line pros and cons. Don't just pick.
- Verify before claiming done. Run the build, run the tests, click through the UI. If you can't verify it, say so out loud.
- Quote real file paths and line numbers when you reference code.
- Don't invent. If you don't know a library's API, say so and look it up. Don't guess.
- No silent scope creep. If you spot a refactor that isn't in the task, mention it as a follow-up. Don't do it without asking.

## Workflow discipline

Every feature runs the same loop: **spec, plan, build, verify.** One feature at a time.

1. **Spec.** I tell you what I want in plain English.
2. **Plan.** You write a short plan before touching files. I read it and correct it while it's cheap.
3. **Build.** You write the code against the approved plan.
4. **Verify.** I click the thing and see it work. "Done" means I saw it work, not that you said so.

Keep the context clean so quality stays high:
- `/clear` between unrelated tasks. Fresh chat per feature, fresh chat per bug.
- `/compact` in a long session that's going well.
- `/rewind` when you've clearly gone down a wrong path, instead of arguing with a confused session.
- If the same bug fails twice, stop. `/clear`, rewrite the request more clearly, start fresh. Two fails means the context is polluted, not that the bug is hard.

## Voice for anything customer-facing

Anything that ends up in front of users (landing-page copy, emails, in-app text, error messages) gets written like a smart best friend.

**Use:**
- Second person, contractions ("you'll", "we've").
- Short sentences. Specific numbers. Real examples.
- UK English in marketing copy. American English inside code (variable names, library calls).

**Avoid these AI tells** (full reference: the tropes.fyi gist, linked in the Skills Vault):
- "Delve", "tapestry", "navigate (a journey)", "embark", "unlock the power of", "unleash", "harness".
- "It's not X, it's Y" parallel structure (dead giveaway).
- "Whether you're a beginner or a seasoned pro...".
- **Zero em dashes.** Never use the em dash character (Unicode U+2014). Use full stops, commas, parentheses, or rewrite. This is the single most well-known AI tell, we don't ship a sentence that contains one.
- "In today's fast-paced world...", "In the realm of...", "In a world where...".
- Bolded keywords inside every bullet.
- Three sentences in a row starting with the same phrase.
- False suspense ("There's one thing nobody talks about...").
- "Quietly", "serves as", "stands as a testament to", "Let's dive in".

Before any customer-facing copy ships, run a one-pass cleanup against this list.

## Code conventions

- **TypeScript everywhere.** No `any`. If you're tempted, name the type properly.
- **Server components by default.** Use `"use client"` only when you genuinely need React state, browser APIs, or event handlers.
- **One Supabase client per route handler.** Don't share clients across requests.
- **Supabase keys: new format only.** `sb_publishable_...` for the browser, `sb_secret_...` server-side only (treat the secret like a password). Never use the legacy `anon` / `service_role` keys, and never give a secret key a `NEXT_PUBLIC_` prefix.
- **Stripe events in `app/api/stripe/webhook/route.ts`.** Verify the signature, switch on event type, return 200 fast, do heavy lifting in a Zapier action or background task.
- **Errors:** throw at boundaries (route handlers, server actions). Don't swallow errors with empty catch blocks.
- **Comments:** only when the WHY isn't obvious. Code that explains itself doesn't need a sticker on it.

## What "done" means

Before you say a feature is done, ALL of these must be true:

1. The feature works end-to-end on a fresh Vercel preview deployment.
2. A logged-out user gets redirected sensibly (no white screens).
3. A logged-in user with no data sees a useful empty state.
4. The Stripe test card `4242 4242 4242 4242` completes a paid flow if billing is involved.
5. The build passes on the Vercel preview (no TypeScript errors).
6. Customer-facing copy has been run through the AI-tells filter above (zero em dashes, no banned phrases).

If any of those is false, the feature is not done. Tell me what's left and what's blocking.

## What I will never want

- A feature that "anyone could use." I sell to one specific job role. Generic features are anti-features.
- A hero headline like "Supercharge Your Workflow With AI". Specific outcomes only.
- A pricing page with three tiers when one would do.
- A new top-level dependency without telling me what problem it solves and what we'd otherwise write by hand.

## When in doubt

Ask me one specific question. Not "do you want me to add tests?" but "the auth flow has no tests, should I add a Playwright test covering signup to first-paid-event?". Specific questions get fast answers.
