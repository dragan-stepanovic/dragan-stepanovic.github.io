---
title: Two intervention points for fastest flow
---
I cannot have a fast feedback loop if I don't have small batches.  
But, I can have a long feedback loop even if I have small batches.  
That's the case when WIP is too high, which causes queueing in the system, which then delays the feedback.  

Also, I cannot have smaller batches if the transaction cost is high because high transaction cost incentivizes actors for batching up the work. And it will happen inevitably, whether I want it or not.  
I'll need to reduce the transaction cost in order to enable smaller batches.  

So, two points where I can intervene in the system that leads to the faster (fastest?) flow and __guarantee__ fast feedback and building quality in are:  
1. reducing transaction cost in order to enable small batches, and
2. reducing WIP limit in order to minimize queueing
