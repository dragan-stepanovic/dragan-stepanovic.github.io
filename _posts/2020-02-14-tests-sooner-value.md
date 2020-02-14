---
layout: post
title:  "Slow tests can help you deliver value sooner"
---

Test execution time can tell you a lot about design of your service. If you have a bunch of domain logic in the part of the service where it shouldn’t be (controllers, repositories, external gateways or any adapter of that sort), your tests have to spin up a mock MVC or embedded database or stub service in order to test it. The more logic you have in these parts of the app, the more tests you’ll have against them, the slower the test suite.

Once you extract this logic to domain types (where it should be), you get way more readable code because you teased out implicit code into explicit domain types, you are able to easily test that logic, you speed up test suite enormously because tests run now in memory and you’ll be incentivized to run tests more often cause the feedback loop is now way shorter. Thus, you’ll be able to use this fast feedback to discover mistakes faster and in turn this will speed up your development.

So, that’s a short story about how slow test suite can guide you to deliver value to your customers sooner.

#listentothetests