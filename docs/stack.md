# Your stack, in plain English

What each tool does, what it costs, and when you have to upgrade. Keep this open while you build.

## Next.js (the app framework)
- **What:** the framework your whole app is built in (pages, routing, server logic).
- **Cost:** free, it is open source.
- **Upgrade trigger:** none, it is just code.

## Supabase (database + auth + storage)
- **What:** stores your data, handles signup and login, and keeps each user's data separate and secure (Row Level Security).
- **Cost:** free tier is generous (500MB database, 50k monthly active users).
- **Upgrade trigger:** Pro is $25/month. Move when you outgrow the free database size or need daily backups, usually well after your first paying customers.

## Stripe (payments)
- **What:** takes the money. Subscriptions, checkout, customer portal, webhooks.
- **Cost:** no monthly fee. They take roughly 2.9% plus 30c per successful charge.
- **Upgrade trigger:** none, you only pay when you get paid.

## Vercel (hosting)
- **What:** puts your app on the internet at a real URL, with a fresh deploy on every push.
- **Cost:** the Hobby tier is free.
- **Upgrade trigger:** Pro is $20/month, and you MUST upgrade the moment you have a paying customer, because the Hobby tier prohibits commercial use. Pair this with Supabase Pro around the same time.

## Zapier SDK (backend automations)
- **What:** connects your app to 9,000+ other apps (email, Slack, CRMs) without writing integration code.
- **Cost:** free during open beta.
- **Upgrade trigger:** check Zapier's pricing when the beta ends.

## Anthropic API (the AI inside your product, if any)
- **What:** powers any AI features inside your app.
- **Cost:** pay per use, tiny while you are small.
- **Upgrade trigger:** none, it scales with usage. Watch it once you have real traffic (see Module 6, cost optimisation).
