Test-Driven Development with Objects
====================================

## A Web of Objects
An object communicates bu messages: it receives messages from other objects and reacts by sending messages to other objects as well as, perhaps, returning a value or exception to the original sendes.

The behavior of the system is an **emergent property** of the composition of the objects.

## Values and Objects
When designing a system, it's important to distinguish between *values* that mode unchanging quantities or measurements, and *objects* that have an identity, might change state over time, and model *computational processes*.

Two *objects* of the same type have separate identities even if they have exactly the same stat now, because their stats can diverge if they receive differnt messsages in the future.

In practice, this means that we split our system into two "worlds":

* values, which are treated functionally
* objects, which implement the stateful behavior of the system

## Follow the Messages
We can benefit from this high-level, approach only if our objects are design to be easily pluggable. In practice, this means that they follow common *communication patterns*.

In our view, the *domain model* in in these *communication patterns* because they are what gives meanig to the univese of possible relationships between the objects.

Tests and mock objects help us see the communication between our objects more clearly.

The books makes an example of a game, and presents 2 different views of objects: one from the game engine, and one from the implementation of the in-play objects. The 2 views are not the same: one provides a static classification, the other a dynamic communication view. 

The mismatch between static classification and dynamic communication means that we're unlikely to come up with a tidy class hierarchy for the game objects that will also suit the need of the engine.

At best, a class gierarchi represents one dimension of an application, providing a echanism for sharing implementation details between objects. At worst, we've seen too many codebases that suffer complexity and duplication from using one mechanism to represent multiple concepts.

### Roles, Resposibilityes, Collaborators

We think about objects in terms of

* roles
* responsibilities
* collaborators

An object is an implementation of one or more *roles*. A role is a set of related *responsibilities* and a responsibility is an obligation to perform a task. A *collaboration* is an interaction of objects or roles (or both).

## Tell, Don't Ask (Law of Demeter)
Calling objexts should describe what it wants *in terms of the role* that its neighbor plays, and let the called object decide how to make that happen.

Objects make their decisions based only on the information they hold internally or that which came with the triggering messsage; they avoid navigating to other objects to make things happen.

Followed consistently, this style produces more flexible code because it's easy to swap object that play the same role.

When we don't follow the style, we can end up with what's known as *train wreck* code, where a series of getters is chaned together like the carriages in a train.

```java
((EditSaveCustomizer) master.getModelisable()
  .getDockablePanel())
    .getCustomizer())
      .getSaveItem().getEnabled(Boolean.FALSE.booleanValue())
```

can be reduced to:

```java
master.allowSavingOfCustomisations()
```

We've reduced the risk that a design change might cause ripples in remote parts of the codebase.

### But Sometimes Ask
```csharp
public class Train
{
    private readonly List<Carriage> _carriages [..];
    private int _percentReservedBarrier = 70;
    
    public void ReserveSeats(ReservationRequest request)
    {
        foreach(var carriage in carriages)
        {
            if(carriage.Seats.PercentReserved < _percentReservedBarrier)
            {
                request.reserveSeatsIn(carriage);
                return;
            }
        }
        request.CannotFindSeats();
    }_
}
```

We shouln't expose the internal structure of `Carriage` to implement this. Instead, we should ask the question we really want aswered, instead of asking for the information to help us figure our the answer ourselves:

```csharp
public void ReserveSeats(ReservationRequest request)
{
    foreach(var carriage in carriages)
    {
        if(carriage.HasSeatsAvailableWIthing(_percentReservedBarrier))
            request.ReserveSeatsIn(carriage);
            return;
    }
    request.CannotFindSeats();
}
```

## Unit-Testing the Collaborating Objects
We can change the way we approach TDD. We try to test the target object and we already know what its neighbors look like In practice those collaborators don't need to exist when we're writing a unit test.

We can use the tet to help us tease out the supporting roles our objects needs, defined as interfaces, and fill in real implementations as we develop the rest of the system. We call this *interface discovery*.

## Support for TDD with Mock Objects
To support this style of test-driven programming, we need to create mock instances of the neighboring objects, define expectations on how they're called and then check them.

We use the term *mockery* for the object that holds the context of a test.
