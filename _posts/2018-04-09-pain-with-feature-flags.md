---
layout: post
title:  "Pain with Feature Flags as a feedback tool"
---


In case you’re doing [Trunk Based Development](https://trunkbaseddevelopment.com/) ([and you should be doing it](https://twitter.com/armakunihq/status/976142586388926464)) you already know or have heard that [Feature Flags](https://martinfowler.com/bliki/FeatureToggle.html) are a form of technical debt. In fact, some teams have so many difficulties with this introduced technical debt that they “lose trust” in Trunk Based Development and fallback to Feature Branching. The important thing here to realize is that this is actually a decisive point in the development.

> Our design communicates to us through resistance

Some valuable questions worth asking here would be: “Is technical debt inherent problem of Feature Flags or is that pain actually some form of a feedback? Particularly, a feedback about our design and our development process?”

My guess is that at least three things about feature flags (FF) play a significant feedback role here:

- number of occurrences of each feature flag across the codebase
- number of distinct feature flags in the codebase
- feature flag open time

#### Number of feature flag occurrences as a design feedback
Usually, when people complain about technical debt when doing Trunk Based Development using feature Flags, they mean the scenario with maintainability difficulties caused by feature flags (i.e. if-elses and switch-cases) being scattered all around the codebase. In this case there are a couple of important questions.

> What does the fact that, in order to introduce new behavior we have to change the existing code in bunch of places, tell us about our current design?

What does this pain tell us about adhering to the Open Closed Principle? Perhaps this is a feedback about the fact that it’s about time to refactor our code so that we could easily slide in new feature hidden behind the feature flag.

Let’s be clear, our code cannot be prepared for every possible future change, but the most important thing is to recognize the point in time when the feedback surfaces and leverage that useful info to address the root cause. In this case by refactoring and molding the design in order to accommodate new change easily rather than, by inertia, shoveling in bunch of conditional code and increasing the technical debt.

In case of a good design (perhaps SOLID adherent one that is [append only](http://blog.ploeh.dk/2012/01/03/SOLIDisAppend-only/)) I’d say that a given feature flag should be, ideally, present in a single place in code. In case you’re doing Dependency Injection, that would be a place where you compose your application, meaning composition root. There we’d have a single conditional, for a given feature flag, for choosing old or new implementation. No if-else proliferation of the feature flags throughout the codebase. No pollution of domain code with feature flags infrastructure.

#### Number of distinct feature flags as a cycle time feedback
Second feedback that we could get use of from feature flags is the number of distinct open feature flags in the codebase. Note: By open, I mean feature flags that are not yet released (meaning deployed but not yet toggled on). Lots of open feature flags add to the overall technical debt in the codebase.

What could the fact that we have so many distinct open feature flags in a given moment mean? What does that tell us about the number of things we’re trying to tackle at a given moment? Are we trying to do too much at the same time? As per [Little’s law](https://en.wikipedia.org/wiki/Little%27s_law), limiting work in progress (WIP) helps in [decreasing cycle time](https://www.youtube.com/watch?v=W92wG-HW8gg). Thus, limiting number of features we’re working on in a given time can be very beneficial for the team in order to delivery feature faster and get faster feedback about the value that it’s trying to add to the user. At the same time this approach decreases technical debt by not having many feature flags open and lots of conditionality scattered across the codebase.

#### Feature flag open time as a work size feedback
One more factor that contributes to the “feature flags are technical debt” story are feature flags that are open for a long time. This means that we have conditionality for a long time in the codebase, thus contributing to the overall technical debt. What does this long feature flag open time represent?

>Long lived branches with Feature Branching are bad, but long lived open Feature Flags with Trunk Based Development are not that better

Perhaps, feature flag open time can tell us about the size of the work for a given feature? Are we trying to tackle too much? Can we split the feature into multiple vertical slices of functionality that could be delivered faster to the user so that we could get faster feedback? Guess what, additional bonus is that they don’t get to be in the code base for a long time, thus not contributing to the “feature flags are a technical debt” story.

##### Summary:

Feature flags don’t have to be technical debt. If they are, then we might at least ask ourselves the question: “Is that pain some kind of feedback that we could leverage to improve our design and development process, rather than solving the wrong problem?” Or to put it bluntly, if feature flags are technical debt then you’ve got some more important problems to solve.
