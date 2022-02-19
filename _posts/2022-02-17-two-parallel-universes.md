---
title: Two parallel universes
---

When it comes to PRs and code reviews, if you are optimizing for these metrics in order to improved the process (and I believe you should)


![](/assets/images/metrics.png) 


then this here

![](/assets/images/results.png) 

is the difference (on a natural log scale!) between the worlds of async code reviews and pairing/mobbing.


Presented, is a 500 PRs, sample data set from a typical product development teams using async code reviews and PRs. I did this analysis across tens of thousands of PRs and the results are pretty much the same.

The best result for async code review I was able to see was 6 (again, on a natural log scale), compared to 0 (zero) that is produced by pairing/mobbing.  
Note: The smaller the score, the better

PR score calculation reflecting the metrics we want to optimize for and in which direction:

![](/assets/images/pr_score.png) 


A bit more on the metrics and the reasoning behind them:

**1. PR size (LoC changed)**

Smaller PRs are something we'd want to have more of, and I believe there's no need to argue about that (if yes, please check the benefits of small batches in Lean). 

Note: some PRs may have many LoC changed, but are quick to produce (e.g. an update of an external library producing a PR with lots of LoC changed); these are outliers that were not included.

**2. Engagement per size**

Number of non-trivial comments (i.e. comments that are not 'LGTM', '+1', 👍, etc.), per size.
If you get little or no feedback for your work, then delayed code reviews don't make much sense, since they both choke the flow and don't build the quality in. We'd want this metric to not go down.

**3. Wait time per size**

Time PR spends sitting in the queue (not being worked on, waiting for author's or reviewers' attention), per size.

Waiting, say, 2 days for a review for a PR that took 5 days to develop (wait to processing time ratio of 0.4) is not the same as waiting 2 days for a review for a PR that took 10 minutes to develop (wait to processing time ratio of 288). ~720 times higher.
The higher the wait time per size, the higher the perceived cost of review and also the lower flow efficiency and throughput.
Also, the higher this cost is, the more it incentivizes authors to batch the changes in a single PR before asking for a review in order to make economic sense of the review process.
That's also the reason why small changes and refactorings are inhibited by a process that has a high cost of code review per size.

Note: Processing time doesn't necessarily scale linearly with the PR size, but the PR size as a proxy for the effort was a good enough approximation to get a sense of the perceived cost of code review per unit of the batch.



Now, as for results for **pair/mob programming**.

![](/assets/images/pr_score_new.png)  

If someone is sitting next to you and is available to give you feedback immediately, the wait time per size is effectively 0 and PR size is effectively as low as 1 LoC since immediate feedback available after every LoC changed; heck, it's even availabile after every letter typed.

The engagement per size is almost always higher than with async code reviews.

I suspect most probably because the feedback is more timely (immediate) and provided through a medium that has lower latency and higher throughput (verbal feedback) compared to the higher latency and lower throughput one (delayed feedback and provided in a written form).

What this means is that the transaction cost of providing feedback in pair/mob is minimal which incentivizes actors (author and reviewers) to provide it as often and as much as they'd like to, which also means it enables the reduction of optimal batch size all the way to the left (as per batch size U-curve optimization).

![](/assets/images/u_curve.gif) 

(Credits to https://lastcallmedia.com/blog/why-devops-most-important-tech-strategy-today)

_Disclaimer_: I'm not saying pairing/mobbing are better across all imaginable dimensions, but I'm saying that if you want to optimize for both throughput and quality, then the difference is huge and pair/mob is the way to go. I invite you to try it and experiment.

If you do it properly (good facilitation needed) and learn the skills of co-creation and working together with others, I believe you'll both very much like it and also be more productive as a team.

There are lots of other benefits of co-creation, but that's a separate topic you can check out [in this podcast I did](https://youtube.com/watch?v=NJWeM7beAGE).


Have fun working together as a team!
