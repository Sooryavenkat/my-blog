
+++
date = '2026-05-15'
draft = false
title = 'Your Users Are Already Building the UI Your Product Never Shipped — Here's Where It Should Live'
+++

Your most capable user is doing something you haven't shipped yet.

They've connected your product to Claude via MCP. They've pulled in data from their scanner, ticketing system, their CRM, and product analytics tools. They've described what they want the output to look like — not just the data, but the layout, widget, filters, the status badges on each row. And an AI built it for them, in natural language, in about twenty minutes.

Then they exported it as an HTML file or PRF and shared it to their team via slack or email.

That ad-hoc attachment is the product gap nobody has named yet. I'm calling it the **malleable workspace problem** — and it's a product decision every SaaS PM is sitting on right now, whether they know it or not.

And to be clear about when it actually matters: if the job is one-off, the PDF or HTML file is fine. Build it in an AI client, share it in Slack, move on. That workflow is perfectly reasonable for a one-time analysis or an ad hoc request.

The malleable workspace problem is different. It shows up when the job is recurring — when the same file needs to be downloaded every Monday morning, or every time a new incident fires. When other team members need to consume it consistently, and the UI has to look the same every time so they know what they're looking at. When someone else needs a slightly different version of the same thing — same data source, different filter, different scope. Or when the initial build was good but the team wants to iterate on it, improve it, make it smarter over time without starting from scratch. Those are the jobs that break down when the output lives in slack or email. They need a home.


## What are your power users actually doing? {#what-power-users-are-doing}

They're composing UI. Not choosing from a widget library you built. Not submitting a feature request and waiting six sprints. They're describing what they need, iterating it through conversation, and producing something that does the job better than your product ever offered natively — because it's scoped exactly to their team's needs.

For example: A PM connecting to Pendo MCP, CRM for subscription details, and her own product to get context to an AI client. She prompts to build a workflow that addresses the team's problem — feedback routed by PODs, feedbacks scored by account value, filtered by exactly the criteria her squad uses and prioritizes the items for next quarter. So she saves it as an HTML file and posts it in Slack and she may collate the prompt as a skill and shares with other PMs. (They have to repeate the same steps) 

What if she is able to send the output (list view of all feebacks with priority) within pendo application so that everyone in the product and program team can view and add comments.

The interface is real. The workflow is real. The only thing missing is a place inside pendo product where it lives, stays current, and is used by the whole team without anyone emailing a file.

That gap is the product decision.

## What does "malleable workspace" mean for your product? {#what-malleable-workspace-means}

It's a surface inside your product — may be a tab or a subsection — where users can publish UI they composed with AI. Not templates you pre-designed. Not widgets you hardcoded for everyone. Interfaces they built themselves, shaped until they look and behave exactly the way their team needs.

Once they're satisfied, they publish it. It becomes a live, team-accessible interface inside your product. Not a one-time export. A surface your product keeps current.

> _The distinction: you're not building the AI. You're deciding where the AI's output lives — inside a domain context environment._

The reason this matters for retention is simple. Every interface a team builds and publishes inside your product is a reason to open it again tomorrow. And every new colleague who onboards into that interface is a reason not to leave.

## Three pushbacks worth taking seriously {#three-pushbacks}

**"SaaS UI is going away in the agentic era."**

Satya Nadella declared SaaS was dead in late 2024. The argument: AI agents interact with APIs and databases directly — they don't need UI & dashboards. And there's something to it.

But notice what the agentic era actually produces: UI built through natural language. The screen doesn't go away. The process for creating it changes. What Nadella's argument (and Girish Mathrubootham's extension of it) actually describes is _"describe an app in English, a working version appears."_ That's not the elimination of UI — it's UI composition without product & engineering. The output still needs to live somewhere the team opens every morning, reviews, and builds on top of. Malleable workspace is how that happens inside your product rather than in a shared Google Drive folder.

**"Users can just build custom tools with MCP."**

Technically yes. Practically, it breaks the moment they try to share it.

One analyst's custom tool is a productivity win. What happens when that tool needs to be used by a 200-person team? Who provisions access? Who deprovisions it when the person who built it leaves? Which prompts ran, against which data, and when — for the compliance audit? Does the data cross regional boundaries?

Every custom MCP tool built outside your product carries those questions as unresolved overhead. Malleable workspace solves them once at the product layer — auth, RBAC, audit logging, and data residency are already there. Every published interface inherits them automatically.

**"Won't Claude or Slack just build this?"**

Claude Cowork is a general-purpose canvas. Slack's Claude integration knows your communication graph — it does not know your data model, your asset hierarchy, or your domain-specific risk logic. The interfaces your users need can only be built by something that understands your domain. That's the moat. A horizontal workspace is infrastructure. A malleable workspace inside your product is domain intelligence.

## What does the workflow actually look like? {#workflow-in-practice}

Take a security operations team that wants a live operations interface — the kind that's never been quite right out of the box because their needs are too specific.

1. **They start in an AI client.** A prompt: "Build me an interface that shows critical vulnerabilities by asset group, with trend lines from the last 30 days and a ticket status column." They're describing the shape of the thing, not just the data.
    
2. **They refine it.** They iterate the layout, adjust analysis logic, add a second data source. The agent builds and rebuilds until it looks right. UI composition through conversation.
    
3. **Instead of exporting, they publish.** The UI lands in the malleable workspace tab inside your product. The team opens your product the next morning and it's there — interactive, live.
    
4. **Your product keeps it current.** A background job re-runs the MCP queries and refreshes the data automatically. The interface stays accurate without anyone managing it.
    
5. **The workspace compounds.** A teammate wants the same interface scoped to enterprise accounts only. They click the existing widget, write a new prompt inline. A new panel appears beside the first. Same data source, different query. The workspace grows as the team's needs grow.
    

What you're building as a PM is not the AI. It's the surface: the workspace tab, the publish action, the scheduled data refresh job, role-scoped visibility controls, and the inline prompt on existing panels. Auth and RBAC you already have — every published interface inherits them.

## What should you ask engineering before putting this on the roadmap? {#question-for-engineering}

Before you think about use cases or pilot teams, there's one question to answer — and it belongs in a room with your engineering lead, not your customers.

**Can your product receive and render something it didn't build?**

Malleable workspace assumes your product can accept AI-generated UI output — an HTML structure, a rendered component — and host it as a first-class surface. In most existing SaaS architectures, that's not trivial.

Put these five questions to your engineering team:

**01 — Can we render AI-composed UI inside our product safely?** If a user publishes AI-generated HTML, can we sandbox and render it without creating XSS — which means a cross-site scripting risk — or injection vulnerabilities? What does that containment layer look like?

**02 — Can our data layer pass real product data to an external AI call?** Malleable workspace needs to route live data to a language model API at render time or on a schedule. Does your current data access model support that?

**03 — Can our existing auth and RBAC extend to user-published surfaces?** A panel published by one user needs to respect the permission model of every user who opens it. Does your access control layer work at that granularity?

**04 — Can we run a scheduled job that re-queries an MCP connection and refreshes stored output?** This is the keep-it-current mechanism — it requires a job runner, a stored prompt reference, and a way to update a rendered surface without user intervention.

**05 — What is our stance on calling the Claude API from within the product?** Every prompt routes to a language model in the background. Is there a security review, a vendor approval, or a data handling policy that governs this — and how long does it take to clear?

The answers tell you whether this is a two-sprint experiment or a multi-quarter infrastructure investment. Know that before you promise anything to a customer.

## How do you pitch this internally? {#how-to-pitch-internally}

Don't frame it as a dashboards upgrade or a reporting feature. The question you're answering is: where does the UI your users build with AI live after the chat window closes?

Right now it lives in their email or chat. You're offering an alternative — it lives in your product, governed, domain-aware, and current.

Three lines that land well in a roadmap review:

_"Our power users are already building custom UI with our data. We could be the place that UI lives and stays current — with zero additional governance overhead."_

_"Every interface a team builds and publishes inside our product makes us harder to leave. It's compounding retention, not a feature sprint."_

_"We're not building the AI. We're deciding where the AI's output lives — and that distinction is available to claim before someone else does."_


**The one action:** Before your next product review, ask your engineering lead one question — "Can our architecture host something our users built, not us?" The answer tells you more about your real timeline than any roadmap exercise.

## Frequently asked questions

**Is this only relevant for enterprise SaaS products?** No — but the governance payoff (auth, RBAC, audit logging inherited automatically) is most visible at enterprise scale. Even a small SaaS product benefits from having a first-class home for AI-composed interfaces rather than sending users to email attachments or Google Drive. The architecture questions are the same at any size.

**What's the difference between malleable workspace and a low-code dashboard builder?** A dashboard builder gives users a widget library you pre-built — they compose from your components. Malleable workspace accepts AI-generated UI your users composed in natural language, outside your product, then publishes it as a first-class surface inside it. The user isn't choosing from your options. They're bringing something they built.

**Do users need to understand MCP to use this?** No. The MCP connection happens at the backend — your product is the surface that hosts the result. Users interact with the published interface the same way they use any part of your product. The AI client experience (where they compose the UI) requires MCP awareness, but using and sharing the published interface inside your product doesn't.

**What happens to published interfaces when the user who built them leaves?** That's one of the governance questions to solve at the product level before launch — who owns the interface, what happens at offboarding, what the lifecycle policy is. It's not complex, but it's the kind of thing that needs to be in the spec from day one, not retrofitted.
