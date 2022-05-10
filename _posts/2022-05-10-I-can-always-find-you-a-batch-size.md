---
title: For any type of async work, I can always find you a batch size
---

 small enough for which the flow efficiency is terrible.

The longer the wait time (async by design involves wait time) the higher this inflection point is and the more flow efficiency plummets as you reduce the batch size. And if the flow efficiency plummets, the throughput does as well.
As an example, this is what happens if you're doing small PRs but reviewing them asynchronously.

Want to increase the flow? Reduce the batch size, but also minimize the wait time. Preferably, by moving from async to sync work.

If you just try to reduce the batch size, at one point, high wait time per size of the batch will signal high transaction cost which will make you slide back into bigger batches and you're back to square one.

_An example_:  
Say you have a test suite that takes 20 mins to run. If you need to wait 20 minutes to get feedback about the changes you've introduced, you're not going to run the tests after every line of code that you change. It doesn't make any economic sense.
The long wait time for getting feedback from tests is incentivizing you to increase the number of changes introduced to the system before you run the test suite, i.e., you'll be running them less frequently. And you want to avoid introducing a lot of changes (big batches) before getting the feedback. Same with the PRs and code reviews.

For a given amount of wait time, there's a range of batch sizes that are economically not viable (for 20 min tests, it's changes that take, say, <= 40 min effort). The longer the wait time, the bigger the range of batch sizes that are economically not viable.

On the other side, if you have no wait time, all batch sizes become viable. And the lack of, or minimal wait time is going to incentivize and enable minimal batch size.
If it takes me 50ms to get feedback from tests, I'll be happy to run them after every LoC change (which I do).
