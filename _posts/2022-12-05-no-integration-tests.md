---
title: You can force yourself to tease out domain logic 
---

by intentionally not adding integration tests.

If you feel you need integration tests out of fear of having too much logic in the parts of the codebase that connect to the outer world (I/O, web, database, etc.), the problem is not the lack of integration tests, but too much logic in the parts of the codebase that connect to the outer world.

When you tease out that complexity into the domain, you might end up with this part of the code so simple and thin that you'll feel no need to write integration tests.

Heresy, I know.
