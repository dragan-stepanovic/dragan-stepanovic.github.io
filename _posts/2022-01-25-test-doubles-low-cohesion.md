---
title: Using Dummy objects in tests is a sign of low cohesion in production code
---

Over the years I came to realize that usage of some test doubles and patterns in test code can actually be an anti-pattern and indication of a deeper design problem. I know that mocks get the hate most of the time, but this time it's not about them. Partly, because I think that folks hating on mocks are actually misusing them and that mocks used as intended can help a lot with the design. (for how to used them as intended check "Mock Roles, not Objects" paper and the GOOS book).

Today: Using Dummy objects in tests is a sign of low cohesion in production code

As per @martinfowler's quote from Gerard Meszaros's "XUnit Test Patterns" book:
"Dummy objects are passed around but never actually used. Usually they are just used to fill parameter lists."
(https://martinfowler.com/bliki/TestDouble.html)

Your test tests a behavior. and if in order to invoke that behavior you have to send in a placeholder object that is not used as part of exercising that behavior, your design probably needs some love when it comes to higher cohesion.

The test is telling you that the signature of the method is asking for this object, but it's actually not used in this use case you're testing. Chances are it's used as part of testing some other use case and my guess would be that that test also sends a dummy object for the parameter that was exercised in the beforementioned test case.

I.e. one test uses a subset of method parameters and the other uses another subset of method parameters. Selectively using parameters of the method depending on the use case is an indication of a low cohesion since it indicates that there are different parts of the method that hang together more tightly, while hanging together more losely with other parts of the method, even though they are located in the same method or a chunk of the code.
E.g. if method Foo has A, B, C and D chunks of code, A and D, and B and C hold together more tightly than, say, A and B, and C and D.

Every object that is instantiated in the test needs to be used as part of the given behavior.
Test should not contain irrelevant details, but that doesn't mean it should hide them (as popularly thought). When a test invokes a behavior I expect to see all passed parameters being relevant for the test. Thus, instead of using dummy objects, redesign the code to increase the cohesiveness so that you don't have to use them.
