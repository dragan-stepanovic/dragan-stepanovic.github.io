---
title: High transaction cost incentivizes for big batches
---

High transaction cost incentivizes for big batches. And lack of availability, causing long waiting times, drives the transaction cost up.
I.e. the more something is rare to find, the more valuable it’s perceived as.

So, in order to enable smaller batches, look for places in the system where the transaction cost, either real or perceived, is high and try to intervene at those points by finding a way to reduce that transaction cost.


Continuous Delivery reduced transaction cost of deployments using automation.

XP reduced transaction cost of:
- code review using Pair/Mob programming
- code change using Refactoring
- code verification using TDD
- code integration using Continuous Integration.

All of these mechanisms are implementations of "keep inventory low" principle from Lean.


Often, after some point, it's not possible to further reduce the transaction cost if there's no current capability in the system to enable that.
Think, manual deployments. Simply doing (trying to) manually deploy often won't help with ["bringing the pain forward"](https://martinfowler.com/bliki/FrequencyReducesDifficulty.html). A mechanism that enables that, reducing transaction cost by automation in this case, has to be put in place.  

Another example are PRs. After some point, reducing PR size when using PR workflow stops, because the transaction cost of creating a branch, opening PR, waiting for review, etc. for a one-liner PR is going to be too expensive and it incentivizes the actors in the system to revert back to bigger PRs.
After the step of reducing the average PR size, I have to remove Github PRs capability altogether in order to enable further reduction of the transaction cost and thus move to in sync, immediate code review, i.e. Pairing/Mobbing.
