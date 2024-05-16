---
title: Bigger batches to save the day
---

From the “right leverage point, wrong direction” series (reference to Jay Forrester), the majority of teams I worked with when faced with high batch transaction cost relative to batch size, instead of reducing the transaction cost they increase the batch size.



It's an intuitive and economically sound approach (getting the biggest bang for a transaction cost buck), but the one that, besides delaying feedback (byproduct of increasing batch size), hides the pain the system is screaming to be addressed.



Some examples:

— conflated design, leading to having to rely on coarser grained, integration tests ⇒ run tests only after a bigger change and take longer time to figure out when something breaks

— lack of availability of a dependent team ⇒ Big, Speculative Design Upfront and premature negotiation of contract

— deployment pipeline taking long relative to the size of the change ⇒ increase size of the change deployed, increasing the risk of an outage

— work in isolation and async code reviews, signaling high cost of code review ⇒ increase size of a PR reviewed and number of LGTMs per PR



By increasing the batch size to hide the pain of high transaction cost, we miss the opportunity to improve the system where everyone experiences benefits.



When you speed up the pipeline, everyone else deploying from that point on will benefit from that.

When you improve the design to enable more focused, microtests everyone benefits from the faster test suite.

When you increase availability in the team by pairing/mobbing, everyone benefits from being able to make smaller changes being reviewed as they are being made.
