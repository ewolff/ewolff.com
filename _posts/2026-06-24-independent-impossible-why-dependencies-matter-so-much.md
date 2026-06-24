---
title: "Independent? Impossible! Why Dependencies Matter So Much"
layout: blog
description: Software architecture is about managing dependencies, and independence is the goal — or so it seems. In reality, however, it is not even entirely clear what dependencies actually are.
tags:
- Fundamentals
---

# Independent? Impossible! Why Dependencies Matter So Much

Dependencies are so important in architecture because they make it
difficult to predict the impact of changes. If everything depends on
everything else, a change can have unforeseen consequences,
potentially affecting entirely different parts of the
system.

Therefore, the goal of dependency management is [loose
coupling](/2025/09/15/loose-coupling.html): a change should have as
little impact as possible on other parts of the system. This applies
at every level. Changes to classes should ideally have minimal impact
on other classes, changes to methods should have minimal impact on
other methods, and the same principle applies to coarse-grained
structures such as packages (collection of classes in Java) or
microservices.

## Independence?

Many people see the goal of good architecture not as loose coupling
but as complete independence of individual elements. However, that is
impossible. The individual elements form a whole: methods form
classes, classes form packages, packages form microservices, and
microservices ultimately form systems. Components are
connected. Therefore, the objective can only be to ensure that changes
have as little impact as possible — but there will always be changes
that ripple through to other components. Every change has a kind of
**blast radius**, an area affected by that change, and that radius
should be kept as small as possible. This is where dependencies come
into play.

Every change has **blast radius**, an area affected by that
change. that radius should be kept as small as possible.
{: .callout }

Dependencies can take different forms. In object-oriented systems, for
example, there is the *uses* relationship: one class uses another
class. It holds a reference to instances of that class. In this case,
the class's interface is known, meaning only methods marked as
`public` can be used. There is also the inheritance
relationship. Here, a more specialized class is derived and can access
`protected` methods or variables as well. Inheritance therefore
creates a stronger dependency because more of the class can be used,
increasing the number of aspects that may be affected by changes.

This is often described using the concepts of **black boxes** and
**white boxes**. With a black box, only externally visible elements
can be accessed — for example, the interface formed by public
methods. A white box should more accurately be called a *transparent
box*, because it also allows access to internal structures, such as
protected methods. Compared to a black box, a white box exposes a
larger set of potentially usable methods, making the dependency
stronger. Thus, an inheritance relationship typically leads to
a stronger dependency than a uses relationship.

## Confusing Dependencies

Once you dig a little deeper, the topic of dependencies quickly
becomes confusing, as several examples demonstrate: There is an
interesting
[paper](https://www.pathsensitive.com/2022/09/bet-you-cant-solve-these-9-dependency.html)
by Jimmy Koppel and a German [stream /
podcast](https://software-architektur.tv/2023/09/01/folge179.html)
that discusses it.

Suppose we build an application that uses Google Analytics. At first
glance, the application is obviously dependent on Google
Analytics. Yet in a certain sense, it is also independent of it. After
all, the application can be built — and more importantly deployed —
without Google Analytics. It merely sends messages over the network to
Google Analytics. Independent build and deployment would not be
possible if Google Analytics were not an Internet service but instead
a part of the application itself, such as a library. Libraries are
required both when building and deploying the application.

However, the application is dependent on Google Analytics in another
sense. It must send messages that Google Analytics understands — and
only Google Analytics understands them. Yet this dependency can be
reduced by introducing an abstraction layer, making it possible to use
a different analytics service.

Would the application then be independent of Google Analytics? Not
entirely. If Google Analytics fails, the application is affected
because it can no longer report metrics. In the case of an analytics
service, this probably would not cause the application itself to fail,
but with other services it might. Conversely, if Google Analytics is
improved, the application benefits. It might become faster if requests
to Google Analytics become faster, or it might provide users with
richer analytics if Google Analytics gains new capabilities.

## Dependent or Independent?

So is the application dependent on Google Analytics or not?

The fundamental problem is that the term **dependency** is not precise
enough. Jimmy Koppel proposes to distinguish three categories of
dependency:

The fundamental problem is that the term dependency is not precise
enough.
{: .callout }

- **Static semantics:** This concerns building the application. In
  this regard, the application is independent of Google Analytics
  because it can be built and deployed without it.

- **Dynamic semantics:** This concerns runtime behavior. Here, the
  application is dependent because if Google Analytics is unavailable
  at runtime, metrics can no longer be collected.

- **Program logic or functional requirements:** In this sense, the
  application is dependent because improvements to Google Analytics
  can directly benefit the application. An abstraction layer also
  affects this category, creating greater independence by abstracting
  different implementations of the same requirements.

Thus, in each category, the question is not whether the application is
dependent or independent. Rather, there are different types
of dependency. In terms of functional requirements, new Google
Analytics features may directly influence the application, while at
the same time Google Analytics remains replaceable if an abstraction
layer is introduced and the functional requirements continue to be
satisfied.

## Even More Confusion

There are many more examples that illustrate the complexity of
dependencies.

If one application writes a file in a specific format and another
reads that file, there is clearly a dependency. But what depends on
what? Jimmy Koppel suggests one interpretation: serialization and
deserialization depend on each other because the data written during
serialization must be readable during deserialization. Another
interpretation is that both implement a common specification. In that
case, both depend on the specification.

However, this perspective is purely technical. If the concern is
ensuring that the correct and meaningful business data is written,
then the two applications depend directly on each other. The
communication medium is irrelevant. Writing files creates essentially
the same challenges as sending and receiving messages.

A message bus does not automatically create decoupling.
{: .callout }

This is why a message bus does not automatically create
decoupling. Data formats and the semantics of the data must still be
coordinated. In addition, there is now a dependency on the message bus
itself in terms of availability. Components can no longer communicate
if the message bus fails, which can have consequences ranging all the
way to the failure of the entire system.

## Conclusion

The concept of **dependency** is central to software architecture, but
unfortunately it is not particularly well defined. Software
architecture typically focuses on dependencies in relation to change,
and concepts such as black-box and white-box dependencies can be
useful in that context.

In reality, however, dependencies have many different dimensions. It
is worth examining the concept carefully precisely because it is so
important.

*This is a translation of my [German article at Java
Magazin](https://entwickler.de/reader/reading/java-magazin/7.2025/05f865d3dbb38a8904cdf802).*
