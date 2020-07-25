---
layout: post
title: Event Sourcing and cheap storage space as enablers of ever higher scalability
disqus: true
---


Maybe late to the party, but just realized an interesting interplay between Event Sourcing and ever cheaper storage space.



Immutability of events in Event Sourcing enables infinite cacheability on the clients, and since price per unit of storage is getting cheaper and cheaper, it heavily reduced the need for horizontal scaling on the server side (event store), since all the data can be closer to the clients without ever needing to "go back to the server" for the things that happened in the past.



Horizontal scalability was (one) solution for the problem with slow rate of progress in vertical scalability and Event Sourcing with cheap storage helps solving the need for horizontal scalability by distributing processing closer to the clients.



Effectively, it solved the problem of slow rate of CPU and network performance increase in the hardware industry by moving it into a storage space, and this curve is way ahead of the former one.
