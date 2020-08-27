---
title: Two intervention points for fastest flow
---
I cannot have a fast feedback loop if I don't have small batches.  
But, I can have a long feedback loop even if I have small batches.  
That's the case when WIP is too high, which causes queueing in the system, which then delays the feedback.  

Also, I cannot have smaller batches if the transaction cost is high because high transaction cost incentivizes actors for batching up the work. And it will happen inevitably, whether I want it or not.  
Thus, I'll need to reduce the transaction cost in order to enable smaller batches.  

So, there are two points of intervention in the system that lead to a faster (most probably the fastest) flow and __guarantee__ fast feedback and building the quality in:  
1. reducing WIP limit in order to minimize queueing, and
2. reducing transaction cost in order to enable batch size reduction
