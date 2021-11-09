---
title: One thing about being specific
---

in the design of methods and messages is that it hugely reduces coupling and enables faster current and future changes.

Example:
Your service might receive 'CustomerAddressUpdated' message, but what you're really interested in is when the customer moved (and thus the address changed).
Maybe the customer's address was updated because they mistyped their address and now they corrected it.

What you now have to figure out is what really happened in the system. Did the customer move, mistyped their address, or something else? You have to dig into that generic and most likely very fat 'CustomerAddressUpdated' event and try to figure it out based on the event data (implicit stuff).
So you have to have logic on top of the implicit event to figure out what happened. And not only your service, but other consumers that are interested in the same event (duplication).
Plus, consumers that are interested in 'MistypedAddressCorrected' event have to figure it out as well on their own based on the same low-level 'CustomerAddressUpdated' event.

Now, you have a bunch of different consumers being interested in, in fact, different domain events but being coupled to the same low-level event, which also makes it hard to change it because multiple teams may be involved in the change.

The vaguer you are in your design, the more parties will _need_ to be coupled to it, but only in order to figure out specific thing they need to figure out. The more specific you are, the fewer parties will be coupled to it (the fan-in factor goes down) and you'll be able to make the change easier.

There are lots of other reasons why being explicit and specific in your design is important, but this one is the one I keep encountering.
