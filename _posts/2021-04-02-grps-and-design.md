---
title: If you need gRPC to optimize the performance of communication over the network
---
functional decomposition of the system is suboptimal which is causing services to be overly chatty.  

Not to mention that most of the complexity (especially operational) is then moved from the services to the network.  

I.e. if REST (over HTTP) is not fast enough for you, take a look at the design of your system again.
