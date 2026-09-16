---
title: "Stable Architecture – Good Architecture?"
layout: blog
description: "The term architecture itself, and the metaphor borrowed from the construction industry, convey a sense of stability. But in reality, stability is not achievable in software architecture – and striving for stability can even be harmful."
tags:
- Stability
---

At the same time, software architecture also seems to somehow stand
for important decisions – and some even claim that software
architecture is about [“the important stuff – whatever that may
be.”](https://martinfowler.com/architecture/).

The assumed importance and stability understandably lead to the goal
to get the architecture right at the beginning of a project. If we
make the right decisions about the important things and those
decisions remain stable, the success of the project is pratically
guaranteed.

Get the architecture right at the beginning of a project?
{: .callout }

This approach is not only understandable, but also makes sense to a
certain degree:

* Probably not everything important is software architecture – but
  architecture is certainly important. After all, it addresses
  questions such as how the software should be structured or how
  quality goals can be achieved.
  
* Accordingly, it is clearly useful to think about these
  issues. The only question that remains is when to do so.
  
* Architecture consists of a multitude of decisions. At the beginning,
  nothing has been decided yet, so software architecture work is
  particularly useful at this point. It answers important questions –
  for example, concerning the fundamental structure and fundamental
  technical challenges.

These points are probably intuitively clear to most people, which
leads to some kind of “architecture phase” at the beginning of a project.

## Big Design Up Front?

This approach becomes problematic when the initial architecture
becomes too detailed. Extreme Programming coined the term “Big Design
Up Front” for such an overly elaborate architecture, and then moved to
the opposite extreme: defining as little architecture as possible at
the beginning and instead making all decisions later.

To a certain extent, this made sense at the time, because it provided
a counterpoint to the concept of Big Design Up Front. It also fits the
idea that decisions should be made as late as possible. Delaying
decisions has the advantage that more information is available at a
later point in time, which can also be taken into account when making
the decision, leading to a better decision.

Decisions should be made as late as possible. 
{: .callout }

And, of course, nobody can foresee everything at the beginning of a
project. New requirements emerge, our understanding of the
requirements changes, new technologies become available – all of this
can mean that new architectural decisions have to be made or existing
decisions have to be revised.

This is why Architecture Decision Records (ADRs) document not only the
decision itself, but also the reasons behind it. This makes it
possible to determine later whether something has changed in the
rationale and, if so, to subsequently revise the decision. In other
words: An ADR prepares a change to the decision right from the start.

## Why Do Architectures Often Not Fit?

In reality, many architectures no longer fit the problem they are
supposed to solve or are not particularly clean. There are only two
ways to address this:

* Think even more about the architecture at the beginning.

* Adjust the architecture when new insights emerge.

We have essentially already rejected the first option as “Big Design
Up Front.” So the problem is presumably a lack of subsequent
changes, because at the beginning we simply cannot know or consider
everything.

Ultimately adapting the architecture is probably the better approach.
{: .callout }

So it is problematic to design an architecture at the beginning with
the expectation that it should be “right” and stable. This likely
makes it harder to admit later that the decisions were right and good
at the time, but now need to be revised. Very quickly, we may find
ourselves trying to demonstrate that we did a good job back then and
that the new insights can therefore also be accommodated within the
existing architecture. Perhaps they can. But ultimately, [adapting the
architecture](https://software-architektur.tv/2022/10/28/folge140.html)
is probably the better approach.

## When Architecture Changes

But even in an obvious case, a team may still fail to make a change
that is actually necessary. Imagine, for example, that an application
is no longer merely supposed to enable users to enter data and store
it in a database. Instead, new requirements and a better understanding
of the domain have made it clear that there is complex logic involved
– validations, but also more complex logic. This is not particularly
unusual, because data is not an end in itself: it exists to provide
specific functionality. The birth date is not the point; the question
is whether a customer is allowed to purchase certain products or is
acceptable as a customer in the first place.

For storing data in a database, data containers without much logic
were sufficient. Now the logic needs to be organized – for example, in
an object-oriented model. But changing everything that has already
been implemented would be a massive effort. So initially, developers
implement the new logic only where they are writing new classes for
new functionality anyway.

Now both approaches coexist: pure data and data with logic. So the
architecture is inconsistent. Something similar often happens when
systems are migrated away from a mainframe: suddenly, two
architectures exist side by side. And sometimes another, newer
architectural design is introduced before everything has been
consolidated, further increasing the inconsistency.

So even if you revise the architecture, that does not mean that it
will actually be implemented consistently.

## Inconsistency

From a purely technical perspective, such an inconsistent architecture
is uncomfortable. Ideally, systems should have a consistent structure
and consistently follow simple principles, making them easier to
understand and change.

But software development takes place under economic constraints. What
economic reasons are there for bringing a system's architecture into a
consistent state? Understandability or maintainability seem like
technical reasons. They merely make it easier to further develop and
maintain the system. But in fact, this is a deeply economic argument:
When systems follow a consistent architecture, changes are easier and
cost less.

Ultimately, then, the question is purely economic: Is it cheaper to
make the system consistent so that changes become easier, or should
the system remain inconsistent because there will not be enough
changes to justify the investment in a clean architecture? The
architecture is “merely” the result of this economic
decision. Unfortunately, such a rational decision is often not made –
for example, when features are implemented without considering the
necessary investment in architecture.

Perhaps architectures are the way they are because it makes economic
sense.
{: .callout }

So perhaps architectures are the way they are because itq
makes economic sense – or because architecture is simply not taken
into account. But there are also many cases where inconsistency has
reached such a level that consultants are brought in to find a
solution. In those cases, more should have been invested in a clean
architecture earlier. The focus on features has eventually led to a
situation where no more features can be implemented.

Either way, however, the problems are probably rooted in the
evolutionary development of the architecture rather than in the
initial design.

So architecture is primarily about organizing the “historical growth”
of the architecture – not about making a few important decisions at
the beginning that then form the basis of a stable architecture.

## Conclusion

Architecture cannot be stable because software has to change due to
new technologies, new requirements, or a better understanding of the
domain. Architecture cannot be exempt from these changes. Accordingly,
the actually implemented architecture would have to be adapted to the
changing ideal architecture. But that is often not economically
feasible.

The result is the typical inconsistent architecture that dominates
real-world systems. Such architectures are either the result of
insufficient investment in architecture or of an economic trade-off.

*This is a translation of my [German article at Java
Magazin](https://entwickler.de/reader/reading/java-magazin/10.2025/b8c5ab011364005a1e13123b).*
