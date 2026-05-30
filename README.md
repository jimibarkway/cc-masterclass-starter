# Claude Code Masterclass, Starter

Your clone-and-go foundation for building a SaaS with Claude Code. This is the workspace, not the app. You build the product yourself in Module 3. This just removes the boring setup so you can start on the fun part.

## Setup (3 steps, about 5 minutes)

1. Click **Use this template** at the top of this repo on GitHub, name your copy (for example `my-saas`), then clone it to your machine.
2. Open the folder in your editor with Claude Code.
3. In your terminal, run:

   ```
   ./setup
   ```

That checks your machine, prepares your environment file, and tells you exactly what to do next.

## What's in here

- `CLAUDE.md`, the brain. Claude Code reads it every session so you never re-explain your project, stack, or standards.
- `.env.example`, every key your app needs, with notes on where to get each one.
- `.claude/`, your project settings and the skills reference.
- `docs/stack.md`, a one-pager on every tool you'll use, what it costs, and when to upgrade.
- `docs/prompt-pack.md`, the exact prompts to paste into Claude Code at each step of the build.
- `docs/troubleshooting.md`, the "stuck? read this" guide for the errors you'll actually hit.
- `setup`, the one command that gets you ready.

## What's not in here (on purpose)

No app code, no auth, no payments. You build all of that with Claude Code during the course. That's the point. You learn by building it, not by inheriting it.

## First move

After `./setup`, open Claude Code in this folder and say:

> Read CLAUDE.md, then help me fill in the project details at the top.

See you in the lesson.

## When you get stuck

Open `docs/troubleshooting.md`. It covers the errors a first-time builder actually hits (Node not found, env vars not loading, Supabase row-level-security, Stripe webhooks, Vercel build fails) with the fix and the exact prompt to paste into Claude Code for each one.
