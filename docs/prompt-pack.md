# The Prompt Pack 🎯

Your real superpower in this course is asking for the right thing, the right way. These are the exact prompts that work, in the order you'll need them. Copy one, fill in the `[bits in brackets]`, paste it into Claude Code. Steal them shamelessly.

Three rules that make every prompt land better:
- One thing at a time. Don't ask for five features in one go.
- Let it plan before it builds (superpowers does this for you).
- After anything important, click the thing yourself. "Done" means you saw it work.

## Setup and planning

**Fill in your project brain** (right after `./setup`)
```
Read CLAUDE.md. Ask me 5 questions, one at a time, to fill in the Project section at the top (name, what it does, who it's for, the promise). Then write my answers into CLAUDE.md.
```

**Spec your MVP** (the most important prompt in the course)
```
Help me spec the smallest version of [my product] that someone would pay for. I want ONE core loop, plus login and one dashboard, nothing else. Ask me what the single core action is, then write a one-page spec. Don't write any code yet.
```

## Scaffold (Module 3)

**Plan the app**
```
Plan a new Next.js 16.2 app for [my product]. App Router, TypeScript, Tailwind. Supabase for auth and database, Stripe for payments, ready to deploy on Vercel. Don't write code yet, show me the plan first.
```

**Wire up Supabase**
```
Now wire up Supabase using the Supabase MCP. Create the client and the env variables in .env.local using the new sb_publishable_ and sb_secret_ key format. No tables yet, we'll do data next.
```

**Wire up Stripe (test mode)**
```
Now add Stripe using the Stripe MCP, test mode only. Just the connection and keys for now, no checkout yet.
```

**Run it and check**
```
Run the app locally and tell me the URL. I'll open it and confirm it loads.
```

## Auth and database (Module 3)

**Safe login and your first table**
```
Install supabase/agent-skills if it isn't already. Then add email and password login with Supabase, and create a [thing] table for my core feature. Add Row Level Security so a logged-in user can only see and edit their own rows. Show me the SQL before you run it.
```

**Add a table later**
```
Add a [name] table with these columns: [list them in plain English]. Add Row Level Security so each user only sees their own rows. Show me the plan and the SQL first.
```

## Payments (Module 3)

**Checkout and customer portal**
```
Add Stripe Checkout so a user can subscribe to [plan name] at [price] per month, plus the Stripe Customer Portal so they can manage or cancel. Test mode. Put the webhook in app/api/stripe/webhook/route.ts, verify the signature, and grant access when checkout.session.completed fires.
```

**Test the webhook locally**
```
Set me up to test Stripe webhooks locally with `stripe listen`. Give me the exact command, tell me where to put the signing secret, and how to pay with test card 4242 4242 4242 4242 so I can watch my app update.
```

## Make it look designed (Module 3)

**Audit and polish the UI**
```
Run impeccable /audit on my landing page and core screens. Show me the top 5 things that make this look AI-built, then fix them with /polish. Don't touch the core logic, just the look.
```

## Deploy (Module 3)

**Ship it**
```
Deploy this to Vercel and tell me the live URL. First make sure every key from my .env.local is set in Vercel's environment variables. If the build fails, read the error and fix it before telling me it's done.
```

**Connect a domain**
```
I bought [yourdomain.com]. Walk me through connecting it to my Vercel project: the exact DNS records to add at [registrar], then how to check it's live.
```

## Get your first customers (Module 4)

**Rewrite your landing page to convert** (the highest-leverage money prompt)
```
Use the direct-response copywriting skill and marketingskills/page-cro. Here's my current hero: [paste headline and subhead]. My customer is [who] and their painful problem is [what]. Rewrite it to convert: an under-10-word headline, a clear subhead, one obvious call to action. Give me 3 options.
```

**Twitter build-in-public hooks**
```
Use the direct-response copywriting skill. I'm building [product] for [audience] in public on X. Write me 5 post hooks about the problem it solves, plus a thread outline showing the product solving a real problem. Plain and specific, no hype.
```

**Onboarding emails (no code)**
```
Using the Zapier SDK, set up an onboarding email sequence triggered on signup: a welcome email, a day-3 nudge to do [the core action], and a day-7 trial-ending email. Write the copy too: short, friendly, UK English, no AI tells.
```

## Iterate to product-market fit (Module 5)

**Turn feedback into a build**
```
Here are 5 things customers said this week: [paste]. Find the single most common unmet need, then write a one-page spec for the smallest feature that solves it. Plan it before any code.
```

**Diagnose churn**
```
Look at my Stripe data and split my cancellations into voluntary (they chose to leave) and involuntary (a payment failed). For the involuntary ones, set up Stripe dunning with the Zapier SDK so failed payments retry and the customer gets a heads-up.
```

## Scale to $10K (Module 6)

**Operations on autopilot**
```
Using the Zapier SDK, set these up so I never do them by hand: a Slack ping when someone subscribes or cancels, a weekly KPI digest email (new customers, churn, MRR), and a payment-failed recovery flow. Plan it first, one workflow at a time.
```

## Everyday workflow

**When Claude claims it's done**
```
You said this is done. Show me exactly where it's implemented, then let's test it by clicking through it together. Don't mark it done until I've seen it work.
```

**When it's stuck in a loop** (after `/clear`)
```
Fresh start. The problem is: [describe it plainly]. Here's the full error: [paste]. Plan a fix before you change anything.
```

**Save your work**
```
Commit this with a clear message.
```
