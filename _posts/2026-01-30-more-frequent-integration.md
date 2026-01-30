---
title: More code per unit of time? More frequent integration
---
Practice of Continuous Integration traditionally meant integrating code to main at least once per day.

If you’re generating an order-of-magnitude more code with AI than before, then that definition is not accurate anymore - partly because it was focused on the cadence instead of inventory (of unintegrated code), which I think is much more aligned with CI’s actual goal - flow.

So, depending on how much more code you’re generating per day, you need to integrate to main proportionally more often in order to be doing Continuous Integration.

Otherwise, there’s going to be a lot more pain coming from merge conflicts of bigger batches of code landing on the main, increasing rework rate, rendering any upstream “AI acceleration” useless. It doesn’t matter how much more code and in parallel you’re able to generate. All of that needs to land in the same codebase and a single, main branch.

A good visual metaphor: inflating the elephant that is travelling through the boa constrictor. The bad news is that the change lead time goes up as you start doing that.

Also note that this reasoning applies to all downstream stages from integration (deployment, release, customer adoption, customer acceptance of value, etc.).

<img width="1200" height="576" alt="image" src="https://github.com/user-attachments/assets/c7a25279-f0b8-440f-a59f-62294a2f31ec" />
