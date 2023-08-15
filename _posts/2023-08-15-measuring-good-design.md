---
title: On measuring good design
---

It's close to impossible to measure good, testable design, but over the years two interesting metrics settled in my mind that are a fairly good indication of the presence of clear, explicit code that speaks the domain:

1) 85th percentile of LoC per method (should be low ⬇️)

2) 85th percentile of public-to-private methods ratio per class (should be high ⬆️)

The first one is clear, but the second one is interesting.

The lower this ratio, the more private compared to public methods we have in a class. I also call these classes iceberg classes because the public interface is very narrow, and often these classes are the ones for which we feel the urge to test private methods.

Low public-to-private methods ratio indicates the presence of implicit domain concepts that were not communicated in the code. Once we do that, by extracting collaborators and moving private behavior there and as a side effect making it public, this ratio goes up.

The first metric (LoC per method) is there to guard the 2nd one because for God classes with a single or few, huge methods, this ratio is low, but obviously, the code is far from having a good testable design.

Note: these metrics are not one to rule them all. I see them as good starting indicators and conversation starters.
