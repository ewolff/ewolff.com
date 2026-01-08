---
title: "Cohesion, Modules, and Hierarchies"
layout: blog
description: Good modules have high cohesion — alongside loose coupling from previous post, this is the most important property of modules. But why is cohesion so important? And how does it influence the design of software systems?
tags:
- Fundamentals
---

Cohesion means something like "togetherness". The cohesion of a module
is good when the individual parts of the module somehow belong
together. In fact, it is possible to develop good architectural
designs by simply implementing functionalities that intuitively belong
together in a single module such as a microservice.

Cohesion and loose coupling are therefore related and
mutually dependent.
{: .callout }

For example, assume that a specific product can be reserved, then
ordered, and finally delivered. We are talking about a concrete
product — for instance, a specific used laptop that exists only once
in stock with exactly this configuration. The functionalities
ordering, reserving, and delivering are candidates for a shared
implementation in one microservice. They could **share a data model** in
which the state of a product (ordered, reserved, delivered) is
stored. If one of these functionalities is implemented somewhere else,
this model is torn apart. The status would then have to be available
in two places. As a result, the modules would have to interact a lot,
because the product’s state would have to be kept consistent in both
places. In addition, changes might require modifying both places—and
then the two microservices would no longer be loosely
coupled. Cohesion and loose coupling are therefore related and
mutually dependent.

This way of thinking in terms of models and shared functionality is
central to good modularization.
{: .callout }

This way of thinking in terms of models and shared functionality is
central to good modularization. Unfortunately, this does not seem to
be clear to all software developers and architects, so in practice
models that actually belong together are sometimes split apart,
resulting in poor modularizations.

As so often, there are gray areas here. The concrete approach depends
primarily on the specific domain. That ordering, reserving, and
delivering are so closely related that they must share a data model is
a result of the specific domain. If, for example, not a specific
laptop is reserved and ordered, but merely some laptop that meets
certain specifications, the modeling can look different. Then it may
be sufficient to reconcile inventory levels to avoid reserving and
ordering too many laptops with certain specifications. This difference
is a consequence of the business model: for used laptops there may be
only one specific item with a given configuration, while for new
laptops there may be a stock of identical products.

Delivering the laptop means that no other customer can reserve or
order it. But delivery must also is have logic to actually ship the
laptop, which may be better placed in another module. In other words,
the domain concept of "delivery" can be represented in different
models across different modules: one module that models the state of
the product (reserved, delivered ...), and another that actually does
the actually shipment process.

## Cohesion, Code Duplication, and DRY

**Code duplication** might be an indicator of weak cohesion. This makes
sense: when code is duplicated, the same or almost the same logic is
implemented in two places, even though it should really exist in only
one place. Something has been "torn apart" that probably belongs
together. **DRY (Don’t Repeat Yourself)** can be a countermeasure. DRY
says code should never be duplicated; instead, code should always be
adapted to be flexible enough to cover multiple cases. For example,
duplication of a class can be avoided through a superclass and
inheritance, or duplication of a method through an additional
parameter or a conditional branch.

But the example of data modeling for laptops is a case where DRY and
avoiding code duplication would not have solved the problem. One can
implement ordering and reserving in two separate microservices and
thus achieve no cohesion, while still adhering to DRY. DRY alone is
therefore not sufficient as a concept for achieving cohesion.

Code duplication violates cohesion but can create loose coupling.
{: .callout }

Interestingly, code duplication violates cohesion but can create loose
coupling: When code is duplicated, the two copies can be evolved
independently. For example, if a specific software solution for one
customer is to be turned into an industry solution, one can copy the
specific solution for each customer and adapt it. This is very easy to
implement and enables completely separate development, making
customer-specific changes easy. The changes are thus completely
decoupled — more than just loosely coupled. On the other hand, copying
code also means that a separate, specific solution emerges for each
customer, making it nearly impossible to implement features for all
customers, because these features would have to be implemented in all
customer-specific code bases.

Implement a generic core only after the third similar implementation?
{: .callout }

It seems obvious that it is better to use a single code base for all
customers — there are reasons why DRY an important concept. But then
one has to design a reusable code base of domain logic. This is not
easy at all, which is why
[some](https://software-architektur.tv/2023/10/13/episode184.html)
actually recommend implementing a generic core only after the third
similar implementation. This suggests that up to a certain point,
one benefits more from strict separation and the resulting loose
coupling than from reuse and the tight coupling of a shared code base.

## Hierarchies

In the laptop example, the discussion revolved around functionalities
such as ordering products. With the proposed decomposition, changes to
this functionality would affect only one microservice. But other
criteria for cohesion can also be defined: doesn’t all business logic
code belong together? And the user interface code? When changes are
made to the ordering process, both parts of the system are affected: a
change in business logic can only be used after corresponding changes
to the user interface. Nevertheless, business logic belongs together
and should be separated from user interface code. So there is another
level of modules and cohesion here.

Modules form a hierarchy.
{: .callout }

In fact, modules form a hierarchy: microservices, for example, are
divided into e.g. Java packages that may contain user interface or
business logic. Below that are classes that contain specific parts of
the business logic or user interface, and finally methods. At all
these levels, things that belong together should be implemented
together.

At a coarse-grained level, decomposition should follow domain concerns.
{: .callout }

At a coarse-grained level such as microservices, decomposition should
follow domain concerns; at a fine-grained level, it should follow
technical aspects such as business logic and user interface. Cohesion
applies to all sizes of modules such as microservices, Java packages,
or classes.

## Size and Cohesion

There is a trivial way to always ensure that everything that belongs
together is in one module: just have a single module for the complete
system. For example, one microservice for an entire system, or one
class for a microservice. Obviously, this is a bad idea, because the
systems then become very hard to understand. So size plays a role:
microservices, classes, and methods should be small enough to understand.

Cohesion also means separating what does not belong together.
{: .callout }

So cohesion does not only mean grouping together what belongs
together, but also separating what does not belong together. If
unrelated domain concerns are implemented together in one
microservice, it not only becomes too large, but there are also too
many domain reasons to change it, turning it into a change hotspot.

## Conclusion

Cohesion provides a good way to identify modules: if you implement
things that belong together in the same module, you created at good
designs. Like all other rules for designing architectures, also this one
depends on the domain and the specific use case. This makes it
difficult to apply in practice. However, it applies at all levels:
microservices, packages, classes, and even methods. That is why it is
so important to truly understand these concepts and their effects.

*This is a translation of my [German article at Java
Magazin](https://entwickler.de/reader/reading/java-magazin/5.2025/c089adccc63144b27b9cfcd0).*
