---
title: "Replication, Consistency, and Domain-driven Design"
layout: blog
description: "Software engineers are often almost afraid of storing data redundantly. In practice, however, this is often the better option – because alternative solutions can create even bigger problems."
tags:
- Replication
- Consistency
- Domain-driven Design
---

**By Eberhard Wolff**

One problem many projects struggle with is legacy database
schemas. Like almost everything else, they have "evolved over
time". In other words, they are complicated and keep getting more
complicated, to the point where nobody really understands them
anymore. In addition, multiple applications typically access the same
database schema. This means that, in practice, only
backward-compatible changes are possible. Even those often require a
great deal of coordination. Such database schemas stand in the way of
properly modernizing a legacy system: Of course, you can change the
logic, but only to the extent that the existing database schema
allows. Changing the database schema itself, however, is practically
impossible because of its complexity and the potential impact on other
applications.

Changing the database schema is impossible because of its complexity
and the impact on other applications.
{: .callout }

Naturally, these problems exist with all shared data structures. For
example, if you send the details of an incoming order to all systems
as an event, you create a similar degree of dependency. Nevertheless,
database schemas tend to be the bigger problem in practice. Unlike
data structures such as an order event, database schemas are not part
of the interface but rather part of the internal data modeling. So if
you want to store more information, you have to change the schema –
and this happens much more frequently than needing to request
additional information from communication partners. Events therefore
change less frequently. Furthermore, events do not contain information
that is only required by the implementation, but only the data exposed
at the interface. This means they contain less information and are
therefore simpler data structures.

## The Solution?

Another
[post](/2026/07/09/not-bounded-context-but-models-and-modularization.html)
has already outlined a possible solution to this problem: smaller
models for different business domains. For example, in a hotel, you
might have a model for check-in that includes a customer. This is the
human staying at the hotel. The billing model also has a
customer. This might be the same human if they pay for their own stay,
or it might be their employer, which is a legal entity not a human. A
legal entity cannot check into a hotel. So these smaller models are
not just easier to understand and change - they might also lead to a
better understanding of the domain.

These smaller models are not just easier to understand and change -
they might also lead to a better understanding of the domain.
{: .callout }

Instead of having a central database containing all information about
a customer, this approach creates specialized models for different
functionalities, each containing only a subset of the
information. Each model is used in just one context, which improves
autonomy: fewer agreements and coordination are needed when making
changes.

## Redundancy!

Despite the obvious advantages, these smaller, easier-to-understand,
and more maintainable models have not really caught on. One reason is
the fear of redundant data storage. After all, the customer now exists
in several places, the data is stored in different systems, and all
these systems need to be kept up to date.

The fear of redundant data storage
{: .callout }

At first glance, this does indeed seem to be a challenge, because it
appears that all customer data is being replicated. In reality,
however, the customers are different from a business perspective: A
company cannot check into a hotel. For check-in, the date of birth or
ID number might be relevant, but certainly not for billing. These
differences are precisely why separate models make sense.

It is therefore important to discuss redundancy at the attribute level
and then the actual level of redundancy. In such discussions, the only
relevant scenarios sometimes turn out to be changes of name and
address. But if name and address are the only attributes actually
stored redundantly, this is probably only a small part of the overall
data.

Redundantly stored data is problematic only when changes are
necessary.
{: .callout }

Redundantly stored data is problematic only when changes are
necessary. Because of the redundancy, the data has to be changed in
multiple places. If the data never changes after it has been created,
redundant storage does not matter. If it changes only rarely, the
disadvantages of redundant storage may not be significant at all.

So name changes do not happen very often. On average, a person
probably changes their name less than once in their lifetime. Moving
house happens more frequently, but still not that often. Supporting
moves and name changes as effectively as possible is unlikely to
create a competitive advantage and may therefore not be all that
important. And the data does not necessarily drift out of sync. It is
perfectly possible to send changes to all systems and keep the data up
to date everywhere.

There may not actually be that many reasons against redundant data
storage.
{: .callout }

So there may not actually be that many reasons against redundant data
storage. In its favor are greater autonomy and simpler models that are
easier to evolve. In this trade-off, autonomy and maintainability
probably often outweigh the other factors, because they have a lasting
positive impact on development.

Of course, there are situations where redundant data storage could
create significant challenges. Then storing these attributes centrally
might make more sense - it's just one of the typical architecture
trade-offs.

The discussion about redundancy also reveals other facts: Changes
to addresses and names are indeed not always processed consistently
across all systems. In other words, despite centralized data storage
and its well-known disadvantages, changes are not necessarily
implemented everywhere and consistently. In reality, the supposed
benefits of centralized data storage are often nowhere to be seen.

## Changes = Logic

If you look more closely, these are not simply data changes. What
actually happens is a move, which results in a change of address. A
marriage, divorce, civil partnership, or change to a person's legal
gender entry results in a name change. A move or a civil partnership
may also trigger other actions – maybe sending a small gift as part
of a marketing campaign.

Data changes are really just part of implementing logic for specific
events.
{: .callout }

So what we are really talking about is implementing logic for specific
events. This may seem like a minor distinction, but it is important to
realize that the data change is only one part of that logic.

And the data does not change everywhere: It is not as though addresses
or names in old invoices are changed. Old invoices must remain as they
are. A shared model may therefore need to include a historized data
model that allows old names and addresses to be retrieved. This makes
the shared data model even more complicated. For invoices, given that
they must remain immutable, it would probably be a good idea to copy
the name and address when the invoice is created and then keep them
immutable. In this case, redundancy might avoid the need to keep old
versions of the data.


## Redundancy and Models

Of course, there are also situations where storing data redundantly
makes little sense. Imagine, for example, that one module in a system
handles incoming deliveries in a warehouse management system, while
another module handles outgoing deliveries. One module increases the
stock level, while the other decreases it. These changes happen
relatively frequently. If both modules store the stock level
redundantly, chaos is practically guaranteed, because changes from two
different sources would constantly have to be synchronized.

In this case, splitting things into two models would be
problematic. Both receiving and shipping should probably be
implemented using a single model. This model exposes the operations of
receiving and shipping goods. It implements the necessary logic and
then updates the stock level. Internally, this model knows about the
stock level. In other words, separating the two concerns would split a
single model into two. This is why creating meaningful models is so
important.

Creating meaningful models is very important.
{: .callout }

Other modules may be interested in the stock level. They should then
request it through the interface. Or perhaps they are not actually
interested in the stock level itself, but rather in whether a certain
number of products can be shipped. The stock level is only one factor
here: shipping capacity and reserved products may also play a
role. This once again argues for hiding the data and exposing a method
at the interface that provides access to some business logic - in this
case to figure out whether a product can be shipped.

Sometimes people even see a conflict between avoiding redundancy and
using different models as advocated by Domain-driven Design. But the
amount of data actually stored redundantly is usually acceptable. Also
the real concern may not be data at all, but rather logic such as
determining the quantities that can be shipped.

There is another advantage: Redundant data improves availability. If
the central system fails and can no longer provide any product
information, the impact is likely to be significant. If the data is
stored together with other relevant data, an outage is more
likely to remain limited to a single system.

## Fear?

So redundancy actually seems to be the better approach in many cases:
The problems caused by a few changes are outweighed by significant
gains in autonomy and the ability to evolve. To be clear: this does
not mean that redundancy should be preferred everywhere. Rather, the
pros and cons need to be weighed as part of an architectural
decision. Both a decision for a centralized model as well as for a
model with redundancy need to be justified.

Avoiding redundancy at all cost might seem "cleaner" and "clearer".
{: .callout }

Nevertheless, models without redundancy still seem to be preferred. If
there are so many arguments in favor of accepting a certain degree of
redundancy, this tendency is irrational. Perhaps storing data without
redundancy simply seems "cleaner" and "clearer". Precisely to counter
such irrational tendencies in a rational way, it is important to weigh
up and justify architectural decisions.

## Conclusion

A certain degree of redundancy often goes hand in hand with
significantly greater autonomy and the ability to evolve. Above all,
it solves the problem of overly complex shared data structures, such
as database schemas. Those stand in the way of further development or
modernization. Redundancy also makes it possible to create multiple
relatively autonomous modules. On closer inspection, the amount of
actual redundancy often turns out to be quite small. Nevertheless,
these solutions do not seem to be particularly popular, perhaps
because of an irrational aversion to any kind of redundancy.




