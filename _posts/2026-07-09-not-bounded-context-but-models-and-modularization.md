---
title: "Getting Architecture Right: Not Bounded Context but Models and Modularization"
layout: blog
description: A good decomposition of the domain logic is crucial for making systems maintainable in the long term. Discussions often focus on Bounded Contexts — but models are far more important.
tags:
- Modularization
- Domain-driven Design
---

Bounded Contexts are often regarded as a silver bullet for the
architecture of the domain logic. But in practice they are rarely
sufficient. Inside a Bounded Context a Ubiquitous Language is defined
— a shared language between developers and domain experts. Every
project has its own language. And terms are often defined differently
in different contexts.

For example, during hotel check-in, the customer is the human check
in. However, when invoicing the same stay, for a business trip the
customer might be the employer of the person checking in. This is a
different customer and a company rather than a human. So check-in and
invoicing are probably two Bounded Context with different
languages. Each language ahas a different definition of the term
"customer". Such distinctions are valuable for analyzing and
understanding the business domain. But are they also a good starting
point for architecture?

As architects, what we really want is a decomposition of the domain
logic into modules.
{: .callout }

As architects, what we really want is a decomposition of the domain
logic into modules. A Bounded Context defines the scope of such a
module — for example, check-in or invoicing. At the same time,
Domain-Driven Design views a Bounded Context also as a part of the
software for which a team is responsible.

As a result, Bounded Contexts are defined as:

* a boundaries for **modules** of the domain logic,
* the scope of a **Ubiquitous Language**, and
* the area of responsibility of a **development team**.

These three meanings are problematic. They overload the concept and
make it harder to understand ([German stream /
podcast](https://software-architektur.tv/2025/04/25/folge261.html)
discussing the three definitions.)

In some situations they even lead to questionable restrictions. Why
should teams be allowed to work only on Bounded Context? In reality,
quite some teams work on UI or entirely different things like
infrastructure automation. Why should collaboration between multiple
teams on the same Bounded Context be ruled out? Certainly, such
collaboration may introduce friction, but that alone is not a reason
to prohibit it. And why couldn't an area governed by a single
Ubiquitous Language contain multiple modules?

## Models

At the core of what we as software architects actually want to achieve
with Bounded Contexts is the creation of models.

In fact, the original [Domain-Driven Design book]() begins by discussing models, using the example of a map of China. The book defines a model as follows:

> "A model is a simplification. It is an interpretation of reality
> that abstracts the aspects relevant to solving the problem at hand
> and ignores extraneous details."

The famous quote by George Box, *"All models are wrong, but some are
useful,"* makes the point clear: the goal is not a perfect
representation of reality but a useful simplification. Which aspects
are relevant depends on perspective—which brings us back to Bounded
Contexts.

## The Real Problem: Organizing Business Logic

The goal of the entire exercise is a sensible decomposition of
business logic that enables maintainability and extensibility.

The team-related questions that Bounded Contexts also address are
secondary. A different Ubiquitous Language may indicate that a
separate module makes sense, but the concept of multiple Ubiquitous
Languages is not always easy to grasp.

From an architect's perspective, it may be easier to think in terms of
**data** and its structure. The example of the ambiguous definition of
"customer" in different Bounded Contexts is directly reflected in data
modeling. Focusing on data modeling might be easier for architects
than focusing on the multiple definitions of a term.

Bounded Contexts do not solve the problem of organizing business
logic.
{: .callout }

Bounded Contexts therefore do not solve the problem of organizing
business logic. They merely tell us that we need multiple models — not
what those models are or how to find them.

Of course, collaborative modeling approaches such as [Event
Storming](https://www.eventstorming.com/) can help identify models,
and they are very valuable. Nevertheless, it is useful to have
alternatives. Moreover, we must be able to evaluate and refine the
results of such design exercises. To do that, we need to understand
what makes a model suitable for software.

Models are simplifications created for a specific purpose.
{: .callout }

Models are simplifications created for a specific purpose — in this
case, representing a business domain in software. Since many different
models are possible, understanding the characteristics of a good model
becomes critically important.

## Information Hiding

Information Hiding is a fundamental concept for developing large
systems.

The foundation is the observation that developers will use every piece
of information they can get about a module. Once they depend on that
information, it can no longer be changed easily. As a result, the
system becomes difficult to modify.

An example: Consider a class intended to model a bank account. It
exposes an instance variable representing the account balance. We know
that allowing direct access to this variable without getters and
setters is a bad idea — but why?

If direct access is permitted, we lose the ability to change the
model. Instead of storing the balance directly, we might later decide
to calculate it from the transaction history. In that case, the
internal implementation would be entirely different.

If consumers know only the interface, we can swap the implementation
for another without affecting other modules.
{: .callout }

If consumers know only the interface, we can swap the implementation
for another without affecting other modules. Hiding the implementation
is therefore an important aspect of Information Hiding.

This leads to another important insight: data such as the account
balance is not a good foundation for modularization. Functionality —
such as retrieving the account balance — is the better starting
point. Certain data is needed to provide that functionality, but the
data itself should not define the module.

## Coarse-grained Modules

What we discussed at the class level also applies to coarse-grained
modules, such as those that often form the basis of Bounded Contexts
or Microservices.

A coarse-grained module responsible for bank accounts will likely have
a database. If other parts of the system access that database directly
instead of going through the module's interface — for example, to read
account balances — then changing the module becomes much more difficult.

Of course, some information cannot be hidden. For example, calculating
a balance from transactions will generally take longer than returning
a stored value. This runtime behavior can be observed even if only the
interface is exposed. It might be important if a consumer of the
interface has some performance constraints that limit how the
implementation can be changed.

Information Hiding therefore suggests that we should focus on the
interfaces of modules and models. However, that alone is not enough to
design good modules.

## Abstract Data Types

The concept of [**Abstract Data Types
(ADTs)**](https://en.wikipedia.org/wiki/Abstract_data_type) can help
us further refine the definition of an interface. An ADT defines the
behavior of a data type from the perspective of its users. Besides the
set of values the data type can represent, its defining
characteristics are primarily its operations — that is, its interface.

A classic example of an ADT is the
[**stack**](https://en.wikipedia.org/wiki/Stack_(abstract_data_type)). The
data structure is modeled after a physical stack, such as a stack of
plates. A stack provides the following operations:

- **Push** places an item onto the stack.
- **Pop** removes and returns the most recently added item.
- Optionally, an operation can test whether the stack is empty,
  although this is not an essential operation.

If we first push the number 23 and then 42 onto the stack, a
subsequent pop returns 42, and the next pop returns 23. Thus, **Pop**
not only returns the element but also removes it from the stack. A
stack is therefore a **Last In – First Out (LIFO)** data structure.

At the interface level, we can define additional semantics using
**preconditions**, **postconditions**, and **invariants**.

The precondition of **Pop** is that the stack must not be empty. After
executing **Push**, the stack is guaranteed not to be empty, making
this a postcondition of **Push**. There may also be invariants that
always hold.

ADTs can become almost a specification of a module.
{: .callout }

ADTs therefore extend the concept of Information Hiding by recognizing
that an interface can be more than just a list of operations — it can
become almost a specification of a module.

Nevertheless, different implementations of the same ADT are
possible. For example, a stack can be implemented using an array and
an index pointing to the top element. Alternatively, it can be
implemented as a linked list, where each stack element points to the
one below it. These implementations may differ in performance or
memory consumption, but both satisfy the semantics of a stack.

Using the ideas behind ADTs, we can define the behavior of a module
solely at the interface level without prescribing its
implementation. Focusing on the interface therefore achieves more than
Information Hiding alone.

This emphasis on specifying a module through its interface is also the
central idea behind **Test-Driven Development (TDD)**. A test is
written before the implementation exists. To write the test, the
interface must first be defined. Only after the test has been written
is the implementation created. Here, too, [the design is
driven](https://bsky.app/profile/jasongorman.bsky.social/post/3lnhjxke4vc22)
by the perspective of how the module will be used.

## Autonomy

Ideally, modules should be **autonomous**: every piece of
functionality should be implementable without relying on other modules
too much. Then, a change to a particular feature can typically be made
within a single module without affecting others.

In practice, however, not every change can be confined to one
module. Modules together form the overall system, and some changes
inevitably cross module boundaries. Nevertheless, autonomy remains an
important design goal.

Autonomy leads to additional heuristics for creating good modules.
{: .callout }

If we consider autonomy as a design objective, it leads to additional
heuristics for creating good modules.

Take the hotel example discussed earlier. We could implement the
system using three modules:

- Check-In
- Invoicing
- Customer

The Check-In and Invoicing modules contain the business logic for their
respective processes. The Customer module provides customer data.

Such a design is certainly feasible, but the Customer module may
become problematic for two reasons.

1. **Invoicing** and **Check-In** require different information about
   a customer. In fact, they deal with different concepts both called
   "customer". As discussed earlier, the customer in Check-In must be
   a human, whereas in Invoicing this is not necessarily the case. Other
   parts of the system may introduce yet more interpretations. During
   booking, for example, customers might be travel agents who book
   trips on behalf of companies. These correspond to several customers
   in the Check-In context but perhaps only one customer in
   Invoicing. Trying to unify all these concepts within a single
   Customer module may make that module quite complex.

2. Many hotel functions require **customer** information: Check-In,
   Invoicing, Booking, and so on. This is hardly surprising, since a
   hotel provides services to customers. So quite a lot of business
   logic will deal with customers. If customer functionality is
   concentrated in a single module, that module will be used by many
   others. It becomes a dependency hotspot, reducing the autonomy of
   the remaining modules.

Autonomy therefore highlights a particular weakness of modules that
merely model data. Such modules reduce autonomy and tend to have many
dependencies.

On the other hand, they may offer advantages. For example, storing a
customer's name in one place makes it easier to handle name changes
consistently throughout the system. Whether this benefit justifies the
reduced autonomy is a trade-off that must be evaluated — but at least
the trade-off becomes explicit. Quite honestly valuing autonomy lower
than supporting a name change would be surprising. But the trade-off
might be different in other cases.

Moreover, a module that merely models data is also likely to violate
the principles of **Information Hiding**, since data is typically an
implementation detail. Nevertheless, many systems are designed around
such data-centric modules. When improving these architectures, it is
important to articulate their disadvantages clearly before deciding
whether restructuring is worthwhile.

The decision is not simply black or white. Some customer information,
such as the customer's name, may be placed in a shared module, while
more specialized information—such as booking preferences—can remain in
the Booking module that actually requires it.

# Three Heuristics

We now have three heuristics for designing good models or modules:

- **Information Hiding** suggests that modules should be defined in
  terms of their interfaces — and thus their functionality — rather
  than their data.
- **Abstract Data Types (ADTs)** demonstrate that an interface can
  define the meaning of functionality. Preconditions, postconditions,
  and invariants are also part of the interface. Much like Test-Driven
  Development, adopting the external perspective of a module's users
  helps achieve a sound decomposition.
- **Autonomy** serves as another design goal, making modules that
  merely model shared data appear less attractive.

# Examples

Let us apply these heuristics to design decisions commonly encountered
in practice.

Should an **ordering process** implement not only the execution of an
order but also the decision whether a customer is allowed to place an
order?

From the perspective of ADTs, this seems reasonable. Determining
whether ordering is permitted is a **precondition** for the ordering
operation itself.

However, this is only one heuristic. If authorizing an order
requires entirely different data and business logic from processing
the order, then authorization represents a different model and should
probably be implemented separately.

Should a **payment process** know about products?

Looking only at the interface, a payment service should probably
receive nothing more than a monetary amount and return whether the
payment succeeded.

On the other hand, there may be situations where products must be
known. For example, a credit card company may provide insurance for
certain products and therefore require information about what was
purchased.

Finally, the autonomy heuristic can guide the decision of whether
modules should contain shared data models or maintain their own
specialized representations.

Thus, these heuristics point us in a particular direction, but they do
not determine the correct solution. What the best design is, still
needs to be evaluated in each specific situation.

# Conclusion

Creating models and modules for business logic is the central challenge
of business architecture.

A Bounded Context merely tells us that multiple models may exist. It
does not explain what those models should be or how to identify them.

Information Hiding, Abstract Data Types, and Autonomy provide useful
heuristics for discovering and evaluating such models. Other
approaches, such as Event Storming, also contribute to this
process. Even there, however, these heuristics remain valuable,
because Event Storming merely produces candidate models that must
subsequently be evaluated and refined.

More generally, these heuristics are useful whenever architectural
designs need to be assessed.

*This is a translation of my [German article at Java
Magazin](https://entwickler.de/reader/reading/java-magazin/8.2025/807160beec78709947ca8a04).*
