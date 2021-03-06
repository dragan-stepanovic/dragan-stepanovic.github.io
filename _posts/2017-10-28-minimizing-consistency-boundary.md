---
layout: post
title:  "Minimizing Consistency Boundary with Event Sourcing"
---

Imagine you have a system for managing customer subscriptions of your SaaS product. Your customer can be a company and can have multiple licenses he can use with the subscription he payed for. Customer also wants to be able to assign and unassign those licenses to his employees. Also, customer wants to be able to see how many unused licenses are available for a given subscription and how many licenses in total are used (across different subscriptions that he has payed for).

Given these requirements, let’s say that a business rule we have in our system is that when a customer assigns a license for an employee:

- new license is stored to the database
- number of unused licenses for a given subscription is decreased
- total number of used licenses for all subscriptions of that customer is increased

Complementary, when a customer unassigns a license from an employee:

- given license is deleted from the database
- number of unused licenses for a given subscription is increased
- total number of used licenses for all subscriptions of that customer is decreased

#### Storing only current system state (i.e. using database)
Looking at the business rules we have in place, all three operations for assigning and unassigning licenses need to be executed in a single transaction. If any of them fail, consistency boundary is broken. Thus, consistency boundary consists of all three operations.

When unassigning the license, it can happen that we delete the license from database, but bug in the code prevents us from increasing number of available licenses for a subscription and decreasing total number of used licenses for a given customer. Can we recalculate the two numbers again later given the license has already been deleted from the database? I’m not sure we can (at least not easily). This can leave us in an inconsistent state. In production. For hundreds of customers. Where we cannot easily trace back what state we were in before the bug has happened and thus not know what operations to revert in order to get back to the previous consistent state or what operations to apply to get to the next consistent state.

One of the ways to address this is by decreasing a probability of having a bug in code that caused this. Yeah, right 🙂  
On the other hand, perhaps we can ask ourselves if that way we’d be solving the wrong problem actually. Perhaps we shouldn’t be having all three operations in transaction in the first place. Perhaps, we could somehow decrease the consistency boundary.

#### Using Event Sourcing
What if we use event sourcing? Meaning, when assigning/unassigning a license we only record that that event happened instead of inserting/deleting the records in the database and updating related counter fields. In that case, consistency boundary would only encompass storing license assigned/unassigned event that has happened. Calculating two counters would be a matter of projection over a set of events for a given moment in time. E.g. asking what is a number of unused licenses is a projection over a set of all the license assigned and unassigned events that have happened for a given customer and given subscription up until now. In a similar way we’d be able to calculate total number of used licenses by a given customer.  
License assignment/unassignment event is the single source of truth. Every other information can be derived from this.

> Moment that we calculate information derived from the original event should not be coupled to the moment we record original event.

When storing only current state of the system, you have no option but to save the information that is derived from the original event at the moment when the original event happens. You must save it at the given moment because you have no history of changes and thus no ability to recalculate it afterwards based on the state you find in the database. This extends consistency boundary, meaning more operations in the transaction.

If anything about calculating number of unused licenses goes wrong because of the bug in the code, we can easily try the projection over the same set of recorded assigned/unassigned events again when we fix the bug. No need to intervene in order to get the data back in the consistent state.

#### Other side benefits of ES
Besides increasing the consistency boundary, former approach with storing only current system state and always precalculating counter fields can be a performance hit (imagine if this is some CPU heavy operation). What if it turns out that a given customer rarely goes to the part of portal where they can see this precalculated information (e.g. customer’s total number of assigned licenses)? Event sourcing also enables us to delay the calculation until the last responsible moment, meaning just when the user asks for it and thus save CPU cycles. We can even go further and record the events when and how often projections/calculations are triggered and thus observe how often do customers actually use this part of system. Low activity can indicate that there’s no value in keeping that functionality of the system at all. Less code, less problems.

In case you’re worried about the load hit that you’d face when lots of customers use this functionality, event sourcing presents recorded immutable series of events and thus plays very nicely with functional paradigm. This means that projections are pure functions without side effects and can be easily scaled out if needed. There’s also a possibility to use CQRS and separate read store containing two mentioned counters that would be updated on the license assign/unassign event. You could say that this boils down to the same thing as with the first approach, but the thing is that this is actually caching for performance reasons and also you can always recalculate these counters which is not the case when storing only the current state of the system.

Also, when using event sourcing, the amount of data that needs to be stored can be smaller than when storing only current state of the system. As we’ve seen in the given example, we only need to store the event that assign/unassign has happened, while two related counters are calculated when needed and don’t need to be stored. When you scale this to fairly large number of use cases this can make a difference. Surely, when you record series of events, rather than only current state, you’ll be using more data, but I wonder if not needing to store derived information actually zeroes out the differences in terms of data usage in these two approaches.

#### And some trade offs
On the other hand, using event sourcing usually needs more complex projection since you need to go through the whole history of events (though you can shortcut this with snapshots). When storing only current system state you are forced to calculated derived information and at this moment it’s usually fairly simple to do this. Using above mentioned example, asking what is a number of unused licenses for two approaches respectively:

- is a projection over a set of all the license assigned and unassigned events that have happened for a given customer and given subscription up until now, versus
- simply increasing number of used licenses by one

So, there’s a trade off between _consistency boundary scope and complexity of derived value calculation._

##### Summary
Storing only current state of the system increases the consistency boundary of the system and can cause more problems and inconsistent state in case of the failure of the system. It can also place upfront performance hit and also speculates that the derived, calculated information is going to be needed (at all).
Event sourcing decreases consistency boundary, enables projection/calculation of related information just when it is needed and keeps the application state consistent, while somewhat increasing complexity of derived values calculations.
