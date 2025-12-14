---
title: Heavy AI machinery and design
---
When coding, I find AI especially valuable when trying to achieve consistency across the codebase once I have a directional change in design. The “look at this example of how I did it and apply it to all other cases in the codebase”, where AI does all the heavy lifting, drastically cuts the time to implement a change.

But, then, when I do a bit deeper dive into the design, I often find that I was actually too late with addressing the signal design was trying to tell me, but I didn’t listen to.
E.g. already too high fan-in factor to a method/class - it’s used in too many places and there was a missing domain concept that should’ve sat in between to reduce it. Had I had it, I wouldn’t have needed the heavy-lifting because the change would’ve been more contained than it was.

So, my guiding question currently is: “Any time you recognize big value of AI doing some heavy-lifting work for you, ask yourself, is there something about the design that you should’ve addressed earlier before it got cemented such that you needed heavy machinery to address it?”

Reducing the cost of this kind of heavy lifting makes it less likely that the design will be addressed in a timely manner. And that’s something I’m trying to be aware about as much as I can.
