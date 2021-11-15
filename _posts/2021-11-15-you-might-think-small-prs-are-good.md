---
title: You might think that small PRs are good
---

because you see more feedback and quality being built in than on big PRs ('LGTM + Approve syndrome').

But if you're reviewing them in an async manner, more conversation on the smaller PRs means more back and forths per LoC, meaning higher cumulative latency per LoC compared to bigger PRs.

In fact, the smaller the PR, the more latency in the communication starts dominating PR's lead time, meaning more waste in the system and lower flow efficiency and throughput.

Here's an advice: if PRs for review are accumulating, the intervention point is not to constantly urge people to prioritize reviewing other people's PRs over those they work on, but to focus on minimizing the latency in the review process.

If you're working in an async manner, you won't be able to bring it all the way down to zero, but hopefully, that will make you realize that in fact, you shouldn't be working in an async manner and instead move to face to face conversations and co-creation (pair/mob).

You'll unlock another level of process improvement that wasn't available before.

Also, higher levels of psychological safety and trust in your team can thank me later.
