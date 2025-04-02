---
title: Designing People and Teams - Same as Designing Software?
layout: blog
description: Software development projects are sociotechnical systems. They have a technical component - the software - but also a social component, the team that creates the software. Both aspects must be deliberately designed. Can the same concepts be applied to both?
tags:
- Software Development
- Sociotechnical
---

Software architecture structures software systems. Naturally,
important decisions should be documented in text: for example,
individual decisions as Architecture Decision Records or the entire
architecture using standards like arc42 or
[C4](https://software-architektur.tv/2021/01/22/folge36.html). A
popular tool that can be part of such documentation is
diagrams. Diagrams are particularly useful in discussions and often
emerge during them. This suggests that diagrams best represent how
people think about software architecture. It is no coincidence that
boxes and arrows — along with PowerPoint and Visio architectures —
hold such significance.

However, in reality, diagrams have weaknesses. When asked what the
boxes and arrows in a diagram specifically represent, the answer is
often surprising. They do not necessarily correspond to actual
structures like Java packages, JAR files, Maven or Git projects;
rather, their relationship to real structures in the code is often
unclear. This might be because diagrams reflect an ideal rather than
reality. In such cases, discussions based on these diagrams are not
particularly helpful: they do not represent the actual state of the
code. Decisions at this level become meaningless because they are not
grounded in reality and have little influence on it. Architects may
then find themselves in an ivory tower, detached from the developers’
reality at the code level.

For code, it is possible to ensure that the structures in diagrams are
actually followed. [Architectural management
tools](https://software-architektur.tv/tags.html#Architecture%20Management)
can be used for this purpose. These tools check whether the code
adheres to a predefined structure and contains only permitted
dependencies. Structuring a system in diagrams without such a tool is
pointless, as the intended structure is typically violated, making the
diagrams unreliable representations of reality. Nevertheless, software
systems can be designed to align with these diagrams. In such cases,
discussions about these diagrams are meaningful and can lead to
well-founded decisions and improvements.

## People Diagrams

There are also "people diagrams": in an organizational chart,
relationships between different teams and individuals are
depicted. Just like in architectural diagrams, there are boxes and
arrows: boxes represent people or teams, and arrows represent formal
relationships, such as authority.

As an architect, one can do with these diagrams what is done in
software: create diagrams and attempt to influence reality through
them. At first glance, these diagrams seem to better reflect reality
than typical software diagrams: unlike software, teams and individuals
are physical entities, whereas software exists only virtually as bits
and bytes. Comparing the diagram to reality seems easier because
reality appears more obvious in this case.

However, it is clear to everyone that people communicate outside of
this formal organizational chart — during lunch, at the coffee
machine, or in social activities outside of work. It is also evident
that some individuals work together more harmoniously than
others. Thus, an additional layer emerges beyond the organizational
chart: informal structures of people who collaborate effectively or,
conversely, experience conflicts and poor working relationships. These
informal structures overlay the organizational chart, influencing
whether collaboration is particularly effective or particularly
difficult.

Everyone involved in IT projects takes advantage of this: they solve
problems at the coffee machine, provide the right people with the
right information at the right time, and build trust-based
relationships within the project. Of course, these relationships cut
across the formal organizational chart: someone might know a colleague
from another project, or coincidental alliances might form. For
example, a developer and the company’s CTO might ride road bikes
together in their free time — and naturally, they may discuss
project-related topics during those rides. However, such interactions
are independent of the hierarchies in the organizational chart.

This creates a paradoxical situation: when asked who makes certain
decisions — such as team organization — people typically point to the
responsible person from the organizational chart, perhaps the
CTO. Formally, this is correct. But in reality, this person consults
with others, incorporates their perspectives, and then makes a
decision. Informal relationships play a role in this process—such as
the developer from the cycling group. The decision is not made by a
single person but rather by an informal group.

In theory, the formally responsible individual could make the decision
alone. Theoretically, this would "only" result in a lower-quality
decision because the expertise of others was not considered. However,
those individuals can undermine the decision by not implementing it or
deprioritizing it to the point where it has no real effect. Just as
architects can be trapped in an ivory tower, managers can be too: they
rely on the information they receive. Employees might even pretend to
implement a decision while actually disregarding it.

At this point, the formal organizational chart becomes inferior to
informal structures: those who can effectively leverage informal
networks likely have more influence than someone with all the formal
authority. Leaders who rely solely on formal command structures will
be ineffective because their decisions are neither implemented nor
based on accurate information.

## Paradoxes

This creates a paradox: informal networks are evident to everyone, and
everyone uses them, yet thinking still tends to focus on formal
structures, just as in software architecture diagrams. This is why
organizational charts are discussed. Other seemingly clear rules —
such as [team size
limits](/2024/10/15/the-dunbar-myth-primates-and-software-teams.html)
— are probably popular because they can be easily measured and
adjusteda. When people are accustomed to structuring architectures
based on formal criteria or evaluating companies based on numbers,
they apply the same formal concepts to organizational design. However,
they actually understand that other factors influence an
organization’s effectiveness more, as they themselves use informal
structures and are part of them.

The significance of these aspects is widely recognized: when asked
about the most important skills in IT, the overwhelming majority
mention soft skills or communication skills.

This raises an interesting question: individuals can certainly improve
their own communication skills and other soft skills — but can an
entire organization be systematically improved? This seems difficult
because people differ in their social skills and ability to interact
effectively. Improving an entire organization appears to be even more
challenging.

To answer this question, it is worth looking at other industries. In
aviation, communication was identified as an important optimization
factor in the 1970s. This realization was driven by the deadliest
aviation accident at the time, in which a Boeing 747 took off without
clearance and collided with another Boeing 747. A crew member had
asked about the location of the other aircraft, but the captain took
off anyway. Had the crew member been heard, many lives would have been
saved. While multiple factors contributed to the crash, aviation has
since recognized cockpit interaction as an area requiring
optimization.

Hierarchy plays a role in cockpit communication: there is the more
experienced captain and the less experienced first officer. This
hierarchy becomes a problem if the first officer no longer questions
the captain’s decisions — because their role is precisely to provide
checks and balances. It is dangerous when first officers fail to speak
up, and equally dangerous when captains ignore their input. To address
this, the aviation industry introduced Crew Resource Management (CRM)
to systematically improve communication and collaboration among crew
members. Pilots are trained to interact respectfully and openly to
ensure that no critical observations are ignored or dismissed.

## What Can We Do?

So it is possible to systematically improve communication and thereby
optimize collaboration. This has a greater impact on productivity and
outcomes than organizational charts. Software development is a
sociotechnical process, and the social aspect cannot be overstated.

Our industry must ask itself what we are doing beyond drawing diagrams
to genuinely improve collaboration. At first glance, there seems to be
little: developer and architect training rarely covers these topics.

However, the situation is not entirely bleak. The role of Scrum
Masters, for example, is to remove obstacles to effective
teamwork. Many architects and managers have also developed these
skills—through on-the-job experience or training. Since their roles
inherently influence organizational structure and communication,
optimizing this aspect is certainly beneficial for success.

## Conclusion

Technologists tend to structure and discuss things using
diagrams. This applies to both software and teams. While software
diagrams can align with reality, organizational charts for teams and
individuals are less important, as they are overshadowed by informal
relationships, which have a much greater impact on project
success. These informal structures can be systematically improved, as
demonstrated by the aviation industry. In our field, Scrum Masters can
address these aspects—but it is also valuable for technologists to
develop these skills themselves.

*This is a translation of my [German article at Java
Magazin](https://entwickler.de/reader/reading/java-magazin/12.2024/b6c31f2883c6c21666efcdfb).*
