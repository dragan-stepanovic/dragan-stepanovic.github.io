---
title: Separate refactoring tasks and PRs
---

I noticed that teams that use a process that makes reviews expensive (PRs and async code reviews are one of those) also tend to have refactoring as a separate task or a separate PR.

And when you think about it, under given circumstances it makes sense.

If review is expensive then I'll try to separate the work that adds direct value to customers and work that adds it indirectly (refactoring) in order to get the biggest bang for the buck for the effort put during the (expensive) review.

Unfortunately, this incentive also leads to accumulating cruft in the codebase since refactoring is implicitly treated as less important, which, in turn, leads to slowing down the development as you go.

Reduce the cost of code review to be able to refactor (continuously, as it's meant) and keep your codebase healthy.
