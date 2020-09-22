---
title: What is a high transaction cost?
---

An example is of transaction cost is how long it takes us to get enough confidence that our change didn't break previous functionality.

If it takes me a long time to do this (high transaction cost) because of manual testing perhaps, that high transaction cost will incentivize actors to batch up the work (increase the batch size) that comes before testing/checking.

One way to reduce the transaction cost in this example would be to invest in automating that step.

Same thing with the deployments (automation) or PR reviews (moving to pair programming) that take a long time.

The fact that it takes a long time is communicating to the actors in the system that this step is expensive, so they are naturally incentivized towards behavior that provides them a better unit economics, which in this case means increasing the batch size
