---
layout: post
title:  Measuring flow efficiency in software development
---


high throughput -> make sure that you have high flow efficiency and small batch size

queuing time -> proxy for busyness -> proxy for high WIP

batch size

smaller batch size can uncover low flow efficiency because processing time goes down, queue time will dominate
big batch -> processing time longer, queue time contributess less to cycle time and thus the flow efficiency is misleadingly high


With high WIP, queing time goes up, so average PR age goes up, and thus can be used as a proxy for high WIP
But it can also be used as a proxy for batch size, since with larger batches feedback time goes up (reviewers have to reviewer bigger PR), and risk of more back-and-forths between the reviewers and author goes up as well.

Average number of PRs divided by team size is a leading indicator of high WIP. This will also drive the queue time up and thus affect the average PR age as well.
[It can be rolling average (e.g. every week)]

More frequent commits give you better accuracy, but even without that it's good enough to tell you about the batch size.




For measuring WIP (1)
1) Average number of open PRs divided by team size (time unit would be per day)
2) Average age of PR (from raising PR to merging it)


And for slicing ability (2)
1) Average time from first commit in PR till raising the PR (effectively until ready for review)
2) Average size of the PR (in Lines of Code)


with pairing and mobbing, flow efficiency is maximized (in case you don't have some external blockers, which cross-functional team should minimize).
For slicing ability you can cap the cycle time to extract most of the value from the work you're doing.
same with code coverage. you don't even have to measure

XP practices + caping cycle time gives you guaranteed flow efficiency and small batch size, which leads to maximizing throughput of the value of the whole team.

- Percentile treba da se gleda, ne average
- percentage of PRs merged with 0 or 1 comments

piši o slicing-u, da treba da se vratimo na problem da bi skontali kako da slice-ujemo solution space. a ovo sve kako bi maksimizovali throughput of value


================

When you figure out that it would be faster to increase the batch size, think about how to reduce the transaction cost in order to enable smaller batches
