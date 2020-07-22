---
layout: post
title:  "Queue time has way more leverage than processing time"
---

Lead time = processing time + queue (feedback) time

Cutting batch size drives processing time down, while queue time becomes a bigger contributor to lead time.
This means that queue time becomes a bigger leverage point, compared to processing time, to reduce the lead time.
So, as you cut the batch size, shortening feedback time becomes even more important in order to increase throughput and cut lead times.

Amongst other things, that's why Pair Programming and TDD, counterintuitively, are "faster" compared to solo work and async code reviews. As a bonus, you also get to build more quality in.
