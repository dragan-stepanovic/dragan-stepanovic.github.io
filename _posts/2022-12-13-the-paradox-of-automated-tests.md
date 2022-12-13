---
title: The paradox of automated tests as a safety net: as the testability of a codebase goes up, the ROI for test automation goes down?!
---

Automated tests as a safety net are most valuable in codebases with high risk when making a change. Those are conflated, coupled codebases where:
1) the average rate of change per element (method/class) is high and
2) the risk of introducing problems with a change is high (too much coupling).
The latter is a consequence of the former, and codebases with long methods and classes inherently exhibit these characteristics.

But then, even though in these codebases the ROI for automation as a safety net is high, it's very difficult to introduce tests because the code was not designed with testability in mind.

On the flip side, in codebases that are clear, explicit, and speak the domain language, as a byproduct of making it that way we get tiny methods that are very easy to test and also have a very low rate of change per method. As methods and classes get smaller, they have fewer reasons to change.

>With every change we need to make, we need to change fewer methods as a % of the total number of methods (more seams in code), and thus we also reduce the average rate of change per method.



When you have 100 tiny methods, and you need to change something, the number of methods you need to change as % of the total number of methods is most often way lower than when you have fewer, longer methods.

That's the economic argument behind investing in good design because we reduce the risk of change by reducing the average rate of change per element.

But! As the rate of change per element goes down, the risk also goes down, thus the value you get out of automating tests as a safety net goes down as well, so it's less easy to justify the upfront investment.

There are two additional, important points here:
1) If you have a piece of code that is inherently harder to test – anything that interacts with the outer world, e.g., database, console, files, external API calls, queues, etc. – instead of automating tests you can leverage the design to reduce the rate of change of these parts of codebase in order to reduce the risk, perhaps to a point where it doesn't make economic sense to automate the tests.

2) Reducing the risk of change by lowering the rate of change per element of code is driving down the amount of rework in the teams with good, heavily factored design and thus making them more productive
