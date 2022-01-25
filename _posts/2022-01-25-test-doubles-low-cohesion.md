---
title: Using Dummy objects in tests is a sign of low cohesion in production code
---

Over the years I came to realize that usage of some test doubles and patterns in test code can actually be an anti-pattern and indication of a deeper design problem. I know that mocks get the hate most of the time, but this time it's not about them. Partly, because I think that folks hating on mocks are actually misusing them and that mocks used as intended can help a lot with the design. (for how to used them as intended check "Mock Roles, not Objects" paper and the GOOS book).

Today: Using Dummy objects in tests is a sign of low cohesion in production code

As per @martinfowler's quote from Gerard Meszaros's "XUnit Test Patterns" book:
"Dummy objects are passed around but never actually used. Usually they are just used to fill parameter lists."
(https://martinfowler.com/bliki/TestDouble.html)

The reason why using dummy objects can be an indication of a deeper design problem is that if your test tests a behavior and in order to invoke that behavior you have to send in a placeholder object, your design probably needs some love when it comes to higher cohesion.

What your test is telling you is, the signature of this method is asking for this object but it's actually not used in this use case and the behavior you're testing. Chances are it's used in some other use case and my guess would be that that test sends a dummy object for the parameter that was used in the other test case. One test uses a subset of method parameters and the other uses the other subset of method parameters. Selectively using parameters of the method depending on the use case is an indication of a low cohesion and indicates that there are different parts of the method that hang together tightly with some of other part of the method, while hanging together losely with other parts of the method, even though they are located in the same method or a chunk of the code.

Every object that is instantiated in the test needs to be used as part of the given behavior.
Test should not contain irrelevant details, but that doesn't mean it should hide them as popularly thought. When a test invokes a behavior I expect to see all passed parameters being relevant for the test. Thus, instead of using dummy objects, redesign the code to increase the cohesiveness so that you don't have to use them.
