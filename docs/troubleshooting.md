# Stuck? Read this 🛠️

Everyone hits errors, including people who have done this for years. An error is not a sign you can't do this. It's just the computer telling you exactly what it needs. This guide gets you unstuck fast.

## Do this first (works for almost everything)

1. Don't panic. This is normal.
2. Copy the **whole** error, top to bottom, not just the red line.
3. Paste it to Claude Code with one line of context: "I was trying to [what you did] and got this: [paste the error]. What's wrong and how do I fix it?"
4. If Claude tries the same fix twice and it still fails, stop. Type `/clear`, then describe the problem fresh. Two fails means the chat is confused, not that the problem is hard.
5. If Claude has clearly gone down a wrong path, type `/rewind` to go back to a working point.
6. Never accept "done" you haven't seen with your own eyes. Click the thing.

If the steps above don't crack it, find your error below.

## Machine and terminal

### `command not found: node` (or `npm`)
**What it means:** Node.js isn't installed, or your terminal can't find it.
**Fix:** Install Node from [nodejs.org](https://nodejs.org) (the LTS version). Close your terminal, open it again, and run `node --version`. You should see a number.
> Paste to Claude Code: "node --version says command not found. Walk me through installing Node LTS on [Mac or Windows] and checking it worked."

### `command not found: claude`
**What it means:** Claude Code isn't installed, or isn't on your PATH.
**Fix:** Reinstall Claude Code following the Module 1 install lesson, then open a fresh terminal.
> Paste to Claude Code (in a different app, or your phone): "The `claude` command isn't found in my terminal. Help me check whether Claude Code is installed and fix my PATH on [Mac or Windows]."

### `command not found: git`
**What it means:** git isn't installed.
**Fix:** Install it from [git-scm.com/downloads](https://git-scm.com/downloads), reopen your terminal, and run `git --version`.

### `permission denied` when you run `./setup`
**What it means:** the script isn't marked as runnable on your machine.
**Fix:** Run `sh setup` instead. That always works. (If you want the shorter `./setup`, run `chmod +x setup` once first.)

### "Port 3000 is already in use" (`EADDRINUSE`)
**What it means:** a dev server is already running, probably one you forgot about.
**Fix:** Use the URL it's already running on, or close the other terminal tab that's running it.
> Paste to Claude Code: "I get EADDRINUSE on port 3000 when I run the app. Find what's using it and either stop it or start my app on a free port."

## Environment and keys

### "Missing Supabase env vars", or nothing connects after you added your keys
**What it means:** your keys aren't loaded. Almost always because you edited `.env.local` but didn't restart the dev server, or a key name is slightly off.
**Fix:** Stop the dev server (press Ctrl+C in its terminal) and start it again. Environment files only load when the server starts. Then check the names in `.env.local` match `.env.example` exactly.
> Paste to Claude Code: "My app says the Supabase env vars are missing even though I filled in .env.local. Check my variable names against what the code expects and tell me exactly what's wrong."

### A key looks right but auth or payments still fail
**What it means:** you may have pasted a publishable key where a secret goes (or the reverse), or used the old Supabase key format.
**Fix:** Supabase uses `sb_publishable_...` for the browser and `sb_secret_...` for the server only. Stripe uses `pk_test_...` and `sk_test_...`. Never put a secret key in a variable that starts with `NEXT_PUBLIC_`.
> Paste to Claude Code: "Check every key in my .env.local is the right type in the right place (publishable vs secret), and that no secret key has a NEXT_PUBLIC_ prefix."

## Supabase

### Your data won't show, or you get a "row-level security" / permission error
**What it means:** Row Level Security is switched on, which is good, it stops one user reading another's data. But you haven't written a policy that lets the logged-in user see their own rows yet.
**Fix:** Have Claude add the right policy. Install `supabase/agent-skills` first, it stops Claude getting this wrong.
> Paste to Claude Code: "Install supabase/agent-skills if it isn't already, then add Row Level Security policies so a logged-in user can read and write only their own rows in [table name]. Show me the SQL before you run it."

### "Invalid login", or you land on a broken page after signing in (especially after deploying)
**What it means:** Supabase doesn't recognise your live site's URL, so it blocks the redirect.
**Fix:** In Supabase, add your Vercel URL to the allowed redirect URLs under Authentication settings.
> Paste to Claude Code: "After deploying, login redirects to a broken page. Walk me through adding my production URL to Supabase's allowed redirect URLs."

## Stripe

### You pay with the test card but your app never updates (the webhook isn't firing)
**What it means:** on your own machine, Stripe can't reach your app unless you forward its events with the Stripe CLI.
**Fix:** In a separate terminal, run `stripe listen --forward-to localhost:3000/api/stripe/webhook`. It prints a signing secret starting `whsec_`. Put that in `.env.local` as `STRIPE_WEBHOOK_SECRET`, then restart your app.
> Paste to Claude Code: "Stripe payments succeed but my app never hears about it on localhost. Set me up with `stripe listen`, tell me exactly where to put the signing secret, and how to test with card 4242 4242 4242 4242."

### "No signatures found matching the expected signature"
**What it means:** your `STRIPE_WEBHOOK_SECRET` is wrong or out of date.
**Fix:** Copy the `whsec_...` secret that `stripe listen` prints (for local testing) or the one from your webhook settings (for production) into `.env.local`, then restart.
> Paste to Claude Code: "I get 'No signatures found matching' on my Stripe webhook. Check my STRIPE_WEBHOOK_SECRET is the right one for where I'm testing and fix it."

### Your test payment is declined
**What it means:** you're probably not using a test card, or you're in live mode by mistake.
**Fix:** Use card `4242 4242 4242 4242`, any future expiry date, any CVC, any postcode. Make sure your Stripe keys are the `..._test_...` ones.

## Deploy (Vercel)

### It works on your machine but the Vercel build fails
**What it means:** usually one of two things. Either your environment variables aren't set on Vercel, or an import uses the wrong capitalisation (your Mac ignores case, Vercel's Linux servers do not).
**Fix:** Add every key from `.env.local` into Vercel's project settings under Environment Variables, then have Claude check your imports for case mismatches.
> Paste to Claude Code: "My app builds locally but the Vercel build fails with [paste the error]. Check for missing env vars on Vercel and any import paths with the wrong capitalisation."

### Your custom domain won't connect
**What it means:** DNS changes take time to spread across the internet, or the records aren't quite right.
**Fix:** Add the domain in Vercel, copy the DNS records it gives you to your domain registrar, then wait. It can take a few hours.
> Paste to Claude Code: "I added my domain in Vercel but it isn't loading. Walk me through the exact DNS records to add at [your registrar] and how to check whether it has propagated."

## When Claude itself is the problem

### Claude says a feature is "done" but it isn't
**What it means:** it sometimes writes a placeholder instead of the real thing, or assumes it worked without checking. This is the single most common way non-coders get burned.
**Fix:** Never take "done" on trust. Click the thing yourself. If it's fake, say so plainly.
> Paste to Claude Code: "You said this is done but here's what I actually see: [describe it]. Don't tell me it works, show me where it's implemented and let's test it by clicking through it together."

### Claude keeps failing the same fix over and over
**What it means:** the chat's memory is polluted. It's now arguing with its own earlier mistakes.
**Fix:** Stop after two failed attempts. Type `/clear` for a fresh chat (or `/rewind` to roll back to a working point), then describe the problem cleanly from scratch.
> Paste to Claude Code (after `/clear`): "Fresh start. Here's the situation: [describe the bug plainly, with the full error]. Plan a fix before you change anything."

## Still stuck?

That's exactly what **Weekly Build Club** is for. Bring the error to the live call, or post it in the community with the full error and what you've already tried. Someone has almost certainly hit the same wall.
