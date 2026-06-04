
+++
date = '2026-05-15'
draft = false
title = 'Why this blog exist at first place?'
+++


A new publication for vibe coders & AI citizen developers building with AI platforms (by prompting) — and the quiet worry they carry.

You described (prompted) what you wanted. The AI built it. It worked.

You shipped it — a dashboard, an internal tracker, a customer-facing form, an automation that saves your team hours every week. Maybe it took an afternoon. Maybe less. You shared the URL, moved on, and started thinking about the next thing.

And somewhere in the back of your mind, a question you never quite named sat quietly: _is this okay?_

Not "will it break" — you know how to fix it with prompts. But, the question is different. It sounds more like: _who can see this data? Is it publicly exposed ? Could someone access what they should not? Am i allowed to share these information to AI? Are there passwords sitting somewhere they should not be?

You never asked anyone, because you did not know who to ask. And the AI tool that built it did not raise the question either.

That is the gap this publication exists to close.

---

## Who is this written for? {#who-this-is-written-for}

Two kinds of people read this. You are probably one of them.

**The vibe coder.** You build by describing. You may never have written a line of code in your life — and you do not need to. You use Lovable, Bolt, Replit, Cursor, or any AI platform (Claude or Codex) that takes a prompt and produces a working application. In an afternoon you can ship something real. That is genuinely powerful.

It is also where this publication starts. Because when you build by describing and the AI builds by generating, a set of security decisions gets made inside that process that nobody flags, nobody reviews, and nobody explains to you. The credential you pasted into the chat. The database with no access rules. The URL that went live without authentication. The app your whole team is using that your IT department does not know exists.

You were not trained to spot these things. The tools you build with were not designed to stop you from creating them. This publication translates those invisible decisions into plain English — and gives you the habits to make better ones, one build at a time.

**The AI citizen developer.** You are a professional in GTM, Sales, Operations, Marketing, Finance, HR, Customer Success, or Product — and AI tools have quietly turned you into a builder. Not a developer. A builder.

You are solving real business problems: the commission tracker your sales team depends on, the onboarding portal HR uses every day, the support dashboard that routes requests across three systems. You built all of it. Your organisation depends on it. And the governance frameworks your IT team uses were designed for a different era — before a marketing manager could ship a full-stack application on a Tuesday afternoon.

That gap — between how fast you can build and how much anyone has thought about what you built — is exactly what this publication addresses.

You do not need to become a security professional. You need to understand ten specific things, develop three specific habits, and know when to involve the people whose job it actually is. This publication gives you all of that, in plain English, one piece at a time.

---

## What will you actually learn here? {#what-you-will-actually-learn}

Not a list of vulnerability types with technical names. Not anything that assumes you have written code before. Not fear-based content that makes every tool you have built feel like a disaster waiting to happen.

Most AI-built internal tools work without incident. The goal here is not to alarm you — it is to give you a calibrated, honest picture of when you need to act and when you can move on.

Here is what you will learn:

**How to tell the difference between a tool that needs attention and one that is probably fine.** Most are fine. The ones that are not share three specific patterns. Learning those patterns is more useful than general anxiety about everything you have ever built.

**What your AI-built tool is actually doing with data.** Who can see it, where it is stored, what would happen if someone unauthorised got access, and what one change would fix the most common problems.

**How to protect credentials.** The passwords, API keys, and connection strings that give access to real systems — so they do not end up visible to anyone who knows where to look. This is the most common problem. It is also the most fixable.

**How to think about access control in plain English.** Not as a technical concept, but as the answer to a simple question: who should be able to use this, and who definitely should not?

**How to have the right conversation with your IT team before something goes wrong.** The vocabulary, the framing, and the moment to bring it up.

**How to build a simple, repeatable habit that covers the most common ways AI-built tools get exposed.** Two minutes. No technical knowledge required. Every time you build.

> The security skill you need is not technical. It is a set of questions you ask before you share — and a calibrated sense of when the answer matters.

---

## Why does this gap exist — and why now? {#why-this-gap-exists}

The security industry was built for two kinds of people: developers who write code, and security professionals who speak risk. Every tool, every publication, every pricing page assumes the reader is one of them.

Snyk, Semgrep, SonarQube — built for engineers who write code. Wiz, Nokod, Zenity, AppOmni — built for CISOs and SOC teams who manage security at the organisational level. Every piece of security content written in the last twenty years has assumed the reader either writes code or speaks security risk.

The vibe coder and AI citizen developer exist in neither world. They are not in the security industry's awareness because the security industry was not looking for them.

Sixty-three percent of active vibe coding users are non-developers. They are building real tools with real data — Salesforce connections, HR records, financial data — and the entire security industry has collectively decided they are not the customer. That is not a gap someone failed to close. It is a gap nobody thought to look for.

Meanwhile, three things are converging in 2026:

AI platforms have made building accessible to anyone with a prompt. The population of non-technical builders is growing from millions to hundreds of millions — and the tools are getting faster, not slower.

Regulation is tightening. GDPR, DORA, and emerging AI governance frameworks do not ask who built the tool that holds the data. They hold the organisation responsible regardless of who built it.

The window is time-limited. AI platforms are slowly improving their security defaults — but they are still two to three years away from absorbing the most critical basics. The education gap is acute right now.

The security industry will eventually catch up. The question is whether someone builds the education layer for non-technical builders before it gets commoditised into a settings toggle.

This publication is that education layer.

---

## The idea in one sentence {#the-idea}

Every vibe coder and AI citizen developer building real tools with AI platforms is making invisible security decisions they never approved — and nobody has built the education layer for them, because the entire security industry was designed for people who either write code or speak security risk, and most builders do neither.

---

## What this is not

This is not a publication for developers. If you write code, there are better resources for you — and this is not one of them.

This is not a fear publication. The opening sentence of every post that works here is a moment the reader has lived — not a statistic about how many breaches happened last quarter.

This is not a vendor publication. I work for a security start-up and build cybersecurity products at scale, which means I understand the space from the inside. It also means I know when a product solves a real problem for a builder and when it is solving a procurement problem for a CISO. I will be honest about the difference.

---

## If you manage or work alongside these builders

IT managers, team leads, and department heads watching their teams ship AI-built tools faster than any approval process can keep up with — this publication gives you the plain-English vocabulary to have the right conversations, the frameworks to build lightweight governance without becoming the person who blocks everything, and the perspective to understand what your builders are actually experiencing.

You are not the last line of defence. But you might be the most important bridge between the speed of building and the discipline of doing it safely.

---

One post per week. Plain English. One concept, one action, every time.

If you build with AI platforms and you have ever had the quiet thought — _is this okay?_ — this is written for you.


---

## Frequently asked questions {#faq}

**Do I need any technical background to read this?** No. Every post is written for someone who builds by describing, not by coding. Technical terms appear occasionally — and every one of them is translated into plain English immediately after it is introduced.

**I already shipped several AI-built tools. Is it too late?** No. Most AI-built tools are fine as they are. For the ones that are not, the fixes are usually simple and fast. This publication will help you identify which category your tools fall into — and what, if anything, to do about it.

**How is this different from every other security publication?** Every other security publication is written for developers or security professionals. This one is written for the person whose entire build process is a natural language prompt. That audience has never had a security publication written specifically for them. Until now.

**How often does this publish?** Once a week or every fortinight. One concept, one action per post. The goal is a habit you can build in ten minutes — not a reading list you fall behind on.

**I work in IT and my team is using AI tools I did not know about. Is this useful for me?** Yes. The publication gives you the vocabulary to have conversations with your builders without becoming the person who shuts everything down.

---
