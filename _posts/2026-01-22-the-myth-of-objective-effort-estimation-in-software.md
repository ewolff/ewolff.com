---
title: "The Myth of Objective Effort Estimation in Software Development"
layout: blog
description: The estimated effort of a software project usually refers to the specific team involved. But can effort be estimated objectively and independently of the team?
tags:
- Fundamentals
---

An objectively estimate would clarify how long it takes to implement a
feature and how much it costs. This could help e.g. when outsourcing
development services.

In agile methods, the effort of a feature is estimated as a story
during planning meetings to decide whether a story should be
implemented. This is optional: NoEstimates describes projects that
work entirely without effort estimates. The advantage: The effort
spent on estimating is eliminated and can instead be used to develop
stories. It is enough prioritization if everyone on the team works on the
currently most valuable feature. [Woody
Zuill](https://software-architektur.tv/2025/02/24/episode252.html) is
a pioneer in this area and has never worked any other way.

Is it enough prioritization if everyone on the team works on the
currently most valuable feature?
{: .callout }

Estimating stories is usually based on a reference story or
functionality that is assigned a size of one. Other stories are
estimated relative to this reference, by and for the team that is
doing the estimating. In addition, there is the team’s velocity
(speed). It is measured in implemented story points per iteration and
can change over the course of a project.

## Objective estimates?

So the estimate is not objective, because it involves the specific
team and because velocity changes over time. However, the estimation
methodology achieves its goal: it allows teams to plan their
work. Through estimation relative to a reference story and through
velocity, it is also possible to make a reasonably good estimate of
what a team can deliver.

Of course, one can try to make these measurements more objective. For
example, a uniform reference story could be chosen. There are
approaches that go much further. The [Function Point
method](https://en.wikipedia.org/wiki/Function_point) attempts to
measure the objective complexity of a business requirement in function
points. But these methods also show variability in estimates. In
addition, they require experience in estimating and are
labor-intensive. Methods such as
[COCOMO](https://en.wikipedia.org/wiki/COCOMO) even warn that their
results provide only rough numbers, not precise estimates.

The usefulness of such estimates is questionable: projects always
change their scope. When software is used in practice, new
requirements emerge. Software development is a process in which
engineers and users learn together how best to support business
processes with software. When you learn something new, you change the
scope. Then precise estimates for the original scope are no longer
worth much, and the effort spent on additional precision is not well
invested. Perhaps this is why agile estimation is used in practice,
but more sophisticated methods rarely are.

When software is used in practice, new requirements emerge.
{: .callout }

Overall, the focus on effort in projects is often exaggerated. Like
any investment, an investment in software must generate value that
exceeds the investment — ideally by a large margin. Estimating value,
however, often seems to be treated as a secondary concern compared to
estimating effort.

## Start-ups

There are very small teams that have developed extremely successful
software. Such outliers raise the question of whether objective
estimation is even possible. Before its acquisition,
[Instagram](https://www.theverge.com/2012/4/13/2946785/facebook-instagram-acquisition)
was valued at one billion dollars, operated a globally scaled system,
and did so with only 13 employees. Before its acquisition,
[WhatsApp](https://www.wired.com/2015/09/whatsapp-serves-900-million-users-50-engineers/)
had 900 million users; 50 engineers developed and operated this
system. That is a fraction of the staff involved in many IT projects
at established companies.

These applications appear to be "just" a simple photo-sharing app or a
messaging app. Does that explain the low staffing numbers? Insurance
products or savings plans seem also simple: you pay money and under
certain conditions, you get money back. Search engines are also
simple: there is even off-the-shelf software to index and search
documents.

On a superficial level, everything appears simple. The complexity of
a problem only becomes clear when you look at the details and truly
understand the problem.

The complexity of a problem only becomes clear when you look at the
details and truly understand the problem.
{: .callout }

Regardless of complexity, the economic success of a project is the
most important outcome. In this respect, Instagram and WhatsApp are
truly convincing: they created billions in value. That is almost only
possible for successful start-ups. But for every successful start-up,
there are many that are not successful.

## Established companies

Let’s assume an established company were to build a photo-sharing app
or a messaging app. It would build it using its typical mechanisms:
potentially hundreds of developers, sophisticated project management,
and detailed project plans. Thirteen people developing a central
system for a market breakthrough would more likely be perceived as a
risk than great value for the money. Large teams and projects also
bring a lot of [prestige](https://www.youtube.com/watch?v=3MP-4UcAYJU)
— for everyone involved, for managers, but also for
engineers. Finally, established companies usually have many software
projects, and the survival of the company rarely depends on any single
one — unlike a start-up. The pressure is therefore objectively lower
at established companies.

There are thus lots of mechanisms that lead to a completely different
level of effort. An established company will develop a software system
using the mechanisms it typically employs and is in a different
competitive situation than a start-up. In a start-up, on the other
hand, the economic conditions are such that something has to go live
as quickly as possible, maybe even at all costs — with corresponding
consequences.

## Solving problems differently

It is also unlikely that an established company would build exactly
the same application for a problem such as photo sharing or
messaging. The IT landscape into which the application must integrate
is different. Not really necessary requirements might be added —
something a start-up often cannot afford due to its economic
constraints.

A start-up would therefore likely develop a much simpler solution even
in areas that are traditionally implemented with complex software
systems — simply because it needs to get to market quickly and has a
very limited budget.

So trying to assess an objective effort makes even less sense:
software solves a problem that an organization has. For example, the
organization wants to establish a new product. To do so, it relies on
the social processes embedded in the organization. For a start-up, the
approach of an established company is just as alien as the approach
of a start-up is to an established company. This includes not only the
development process, but also the product itself.

In the end, the objective effort should not really concern us too
much. What matters is how we can develop better software in a given
situation. And for that, there are always many exciting possibilities.

## tl;dr

Determining the objective effort for a feature may be possible, but
only with great effort. Since it is unnecessary and costly for
planning, most projects do not use such techniques at all. Software is
also "just" an implementation of the solution to a business
problem. Organizations approach problems differently, so the solution
and the effort will differ for that reason alone. Nevertheless, one
can and should ask questions about
[productivity](https://www.youtube.com/watch?v=zLN_apxG8PM) and better
ways of working.

*This is a translation of my [German blog post at heise
Developer](https://www.heise.de/blog/Warum-objektive-Schaetzungen-in-der-Softwareentwicklung-nicht-funktionieren-11074323.html).*
