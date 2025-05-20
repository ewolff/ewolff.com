---
title: "The Real Software Architecture Problem: Communication Overload"
layout: blog
description: The distribution of information plays a central role in software development — there's a reason why so many people spend so much time in meetings. In fact, controlling the flow of information is a key challenge in software development — especially when it comes to limiting communication.
tags:
- Software Development
- Sociotechnical
- Information Hiding
---

Developers and other IT professionals are often frustrated by the
number of meetings — they consume a lot of their working hours. In the
end, there's hardly any time left for "actual" work. Yet, exchanging
information is a core part of IT work. Of course, some meetings could
be replaced with emails — but if meetings are entirely avoided,
important information might be lost. Even the remote meetings that
became common during the COVID era were often less effective and
helpful than direct, in-person communication.

In other words, reducing communication overhead by replacing all
meetings with emails is not effective. On the contrary: more direct
communication is often the better route. For instance, when knowledge
silos exist, some try to eliminate them through documentation —
essentially written communication. But direct communication is more
promising: Pair programming or mob / ensemble programming are suitable
approaches. Two (pair) or more (mob / ensemble) people share a
computer and develop together. If practiced long enough, knowledge
silos are eliminated, as there are always at least two people involved
in an implementation. It seems unlikely that developers can reach a
comparable level of understanding just by reading documentation.

Direct communication is also useful elsewhere: A business requirement
or story can rarely be described sufficiently in writing. This is
precisely why discussing stories is central in agile software
development — to clarify exact requirements during grooming or
estimation sessions.

Or you can improve communication by physically colocating team members
— putting them in the same room, for example. If subject matter
experts like product owners are in a different room than developers,
communication will suffer.

This places teams in a dilemma: On one hand, communication consumes
time that could otherwise be used for development; on the other hand,
it makes no sense to limit communication. In fact, if less
communication takes place, the team may have more time to write
code — but if there’s so little communication that it’s unclear what
should actually be developed, then the team may end up building the
wrong thing.

## Reducing the Need for Communication

The way out of this dilemma is not to restrict communication but to
reduce the need for it. And that brings us to a socio-technical
problem: The social problem of excessive communication can be
addressed through technical measures. The software system can be
designed in a way that requires less communication. This is, in fact,
a fundamental challenge in software architecture.

Here’s a brief detour into programming: When one class directly
accesses the instance variable of another class, it's considered bad
design. But why is that a problem? Code in one class naturally
accesses its own variables, so why not those of other classes? It
seems problematic because it breaks encapsulation. But where do the
real issues arise?

Consider a bank account as an example. If the instance variable
“balance” is accessed from outside the class, external code depends on
the existence of that variable. If the bank account is later changed
to calculate the balance from a list of transactions, the “balance”
variable might no longer exist. All classes that used it will need to
be updated — making the change quite hard to implement.

## Information Hiding

The key concept here is *information hiding*: The details of how the
bank account is modeled should be hidden within the class. That way,
the class can change its internal model without affecting other
classes. Instead of exposing the instance variable, a method should be
used to access the balance. That method can then be changed to
calculate the balance from a list of transactions instead of just
returning a variable. Other classes remain unaffected.

In general, information hiding means hiding details — such as how data
is modeled. If this information leaks out, other parts of the system
will depend on it. Changing the internal model will then require
changes elsewhere too, making modifications more difficult.

This concept also applies at a higher level: Modules, such as
microservices, should hide their data models behind interfaces. A
microservice managing bank accounts should expose a function to
retrieve the balance of an account. Whether the service stores the
balance directly in the database or calculates it from the
transactions stored in the database should be an internal decision
hidden from the outside.

So implementation details like database modeling should be hidden
behind the interface. Therefore, other modules or microservices should
not query the database directly. If they did, changing the data model
would become difficult.

So, information hiding applies at various levels of modularization:
both to classes and microservices.

## Information Hiding and Teams

At a broader level, information hiding affects the need for
communication between teams: When teams use information hiding, they
don’t need to communicate every change. As long as interfaces remain
stable, other teams are unaffected. So, software architecture concepts
like information hiding reduce the need for communication.

In fact, these social effects are the primary motivation behind
architectural concepts like information hiding. Reducing communication
needs through information hiding has been a key principle of software
architecture since its inception. So software architecture has always
had a socio-technical focus. Information hiding is applicable beyond
implementation details. For example, in *The Mythical Man-Month* [^1], Fred
Brooks described how every developer on the IBM OS/360 project had
access to a 10,000-page project manual. He later admitted this
contradicted David Parnas’s concept of information hiding — and that
Parnas had been right.

It’s unclear which parts of the documentation led to specific issues
during development. Software development back then was more
documentation-driven, and the type of information in documentation was
likely different from today.

Some information can't be hidden: If the account balance is computed rather
than retrieved, accessing it will likely be slower. This performance
loss is observable. A team might rely on fast access to the balance to
meet performance goals. If performance decreases, changes must be
coordinated with other teams.

## Further Communication Constraints

In essence, modules and information hiding can reduce the need for
communication — but only if changes stay local and don’t affect
interfaces. If typical changes in a project affect multiple modules,
interfaces must be updated, too. Those changes need to be communicated
and coordinated. Ideally, a change should only affect one module and
one team. If typical changes are business-related, it makes sense for
one team to own a business capability and implement it in a single
module. That team can then make changes independently, and others are
only impacted if interfaces change.

But communication can also influence team setups in other ways:
Communication is easier within the same location. People can talk
spontaneously or are already in the same room. If teams are
distributed across time zones or speak different languages,
communication becomes more difficult.

To reduce overhead, teams can be aligned by location. For instance, if
Java specialists are in one place and JavaScript specialists in
another, you could form Java and JavaScript teams by location. That
conflicts with business-capability alignment, since a business change
might involve both Java (backend) and JavaScript (frontend), requiring
collaboration across teams.

Still, a technology-based split might work better than a
business-oriented one. Business-oriented teams would span locations in
this scenario, increasing communication complexity. Technology-based
teams can colocate, making internal communication easier.

So, clever architecture and business alignment can reduce
communication needs — but external factors like staff distribution
also influence team structure. Since teams typically own code, a
decision to split into Java and JavaScript teams can also shape the
system architecture.

Again, this illustrates the socio-technical nature of the topic: Code
architecture and social factors like communication and team setup
influence each other.

## Team Topologies

[Team
Topologies](https://software-architektur.tv/2024/04/18/folge213.html)
also offer useful insights on communication:

- Team Topologies defines four different team types:
  - *Stream-aligned teams* own a stream of changes to production.
  - *Enabling teams* bring skills like architecture to stream-alogned
  teams.
  - *Complicated subsystem teams* implement e.g. complex algorithms.
  - *Platform Teams* provide which offer internal products like a
    Kubernetes cluster.
- Team Topologies also cover team interaction modes:
  - Teams can collaborate *as-a-service*, exposing APIs or user
  interfaces. A platform team might offer VMs via an API or UI. A
  complicated subsystem team might provide an algorithm as a callable
  service, hiding implementation details—similar to Information
  Hiding, but on a team level.
  - Teams can also work via *facilitation*, helping others build skills.
  - Or through *collaboration*, working closely on prototypes or new
  tech. However, long-term collaboration suggests that team boundaries
  might be wrong and need restructuring.
  
So, minimizing communication isn’t the only way to improve software
productivity. It involves trade-offs — like reducing the cognitive
load of a team. The purpose of Team Topologies is to enable
stream-aligned teams to work on changes to software while the other
teams provide their services to reduce the cognitive load of the
stream-aligned teams.

## Conclusion

From the start, software architecture has viewed projects as
socio-technical systems and sought to reduce communication needs
through concepts like information hiding. But minimizing communication
isn’t the sole goal: Communication is necessary for effective software
development. And even efforts to reduce the *need* for communication
via architecture involve trade-offs. The interplay between
communication and architecture remains fundamentally important.

**References**

[^1]: Frederick P. Brooks Jr.: *The Mythical Man-Month* (Anniversary Edition), Addison-Wesley, 1995, ISBN 978-0201835953  

*This is a translation of my [German article at Java
Magazin](https://entwickler.de/reader/reading/java-magazin/1.2025/501122c883f1a1609fc105ec).*
