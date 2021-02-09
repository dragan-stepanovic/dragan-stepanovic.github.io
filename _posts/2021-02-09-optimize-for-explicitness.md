---
title: Optimize your code for explicitness
---


Two super simple examples, achieving the same thing.

![]()

The first example has fewer lines of code compared to the second. But the amount of domain knowledge that we made implicit (and thus lost since we failed to communicate it) when optimizing for that metric is disproportional.

In the second case we get to understand that:
1) "some.sender@gmail.com" is a sender
2) that the receiver is the same as the sender (we send the email to ourselves), and
3) we get to understand the `sendmail` method call better since we don't have to jump into the method body to understand which parameter is which
4) this also helps us when changing the code on this client's side and reduce chances for swapping the parameter unintentionally

My advice: prefer optimizing for explicitness and readability.

There's a pandora box full of great opportunities that lead you from that point. Opportunities for testability, better design, readability, and domain insights.

Note: If we're in fact sending an email to ourselves, I'd go ahead and extract this method into `send_email_to_ourselves` and just pass a single email address.
But this design decision became way more obvious because I made the previous intentions explicit in the first place.
