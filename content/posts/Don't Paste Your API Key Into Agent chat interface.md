+++
date = "2026-07-15"
draft = true
title = "Don't Paste Your API Key Into Agent chat interface"
+++

Pasting a real API key into Lovable, Claude, or Cursor feels like telling your AI tool a secret. It isn't. Here's what happens instead — and what to do.

Last week I wrote about how deleting a file doesn't erase it from git history — and why API keys you thought you removed are probably still there. This is the earlier mistake. The one that happens before the delete.

You were trying to get the app to connect to Stripe, or OpenAI, or your database. The AI tool asked what credentials to use. So you pasted the key right into the chat.

It worked. The app connected. You moved on.

Here's what actually happened.
## What does the AI tool do with a key you paste into chat?

It uses it — and then it writes it into your code.

When you give a real API key to Lovable, Cursor, or Claude Code inside the chat window, the tool does the most natural thing: it puts the key wherever the code needs it. Usually hardcoded directly into the file. Because that's what you asked it to do, implicitly, by handing it the key.

Now the key is in your code. Which means it's in git. Which means — if you ever push to a public repo, or even a private one you share — it travels with every commit.

Beyond the code, the key was also in your conversation. AI tools retain conversation context. Depending on the platform and your settings, that conversation may be stored, logged, or used to improve the model. A credential in a chat window is not a secret. It's just text you typed.

---
## What's the right way to do it?

Use a `.env` file. This is a plain text file that lives in your project folder and holds your credentials separately from your code. You tell the AI tool: "the key is in the `.env` file as `STRIPE_SECRET_KEY`" — and it writes the code to read from there, not to contain the key itself.

One more step: make sure `.env` is in your `.gitignore` file before you commit anything. That tells git to never include it in your history. The key stays local. It never travels.

If you're not sure how to set this up, just ask your AI tool: _"Help me move my API keys to a .env file and make sure it's gitignored."_ It knows how to do this. You just have to ask before pasting the key.

**The one action: if you've already pasted a real key into an AI chat to get something working — rotate it now, and ask your AI tool to set up a `.env` file for the new one.**

The key you pasted is gone from the chat but it's probably in your code. A new key, stored the right way, costs five minutes. Not acting costs more.

Part of a series on credentials and secrets for vibe coders. Start with: 