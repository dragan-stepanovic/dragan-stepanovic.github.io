---
title: Two intervention points for fastest flow
---
You cannot have a fast feedback loop if you don't have small batches.  
But, you can have a long feedback loop even if you have small batches.  
That's the case when WIP is too high, which causes queueing in the system, which then delays the feedback.  

Also, you cannot have smaller batches if the transaction cost is high because high transaction cost incentivizes actors for batching up the work. And it will happen inevitable whether you want it or not.  
You'll need to reduce the transaction cost in order to enable smaller batches.  

So, two intervention points in the system that lead to fastest flow and *guarantee* fast feedback and building quality in are:  
1. reduce transaction cost in order to enable small batches, and
2. reduce WIP limit in order to minimize queueing
