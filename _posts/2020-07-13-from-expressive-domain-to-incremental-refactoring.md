---
layout: post
title: "Expressive domain as incremental refactoring enabler"
---

Being expressive about the domain doesn't only improve readability, but also reduces coupling, which in turn enables incremental refactoring.

So, expressive domain -> reduces coupling -> enables incremental refactoring.



To quote Brian Marick: "An example would be handy right about now".

A snippet from Game of Life kata:
![](/assets/images/expressive_domain_2.jpg)

3 methods have the same body, but that single line of code is used to communicate 3 different outcomes and meaning in a given (client) context.



As a bonus effect of being explicit about that, it enabled independent changeability of the methods and thus ability to refactor in a small steps.

And believe it or not I did have a need to change them independently while refactoring (from static to non-static).

