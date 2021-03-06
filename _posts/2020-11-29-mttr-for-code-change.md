---
title: How to minimize MTTR for change in the code?
---

Up until this point I was thinking that tests, as a safety net, help us to extend MTBF of the system.
Just figured out that they actually help us with MTTR. But a different kind.

TDD + refactoring in very small steps (ideally a line of code before running tests) bring MTTR from making a wrong change in the code to seconds.  

Not hours, days, or weeks as often is the case without these practices.  
And not breaking trust and damaging relationships with partners and customers in-between.  
And all the piled-up stress, pressure and rough on-call nights.  

We go fastest by minimizing the amount of backtracking.

That's one of the interplays between XP practices.
