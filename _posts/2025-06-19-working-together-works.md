---
title: Dynamics between transaction cost and batch size is simple, but often counterintuitive. 
---

In short, the system compensates for the increase in transaction cost per batch size by increasing the batch size.



If an e-commerce shop charges a delivery fee, on average you won't see people ordering stuff that is less than, say, 2x the fee. Why? Because it doesn't make economic sense. People won't order, or they'll wait until they need to order more/other things and batch them together in a single shipment to compensate for the previously high delivery fee per order value.


That's also why, on average, you'll observe an increase in PR size if the review delay (transaction cost) per size of the PR, or time invested to write a PR (batch size) increases. Why? To compensate for that increase in transaction cost per batch size.


In the same way, if tests are slow and/or flaky, and/or deployment takes long per amount of invested work (time or number of changes), you'll see an increase in the number of changes deployed at once (batch size). We also know how this ends...


"Write smaller PRs!", or "Deploy smaller changes!" sounds as a sensible advice, but it doesn't work when transaction cost per batch size is high.


And when Work in Progress goes up - if people in a team are not working together (pair/mob), WIP is already too high - delays start kicking in because the team members become less responsive to each other's requests, since too many things start competing for their attention.


Those delays drive the transaction cost per batch size up, which soon gets compensated by an increase in the average size of the batch (bigger PRs and bigger deployments).


That's a balancing feedback loop kicking in to reduce back the ratio between the transaction cost and the batch size.


Instead, way better intervention is strictly protecting responsiveness of the system by keeping the WIP low, by people working together. That's why work produced by teams working together is often of higher quality.

They are able to make smaller changes, validate them sooner, thus cut the wrong paths sooner and reduce rework, which then translates into more value-added, productive time.


Working together works.
