---
title: PRs lead to cruft
---

(some call this tech debt) piling up in the codebase because latency in the async code review process signals a high cost of review which in turn hinders continuous refactoring.

The smaller the PR, the higher the cost of a code review for the same wait time.  
E.g. it's perceived as more costly when I need to wait 4 hours for a review of 20 LoC change vs when I need to wait 4 hours for a review of 200 LoC change.

Also, because the wait to processing time ratio is higher, flow efficiency and throughput go down.

Continuous (immediate) Code Reviews minimize the cost of review and thus incentivize continuous refactoring which is mandatory for keeping a codebase healthy.
They also maximize the throughput, because they minimize the wait to processing time ratio (wait time being zero) and thus maximize the flow efficiency.

You get Continuous (immediate) Code Reviews with pair and #mobprogramming and that's the reason why they keep both the throughput and the quality high.
