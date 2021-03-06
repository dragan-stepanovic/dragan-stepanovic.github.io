---
title: Because the cost of code review when pair/mob programming is zero
---
Because the cost of code review when pairing/mobbing is literally zero (reviewer immediately available next to a developer typing the code), it is more likely to both:  
- get the feedback in a timely manner (as you type the code) and
- get very rich feedback (which tends to be the case because it's verbal and immediate, in context)

So, low-latency, high-throughput feedback.

Those two traits are not available with Pull Requests. And that's what building quality in means, which we miss out with PRs. This bites us downstream in production and increases technical debt that most teams have a problem coping with. Not to mention damaging relationship with customers, stress in the team, affecting predictability, etc.

In general, Lean terms, reducing transaction cost (cost of code review) is what enables small batches (PR size of one line of code) that enables and accelerates timely feedback (immediate and way more code improvements).
