---
tags:
  - pattern
  - principles
  - languageOverlap
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses GRASP principle.
Status: Done
Started: 
EditDate: 2024-03-06
Relates: 
Peer Reviewed: 0
dg-publish:
---
General Responsibility Assignment Software Patterns (GRASP) is another set of design principles.

The principles here take a slightly different perspective than the principles in SOLID, although there is certainly some crossover.

GRASP tends to take a responsibility focus, like _who creates this object_, _who is in charge of how these objects talk to each other_, _who takes care of passing all messages received from a user interface?,_ etc.

Now SOLID and GRASP don’t conflict with each other, they are not competing sets, you might choose to use one or both or neither.




## Information Expert

When you assign a responsibility in form of a method, or fields, you assign it to the object that has the most information about it.

Imagine that you have a class called _customer_ and _order_.

The _customer_ tries to know all the _orders_ placed by him, a common mistake is to assign this responsibility to the _customer_ class, since the _customer_ who will trigger this method.

But, this is not the responsibility of the _customer_, the _order_ class is the one which as all the information about the _orders_.

## Creator

It tries to determine who is taking the responsibility of creating the objects.

You try to answer these question:

- Who is responsible for creating the objects?, or, how those objects are created in the first place?
- Does one object contain another (composition relationship)?
- Does one object very closely use another, or, Will one object know enough to make another object?

And if so, it would seem to make sense to nominate those objects as taking that **creator** role and making it obvious which objects are responsible for creating other objects.

> A common design pattern that applies this principle is called [Factory Pattern](http://en.wikipedia.org/wiki/Factory_(object-oriented_programming)).

## Low [[Types of coupling |Coupling]]

It means you try to reduce the dependency between your objects.

If one object needs to connect tightly to five other objects and call 20 different methods just to work, you have a _high_ coupling.

Lots of dependencies meaning lots of potential for breaking things if you make a change to any of these objects.

Now _low_ coupling does not mean no coupling. Objects do need to know about each other, but as much as possible they should do what they can with the minimum of dependencies.

## High [[Types of Cohesion |Cohesion]]

The more you have a class that has relevant and focused responsibilities, the higher cohesion you will have.

You try to make the responsibilities of your classes relevant, related as much as you can. You may need to break a class into some classes and distribute the responsibilities, instead of having a single class that does everything.

## Controller

If, for example, we have a user interface and also some business related classes.

We don’t want to have high coupling between them to actually tie them directly together, where the user interface object has to know about the business objects and the vice-versa.

It’s very common to create a controller class just for the purpose of handling the connection between the user interface and the business related objects.

It’s perfectly normal for object to exist that takes a role in a program that isn’t a real world object as long as it has a well defined responsibility.

> There is a common architectural design pattern called [Model View Controller (MVC)](http://en.wikipedia.org/wiki/Model-view-controller) which is an example of having a controller class.

## Pure Fabrication

What if there’s something that needs to exist in the application that doesn’t announce itself as an obvious class or real-world object?. What if you have behavior that doesn’t naturally fit in existing classes?

Well, rather than force that behavior into an existing class where it doesn’t belong, which means we are decreasing cohesion, we instead invent, we fabricate a new class.

That class might not have existed in our conceptual model, but it needs to exist now. And there’s nothing wrong with creating a class that represents pure functionality as long as you know why you’re doing it.

## Indirection

This is the idea that we can decrease coupling between objects.

If you have multiple objects that need to talk to each other, it’s very easy to have _high_ coupling between them, where there is a lot of dependencies.

And what we can do instead is reduce those direct connections by putting an **indirection object** between them to simplify the amount of connections that each object has to make.

[[Polymorphism]] is another design principle


## Protected Variations

How to design a system so that changes and variations have the minimum impact on what already exists.

Identify the parts of the system that are more likely to change, separate them from what stays the same, and then, encapsulate every part that vary in the system.

Most of the concepts we have been exploring are simply way of doing this, things like encapsulation and data-hiding, making your attributes private.

Interfaces are another area where we can wrap the unstable parts with an interface, and using polymorphism to create various implementations of this interface.

The Liskov substitution principle, where the child classes should always work when treated as their parent classes is another way.

The open/closed principle that we can add, but we try not to change code that works already is yet another.

