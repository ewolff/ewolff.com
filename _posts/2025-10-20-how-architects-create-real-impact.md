---
title: "How Architects Create Real Impact"
layout: blog
description: Designing architectures is one thing — but how can you ensure that the architecture you’ve designed is actually implemented? Every architect faces this challenge if they want to make an impact in a project.
tags:
- Fundamentals
---

First of all: of course, architects need technical expertise. They
must design architectures — and that involves structuring the system
into **modules**, classes, etc., to enable long-term
maintainability. Another aspect of architecture work involves making
**technical decisions** about certain technologies or
approaches. These decisions influence qualities (also known as
non-functional requirements) such as security, performance, or
usability. Making such decisions is at the core of architecture
work. Knowledge of technologies and architectural approaches is
therefore essential. But understanding the specific **requirements**
and desired **qualities** is also necessary to work effectively on the
architecture.

These aspects of architectural work are the focus of most articles,
books, and talks on the subject. However, this article takes a
different angle — because even a perfect architecture is useless if it
is not implemented. Only then can architects make an **impact**. This
aspect is extremely important in practice, yet there is significantly
less material available on the topic.

## Writing Code Yourself?

Architectural decisions affect the code: the code’s structure and the
technologies used within it. So, one might simply sit down at the
computer and implement the architectural decisions directly in
code. That approach obviously works if you’re implementing a project
alone. But most projects are developed by **teams**. You can still
implement your architectural ideas yourself — but that alone isn’t
enough if the other developers implement things that don’t align with
your design. And since there are more of "them" than "you," your
architectural ideas will never be fully reflected in the code unless
they get on board.

The real challenge is influencing the other developers.
{: .callout }

So, the real challenge is **influencing** the other
developers. Writing code yourself can help with that. It allows you to
better understand the challenges others face, gives you firsthand
experience with at least part of the technical context, and increases
your credibility — since you’re not just talking abstractly about
concepts, but actually applying them. Pair programming with other
developers can also help bring architectural ideas to life within a
project.

## Communication!

At this point, it should be clear what this is really about:
**communicating** ideas and **convincing** developers. Some people
expect there to be a kind of magic that allows them to persuade others
of their views. Even if such magic existed — would you really want to
convince everyone of the superiority of your own architectural ideas?

In software architecture, there are many possible options for every
decision. Depending on the specific context, one or another option
might make sense. Sure, you can debate endlessly about which framework
is better, how APIs should be structured, or which architectural
paradigms to use. But in the end, projects often fail for entirely
different reasons — misunderstood requirements, communication
breakdowns, or organizational challenges are common causes. And the
"correct" architecture always depends on the context. In other words:
many options can work; the differences between them might not be huge,
and the supposedly better option can turn out to be suboptimal. Making
compromises requires being willing to compromise — not clinging to a
single approach in a quasi-religious way.

Therefore, an **open dialogue** is better. Other developers may have
ideas or knowledge that lead to better decisions. It’s not about
persuasion — it’s about dialogue that leads to shared, and ultimately
better, decisions.

Other developers may have ideas or knowledge that lead to better
decisions.
{: .callout }

That requires everyone involved to be willing to engage in such a
dialogue — not just push their own egos. Architects need to **foster
such conversations** and deal constructively with disagreement or
resistance, rather than ignoring it.

What applies to architects also applies to other technical
professionals: at a certain seniority level, they must engage in
discussions with others and share their knowledge and ideas. Only then
can they have an impact beyond their direct personal
involvement. Simply opposing others is not enough.

## Management?

At first glance, architects seem to primarily talk to developers and
other technical people. But software projects involve many
stakeholders who define requirements and provide valuable input — so
they must also be included in the dialogue.

Software projects involve many stakeholders - they must also be
included in the dialogue.
{: .callout }

In addition, management and other stakeholders often make decisions
that affect projects. This includes direct **architectural decisions**
— such as which technology to use or whether to adopt an approach like
microservices. Ideally, such decisions should be made by architects,
since they are the experts. Management’s involvement in these
decisions is therefore somewhat contradictory — they are not the
experts and should defer to those who are.

Management also makes decisions about **team setup** and **team
responsibilities**. Since Conway’s Law, we know that organizational
structure affects architecture. Yet such organizational decisions are
often made by management without considering architectural
implications.

In practice, many architects treat these decisions as fixed and
unchangeable. Sure, they are made by people higher up the hierarchy —
but you can still talk to those people and influence their
decisions. Just as architects should engage in **dialogue** with
developers, they should do the same with management.

Just as architects should engage in dialogue with developers, they
should do the same with management.
{: .callout }

Of course, it can be convenient to let others take responsibility for
decisions. But at the very least, architects should provide
feedback — especially when they have unique insight. That feedback helps
improve decisions overall.

Sometimes, decisions need to be "translated": management may not
understand how organizational structures influence
architecture. Likewise, management doesn’t care about the "beauty" of
code, but they do care about development efficiency. As an architect,
you need to perform this translation if you want your ideas to be
heard.

## Dimensions of Effectiveness

There are thus two dimensions of impact: based on your knowledge and
skills, you can design better or worse **architectures** — but whether
they are actually implemented depends on how effectively you operate
within the **organization**. Both dimensions must be considered when
making decisions.

It can even make sense to choose the option preferred by the majority,
even if it’s technically inferior to the one you would choose
yourself. That option will likely receive more support. And in many
cases, the different options don’t lead to dramatically better or
worse outcomes. It might even be that your preferred option only seems
better to you but is in fact worse. Software architecture is complex,
and the consequences of decisions are often impossible to fully
predict.

On the other hand, when decisions could have catastrophic
consequences, you must speak up and escalate if necessary. It would be
completely irresponsible to let such decisions go unchallenged. The
first step is not to treat decisions — especially those made by
management—as immutable truths.

It’s crucial to prioritize which decisions to "push through" or firmly
resist.
{: .callout }

Thus, it’s crucial to prioritize which decisions to "push through" or
firmly resist, and which to approach by focusing on communication and
collaboration.

## Conclusion

Designing architectures and selecting technologies are prerequisites
for successful architectural work — but they’re not enough. To make an
impact, architects must communicate with developers. The goal isn’t
necessarily to impose one’s own ideas but to engage in dialogue,
question those ideas, and revise them if needed. Writing code can
help, but communication skills are far more important.

The same applies when dealing with management and other
stakeholders—these skills are essential for influence. Without the
ability to create impact, even the best architectural designs will
never be realized. That’s why [communication is so important in
IT](https://software-architektur.tv/2024/08/16/episode228.html). And
there are, of course, [many
ways](https://software-architektur.tv/tags.html#Kommunikation) to
improve these skills — for example, through [facilitation
techniques](https://software-architektur.tv/2024/10/04/episode234.html).

*This is a translation of my [German article at Java
Magazin](https://entwickler.de/reader/reading/java-magazin/4.2025/2f30e08fa9bd5efa002644f3).*
