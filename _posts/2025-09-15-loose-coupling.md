---
title: "The Problem with Loose Coupling and Why It Is Important"
layout: blog
description: Loose coupling is a very well-known concept and is regarded as an important quality of an architecture—perhaps even the most important. But how can loose coupling actually be achieved? And why exactly should an architecture have this property?
tags:
- Fundamentals
---

As so often in software architecture, loose coupling is about
**dependencies**. An architecture divides software into different
parts such as packages, microservices, or classes. Ideally, this
allows you to change and understand just one part instead of the whole
system. There must, of course, be dependencies between these parts
because they are supposed to form a complete system. Therefore, truly
“independent” components are impossible. The question then becomes:
what kinds of dependencies should we aim for?

This is where loose coupling comes in: if changes do not ripple
through to dependent components, we speak of **loose coupling**. The
two components may depend on each other, but a change typically
affects only one component and does not touch its dependents. Some
**changes** may still involve both components, but under loose
coupling, this is the exception.

If changes do not ripple through to dependent components, we speak of
**loose coupling**.
{: .callout }

This property plays a crucial role: it ensures that we can modify
**large systems** by changing just one component while largely
ignoring the rest. Without loose coupling, changes become difficult
because dependencies may cause effects throughout the system. In the
worst case, those effects become unpredictable, and the software is
practically unchangeable because the risk of unintended side effects
is too great.

## How to Achieve Loose Coupling

If loose coupling is so important, the obvious question is how to
achieve it. A key concept is modularization: components expose an
**interface** and hide their **implementation**. For classes, for
example, the interface consists of public methods, while their
implementation and private methods remain hidden. This guarantees that
other classes can only depend on the interface. A change that keeps
the interface stable does not technically propagate to other
classes. Of course, a change in behavior may still force updates to
other classes.

A key concept is modularization: components expose an **interface**
and hide their **implementation**.
{: .callout }

Modularization and loose coupling are also why you should avoid
exposing **instance variables** directly: if you change how data is
modeled in instance variables but those variables are accessed outside
the class, changes will ripple outward, making the coupling less
loose. An even more extreme case is sharing a database directly. At
worst, you may not even know which applications are reading from or
writing to the database. If you want to change the database schema,
all these applications could be affected. This tight coupling is why
database schemas often become practically unchangeable. The remedy is
to hide the data model and allow access only through an interface.

There are many other potential dependency hotspots where changes can
ripple through the system — shared data structures, for example.

So, loose coupling is achieved through **modularization** — the
fundamental concept of software architecture. But in practice, loose
coupling is so critical that we often wish for additional ways to
improve it.

## Adapter Layers: Not a Good Idea!

Some architectures introduce an extra layer to further decouple
interface and implementation. In this layer, data is copied into
**Data Transfer Objects (DTOs)**, and an adapter with its own
interface is implemented to hide the interface of the underlying
layer. The idea is that changes to the external interface won’t "bleed
through" but can be addressed by updating only the DTO and
adapter. This should in theory create looser coupling since
changes typically affect only this layer.

The idea is that changes to the external interface won’t "bleed
through" but can be addressed by updating only the DTO and
adapter.
{: .callout }

In reality, these adapter layers often get in the way. When a change
does propagate, you have to update the adapter layer in addition to
the implementation. Adding a new feature to the interface always
requires updating the underlying implementation as well as the adapter
layer.

Subjectively, such adapter layers tend to hinder more than they help
because some changes become more cumbersome. The **overhead** rarely
seems justified by the savings in other cases. This situation occurs
whenever changes commonly pass through the adapter layer — which is not
unusual: new features and changes affecting more than just the
interface are frequent, and these always pass through the
adapter. Furthermore, the system now has an extra layer, making it
harder to understand and thus harder to modify.

Subjectively, such adapter layers tend to hinder more than they help
because some changes become more cumbersome.
{: .callout }

This points to another issue with loose coupling: it is easy to look
back and see whether a system was loosely coupled for past
changes. But **designing** a system to remain loosely coupled for
future changes is much harder. Good modularization will likely result
in looser coupling; adapter layers, on the other hand, rarely will.

Therefore, it’s worth examining loose coupling to improve it. An
important input for this is [Behavioral Code
Analysis](https://software-architektur.tv/2023/06/07/folge168.html). It
looks at how a team interacts with and changes the software. This
approach reveals which parts of the code are often changed
together. You can then take steps to restructure the code so that
similar changes in the future affect only a small part of the system,
making them easier to implement.

In general, **iterative architecture evolution** is a good idea. As
the project progresses, you learn which approaches work well or poorly
and can adjust the architecture accordingly. Only through such
adjustments do truly good architectures emerge. If you neglect
iterative improvement, the system’s quality will inevitably decline.

## Domain Logic

Still, it would be nice to design a system upfront to achieve as much
loose coupling as possible. As mentioned, modularization can help — but
it’s also worth considering completely different strategies. Up to
this point, we have mainly looked at technical measures like
modularization or adapter layers. But software is usually changed or
extended because of the domain.

But software is usually changed or extended because of the
domain. Therefore, you shouldn’t rely solely on technical measures —
you should strive to reflect the **domain concepts** accurately in
code.
{: .callout }

Therefore, you shouldn’t rely solely on technical measures — you
should strive to reflect the **domain concepts** accurately in
code. Then, domain-related changes become easy to
implement. Misrepresentations are common here. For example, if a
payment module knows too much about products, it will need to be
updated whenever a new type of product is introduced. That leads to
tight coupling: every change for a new product type affects payment,
in addition to other modules that configure products. But this is also
probably a domain modeling mistake: conceptually, payment should
simply ensure a specific amount of money is received. Why should this
part of the system know which product that amount applies to? That’s a
question about the domain — but it can lead to loose or tight
coupling, especially for critical changes to the domain logic. No
technical measure — neither modularization nor adapter layers — can solve
this problem. On the contrary, an adapter layer could make changes for
a new product even more complicated.

Thus, a sensible separation of domain logic is a key factor
for loose coupling — and this can be addressed during system design, not
just afterward.

## Conclusion

Loose coupling is rightly considered an essential property of good
architecture. Only with this property are large systems truly
maintainable, as changes have minimal impact and are therefore lower
risk. To achieve it: 

* Focus on modularization and domain modeling
* Be skeptic about technical measures that introduce extra code — like
adapter layers
* Examine how your team interacts with the software. This can teach
you valuable lessons about your architecture and help simplify typical
changes.

*This is a translation of my [German article at Java
Magazin](https://entwickler.de/reader/reading/entwickler.de-blog/3.2025/8ac0fd017dcfe238f917b41d).*

