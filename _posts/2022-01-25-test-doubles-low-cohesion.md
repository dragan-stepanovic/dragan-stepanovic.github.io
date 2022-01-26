---
title: Using Dummy objects in tests is a sign of low cohesion in production code
---

Over the years, I came to realize that usage of some test doubles and popular patterns in test code can actually be an indication of a deeper design problem in production code.

I know that mocks get most of the hate, but this time it's not about them. Partly, because I think that folks hating on mocks are most probably misusing them, and that mocks used as intended can actually help a lot with the design.
(for how to use them as intended, check the GOOS book and "Mock Roles, not Objects" paper by 
@natpryce, @sf105, et al.).

Anyway, back to Dummy objects.


As per @martinfowler's quote from "XUnit Test Patterns" book by Gerard Meszaros:
"Dummy objects are passed around but never actually used. Usually, they are just used to fill parameter lists."
(https://martinfowler.com/bliki/TestDouble.html)

Your test tests a behavior, and if in order to exercise that behavior you also have to send in a placeholder object that is not used, your design probably needs some love when it comes to (higher) cohesion.

Also, chances are that the parameter, you're replacing with a dummy object in a given test case, is exercised when testing some other use case and my guess would be that that test also sends in a dummy object for the parameter that was exercised in the former test case.
Meaning, one test uses a subset of method parameters and the other test uses another subset of method parameters.

Selectively using parameters of the method depending on the use case is an indication of a low cohesion since it indicates that there are different parts of the method that hang together more tightly, while hanging together more loosely with other parts of the method, even though they are located in the same method or a chunk of the code.

E.g. if a method Foo has A, B, C, and D chunks of code, A and D, and B and C hold together more tightly than, say, A and B, and C and D.
Every object that is instantiated in the test should be used as part of testing given behavior.

A test should not contain irrelevant details, but that doesn't mean it should hide them (as popularly thought). Having irrelevant details in the tests is less of a problem for the test and more of a problem for the design of the production code.

When a test invokes a behavior, I expect to see all passed parameters being relevant for the test. Thus, instead of using dummy objects, redesign the code (probably split the method) to increase the cohesiveness so that you don't have to use them at all.

And yes, this is another example of how 'Listening to the tests' can aid your design.
