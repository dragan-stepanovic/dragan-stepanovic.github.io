---
title: When I have a fast test suite 
---

I'm able to experiment with the production code.  

and many times I end up with this kind of monologue:
"What happens if I delete this conditional that I think I need?
Well, surprise, surprise.
It still works, I don't need it, and it's more simple now."  


When I don't have a test suite or it's not fast enough, the cost of getting the feedback is high, so I don't bother to experiment and play the "What happens if I...?" game with the code and simplify things as I go.  

You guessed it.
It leads to the compounding of bloated code that is not used and complicates the rest of the codebase.
That translates to an inability to continuously remove the waste, so I move slower and slower.
