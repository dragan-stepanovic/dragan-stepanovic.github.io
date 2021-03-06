---
title: Wondering why your efforts to reduce PR size further are not going to work?
---


With every halving of the PR size, you get 2x more interruptions for each of the reviewers of a given PR.
Multiply that by the number of PRs in flight (one person, one PR) and you get the total number of interruptions in the team.  
E.g. if it's mandatory for at least one person to review a PR and if you have 4 developers in a team, total number of interruptions in the team increases 8 times (4x2). Just for one halving of the PR!


And, the more often I'm interrupted, the less I'll be willing to continue prioritizing review over my own work, which then delays the review, incentivizes batch size increase ("review is not as cheap as you thought"), which then reduces (balances) the number of interruptions.

So, interruptions are the cause of a balancing feedback loop preventing the system from reducing the batch size further.
Meaning, motivation to review is conflicted from two sides (number of interruptions vs size of the PR) which prevents further reduction of PR size by a need to trade-off between these two.

![](/assets/images/pr-balancing-feedback.png)
Note: [How to read the Causal Loop Diagram](https://en.wikipedia.org/wiki/Causal_loop_diagram)


But, interruptions exist only if reviewers are interrupted in doing something else. If they are doing nothing else, they cannot be interrupted.
![](https://i.giphy.com/media/d3mlE7uhX8KFgEmY/giphy.webp)

So, the availability of the reviewers is what makes that balancing feedback loop disappear.

Does it now make sense why pairing/mobbing is the only way to continue reducing the batch size (to a single line of code change!)?  
And that means shipping things sooner, which means accelerating the feedback, which means building in the quality (both external and internal).
