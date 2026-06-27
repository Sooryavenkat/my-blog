+++
date = "2026-06-28"
draft = false
title = "You Deleted the API Key But Git Didn't"
+++

If you've ever pasted an API key into your code by using an AI agent claude or Lovable and later removed it, it may still be in your git history — visible to anyone with access to your repo. Here's what to check.

You needed the app to talk to an API - Stripe, OpenAI, Supabase, Resend — whatever it was. You copied the key, pasted it into the code so it would work, tested it, and it did.

Later, maybe you read something about not putting keys in code. So you moved it to a `.env` file, or deleted that line, or both. And you moved on.

Here's the part nobody explains to you: git remembers everything.
## What does git actually store?

Git is the version control system underneath GitHub. Every time you save and push your code, git takes a snapshot. Not just of what the code looks like now — of every change you've made, going all the way back to the beginning.

That history is the point. It's how you can undo things, see what changed, recover from mistakes.

But it also means this: if your API key was in a file in commit number 7, and you deleted it in commit number 12, the key is still sitting in commit 7. Anyone who can read your repository can scroll back through its history and find it.

If your repo is public — it's already out there. If it's private, the risk depends on who has access. But "private" is not the same as "safe."
## Why does this matter more than you think?

API keys are not just passwords. They are permissions slips. A Stripe key can charge cards. An OpenAI key can rack up API costs on your account. A Supabase service key can read and write your entire database.

When a key leaks, the attacker doesn't need to break in. They just use the front door with credentials you handed them.

Automated bots scan public GitHub repos continuously looking for exactly this. Within minutes of a key appearing in a public commit — not hours, minutes — bots will have found it. By the time you notice and revoke it, the damage may already be done.

> The key you deleted last week is still in your git history. And git history is readable by anyone who can see your repo.

This isn't a scare story. It's just how git works — and once you know it, you can't unknow it.
## Who does this apply to?

If you built something with Lovable, Bolt, Cursor, Replit, or any AI coding tool and pushed it to GitHub, this applies to you — especially if you connected any third-party service along the way.

If your repo has never had any API keys or credentials in it — if you used environment variables from the very beginning and never committed a key directly — then you're fine. This post is not for you.

If you're not sure, that's the most common situation. Most people aren't sure. And not being sure is a good reason to check.
## What should you actually look for?

Open your repo and think back through the services you connected. Any key or secret that you ever typed or pasted directly into a code file — even briefly — is worth checking.

Common things that end up in git history by accident: OpenAI API keys, Stripe secret keys, Supabase service role keys, Resend or SendGrid API keys, database connection strings (which often include a password), and `.env` files that were accidentally committed before being added to `.gitignore`.

That last one is worth a specific mention. The `.gitignore` file tells git which files to ignore. If you created your `.env` file and then added it to `.gitignore` — but the `.env` file was already committed once before that — it's in the history. Gitignore only prevents future commits. It doesn't erase the past.
## What's the one thing to do?

**Assume any key you've ever pasted directly into a code file has been seen — and rotate it.**

Rotating a key means going to the service that issued it (OpenAI, Stripe, Supabase, wherever), revoking the old one, and generating a new one. The old key becomes useless. Whatever was exposed is now dead.

This takes about five minutes per service. You don't need to understand git history, you don't need to rewrite your commits, you don't need a developer. You just need to log in and revoke.

After rotating, set the new keys as environment variables in your deployment platform — Vercel, Netlify, Railway, wherever you host — rather than in the code itself. Most platforms have a "Environment Variables" section in settings. That's where keys live. Not in your files.

One key rotated today is better than ten "I'll deal with it later" situations sitting in your history.

## Frequently asked questions

**My repo is private. Am I safe?** Private means fewer people can see it — not zero. Anyone you've added as a collaborator, any tool you've connected to the repo, and GitHub itself can access it. If you accidentally make it public even briefly, bots will have scanned it. Rotating exposed keys is still the right move regardless of repo visibility.

**What if I already deleted the `.env` file — isn't that enough?** No. Deleting a file removes it from your current code but not from git history. The commit where it was added still exists. To fully remove it you'd need to rewrite your git history, which is complex — rotating the key is faster and more reliable.

**Do I need to check every project I've ever built?** Start with anything that's publicly accessible or connected to a paid service. That's where real exposure lives. Old experiments that never went live and have no real credentials are lower priority.

**What if I've already been charged or had unusual activity?** Revoke the key immediately, contact the service's support team, and dispute any charges you didn't authorise. Most services have a process for this — they've seen it before.
