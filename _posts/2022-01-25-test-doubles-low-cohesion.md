---
title: Using Dummy objects in tests is a sign of low cohesion in production code
---


Over the years I came to realize that usage of some test doubles and popular patterns in test code can actually an indication of a deeper design problem and an anti-pattern. I know that mocks get the hate most of the time, but this time it's not about them. Partly, because I think that folks hating on mocks are most probably misusing them and that mocks used as intended can help a lot with the design. (for how to used them as intended check "Mock Roles, not Objects" paper and the GOOS book).

Back to Dummy objects.

As per @martinfowler's quote from Gerard Meszaros's "XUnit Test Patterns" book:
"Dummy objects are passed around but never actually used. Usually they are just used to fill parameter lists."
(https://martinfowler.com/bliki/TestDouble.html)

Your test tests a behavior, and if in order to exercise that behavior you also have to send in a placeholder object that is not used, your design probably needs some love when it comes to (higher) cohesion.


Chances are that that parameter, you're replacing with dummy object, is when testing some other use case and my guess would be that that test also sends in a dummy object for the parameter that was exercised in the former test case. Meaning, one test uses a subset of method parameters and the other uses another subset of method parameters.

Selectively using parameters of the method depending on the use case is an indication of a low cohesion since it indicates that there are different parts of the method that hang together more tightly, while hanging together more losely with other parts of the method, even though they are located in the same method or a chunk of the code.
E.g. if a method Foo has A, B, C and D chunks of code, A and D, and B and C hold together more tightly than, say, A and B, and C and D.

Every object that is instantiated in the test needs to be used as part of the given behavior.
Test should not contain irrelevant details, but that doesn't mean it should hide them (as popularly thought).
Having irrelevant details in the tests is less a problem for the test and more of a problem for the design of the production code.
When a test invokes a behavior, I expect to see all passed parameters being relevant for the test. Thus, instead of using dummy objects, redesign the code (probably split the method) to increase the cohesiveness so that you don't have to use them.
