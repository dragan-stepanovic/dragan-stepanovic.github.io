---
title: The slower the test suite, the more we'll be retracing
---
The slower the test suite, the less often we'll run it, the more we'll backtrack whenever we make a wrong turn in the code, the slower we'll go at the end.

We need a good (i.e. testable) design to enable a fast test suite, so we can go faster by being able to minimize retracing.  
Most of the confidence and feedback should be coming from the in-memory very fast tests suite. If you're not able to achieve that, most probably there's an underlying problem with the design that at the end is slowing you down by having to backtrack too much when making a mistake.

That's another interplay between XP practices.
