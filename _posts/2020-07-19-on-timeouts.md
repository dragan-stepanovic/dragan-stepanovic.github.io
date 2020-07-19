---
layout: post
title: On Timeouts in Distributed Systems
---


Here's a brain dump of thoughts I kept in my head about timeouts in distributed systems.

Longer timeouts are tying request handling threads for longer time which means that request handling thread pool is going to get exhausted faster, which at point of exhaustion causes a cascading failure starts in the upstream services.
Upstream services have a higher chance of this happening since they are, by definition, waiting longer for the response than downstream services (response time of a given serivce is proportional to the number of downstream dependencies) and thus needs to be planned accordingly in terms of capacity.
The first service that fails in the call chain is propagating failure upstream until the whole system becomes unavailable.

It also depends on the fan-in factor of a given service. Usually, the more downstream we go, the higher fan-in becomes. This indicates services that we need to be more careful about since if they become unavailable they are bringing more of a system down than the services that have lower fan-in factor.
Meaning, the service with high fan-in factor has to have more aggressive timeouts towards the downstream dependencies.

Also, timeouts help with system (service) availability, but not necessarily with the business availability.
If we have A -> B -> C service chain and B timeouts for A, then A is going to be able to accept requests, but not be able to fulfill them. Service is up, but not able to fulfill business capability. So, timeouts don't help us with business availability in this case, but can help us with being able to respond to requests that don't go down the path of B -> C, but A calls a different service in order to fulfill the given request.

Also, if there are, say, 2 downstream endpoints that a given service calls and one of those is for a use case which is, from the business value perspective, more important than the other one, then the recommended heuristic is that the timeout for the less important one should be more aggressive. That's because, the duration of the timeout for the downstream dependencies is directly proportional to the rate at which we're going to eat up the request handling thread pool in the service. We don't want less valuable functionality to eat it (faster) and jeopardize the more important functionality (more valuable downstream endpoint) of becoming unavailable.

When multiple teams are collaborating in the same service, they might not know how the downstream endpoints compare as for the business value, so it's important to have this conversation across teams collaborating in the given codebase in order to maximize the amount of residual value available to users in case of a problem in the system (which is inevitable).
The same conversation has to happen even inside a single team if that team is the only one owning a given service.

Also, long timeouts (I'd say longer than a second) can be an indication of a system design problem and should be reevaluated from that perspective before proceeding.

Maybe to provide a bit more details here, e.g. that availability of three downstream calls is A * B * C and that availability of each service by definition is <1. I.e. with every downstream service dependency added, availability by definition goes down.

Also, worth pointing out that this should be taken into consideration when designing the system.
Sometimes it's possible to avoid the need of resiliency patterns by rethinking the design of the system.
