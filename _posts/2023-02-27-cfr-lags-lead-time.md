---
title: Change failure rate is a lagging indicator of lead time to change
---
If you halve the change size, your deployment frequency goes up twice, and now in order to keep the same change failure rate % as before you have to have twice as many failures per change.

As you keep halving the change size, it gets increasingly more difficult to keep the same change failure rate % as before, which is of course good news.

Your MTTR also goes down because troubleshooting smaller changes gets increasingly easier.

Did I just say that micro-commits with instant code review, good design that enables fast tests, and a safety net generated as a byproduct of TDD will help you with all your DORA metrics? Seems that I did 🤷‍♂️

Welcome to XP.
