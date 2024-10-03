---
title: If you halve the amount of effort you put into producing a PR
---

(say that a simple, yet good enough proxy for that is halving the size of a PR, or halving the time taken to create a PR) but you don't halve the wait time to review it, you're losing throughput of number of changes you're able to push through the system of work in a unit of time.

The reason? As you reduce processing time, the wait to processing time ratio goes up if you're not decreasing the nominator simultaneously with the denominator.
That translates into higher cumulative wait time in the system across all PRs created, which translates into higher lead time per unit of effort invested per PR, which translates into lower throughput.

As you reduce the batch size, there's no way around not losing the throughput if the availability of reviewers and the author doesn't go up proportionally to enable lower wait times in order to at least keep the same wait to processing time ratio, i.e. not lose throughput, as you reduce the average size of the batch.

I don't know if you already heard of pair/mob/ensemble programming/software teaming as a way of working, but they help with that because the availability of reviewers and author are guaranteed by design.
