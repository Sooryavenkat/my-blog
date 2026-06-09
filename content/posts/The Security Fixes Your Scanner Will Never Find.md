
+++
date = '2026-05-30'
draft = false
title = 'The Security Fixes Your Scanner Will Never Find'
+++

Cybersecurity for product managers means more than CVE tracking. Silent security fixes — patches without a CVE ID — are a real gap in most dependency audits. Here is what to ask your team about.

Your engineering team runs a dependency scan before every release. The scanner comes back clean. Everyone moves on.

Here is the thing: clean does not mean safe. It means no vulnerabilities were found with a name tag. A large category of security fixes never get a name tag at all.

---

## What is a silent security fix — and why should a PM care?

A silent security fix is when an open-source maintainer patches a security vulnerability, ships the update, and moves on — without filing a formal CVE.

CVE stands for Common Vulnerabilities and Exposures — which is the official database that most security scanners use to check whether your software has known vulnerabilities. If a fix never gets a CVE, most scanners will never surface it. Your product could be running an older, vulnerable version of a library, and your scan will return green.

This is not a theoretical risk. Research across the Wolfi OS ecosystem — a widely-used container package registry — identified over 100 security-relevant fixes across 600 projects that had no associated CVE. Those fixes existed. The CVE did not.

> **The gap is not in your scanner. The gap is in what the scanner is designed to look for.**

---

## Why do maintainers skip the CVE process?

Because filing a CVE is optional, time-consuming, and — for smaller projects — often not prioritised.

Maintainers are fixing real bugs. Some of those bugs have security implications. Some do not. The maintainer writes the fix, notes it in the release changelog or commit message, and ships it. Whether that fix gets a formal CVE depends on whether someone — the maintainer, a researcher, or a vendor — decides to file one.

That process can take weeks. Sometimes it never happens at all.

The result: the fix exists in the newer version of the library. The vulnerability exists in the older version your product is running. Your scanner, which checks against the CVE database, finds nothing because the database has no record of this particular vulnerability.

---

## What does this mean for your product specifically?

If your product depends on open-source libraries — and almost all modern products do — you have exposure to this gap right now.

The practical consequence is this: your security team or scanner vendor may be reporting a clean bill of health based on a deliberately incomplete signal. They are not wrong. They are using the standard method. The standard method has a known blind spot.

Working on security products, I see this pattern in vulnerability data across ecosystems consistently. This is not a corner case — it is a structural gap in how the industry tracks patched vulnerabilities. The [PM] who understands this has a more accurate model of what "clean scan" actually means.

---

## When does this matter most — and when can you move on?

This matters most in two situations.

First: when your product is in a regulated environment — fintech, healthtech, enterprise SaaS — where a supply-chain incident carries regulatory or contractual consequences. In those contexts, the question is not "did the scanner find anything?" but "are we running the latest patched versions of our dependencies?"

Second: when your product relies heavily on open-source libraries from smaller, less-resourced projects. Larger vendors (Google, Microsoft, major cloud providers) have dedicated security disclosure processes. Smaller open-source projects often do not.

If your product is a low-sensitivity internal tool with no regulated data, this is useful context but not an immediate action item. The calibration matters: most products running reasonably current dependencies are fine. The risk is concentrated in outdated, unmonitored dependency trees.

---

## What is the one question to bring into your next sprint review?

Ask your security team or engineering lead: **"Are we running the latest versions of our key dependencies — not just scanning for known CVEs?"**

This is the gap the silent fix problem exposes. The answer to that question tells you whether your current scan is a complete picture or a partial one. You do not need to know which libraries are affected. You need to know whether your process is designed to catch fixes that exist but were never formally disclosed.

That question — about version currency, not just CVE match — is the product security decision this post is about. It belongs in your security acceptance criteria for every release.

---

## Frequently asked questions

**Does this only affect open-source software?**
Primarily yes. Commercial software vendors typically have formal vulnerability disclosure processes and maintain CVE records. Open-source maintainers are not required to file CVEs, which is where most silent fixes occur. That said, most modern products use a mix of both.

**Is keeping dependencies up to date enough to close this gap?**
It significantly reduces your exposure. If you are running current versions of your dependencies, you have likely already received most silent fixes through normal update cycles. The risk is concentrated in teams that are running significantly outdated versions without a process to review changelogs.

**Does my security scanner vendor know about this gap?**
Most do. Some vendors supplement CVE-based scanning with changelog and commit analysis. It is worth asking your vendor whether their product monitors beyond CVE databases — and if not, whether that is on their roadmap.

**Should this change how we write acceptance criteria for security?**
Yes, at the margin. Adding "dependencies running current major version" as an explicit check alongside CVE scan results gives you a more complete signal. This is a one-line addition to your definition of done for security-sensitive releases.
