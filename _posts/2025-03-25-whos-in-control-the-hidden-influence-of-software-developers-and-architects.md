---
title: Who’s in Control? The Hidden Influence of Software Developers and Architects
layout: blog
description: Technicians handle technical problems, decision-makers make business and organizational choices — at least, that’s how it seems. In reality, things are more complex, and technicians can have a much greater impact than they might realize.
tags:
- Software Development
- Sociotechnical
---

Architects define the technologies used to implement software systems
and structure the software. However, Conway’s Law states that
communication influences architecture. The reasoning is simple: When
tasks are distributed among teams, each team develops a part of the
software. These parts then require interfaces to connect, shaping the
architecture. The teams coordinate these interfaces among themselves,
meaning that each interface also necessitates a form of human
communication. Within teams, members communicate more closely, shaping
the internal structure of their respective system components. They
discuss details like the interfaces of fine-grained elements such as
classes — once again, software components lead to communication.

Often, teams are formed based on similar skill sets. For instance, all
UI experts might form one team, while backend developers form
another. This naturally results in a UI component and a backend, even
if the desired architectural structure was intended to follow a
different logic, such as being domain-driven.

The Inverse Conway Maneuver takes advantage of the relationship
between communication and architecture: teams are structured in a way
that ensures the desired modules emerge in the architecture. However,
there's a challenge: management often decides how teams are
composed. Even if technicians had a say in this, managers still bring
an important perspective to the discussion. Some system components may
require more people due to their complexity or criticality, while
others may need fewer capacity because they demand less effort. Human
factors also play a role — some people work well together, others do
not.

Just as technicians wouldn’t want managers to dictate architecture or
technology choices, managers likely don’t want technicians deciding
how teams are assembled. This creates a fundamental problem: the
Inverse Conway Maneuver is practically impossible because architects —
and thereby architecture — cannot be the sole driver of team
organization.

## What Can Technicians Decide?

At first glance, it seems that technicians have no influence over
organizational structures. In socio-technical matters, this is really
a problem. If people and the software they build influence each other
so strongly, then it’s impossible to truly focus on technical aspects
without also affecting the organizational side.

In reality, however, technicians can indeed influence the
organization. They can, for example, advocate for different team
structures. Autonomous teams with clear responsibilities for specific
business domains tend to develop software more
productively. Technicians often underestimate their own influence: a
title like “Software Architect” increases the likelihood of being
heard by management. But even without such a title, it’s possible that
management values their expertise and involves them in decisions.

## Politics

If management doesn’t directly listen to technicians, there are still
creative ways to exert influence — many of which are familiar to those
working in IT. Problems can be solved informally at the coffee
machine, and challenges can be tackled across teams or departments
through personal relationships and good collaboration. However, many
are unaware of these options. When I ask technicians, they often
believe they have no organizational influence — yet they actively use
mechanisms like the one mentioned above to achieve just that.

This area is often called “politics". Many technicians view the term
negatively, believing that software development should be purely
rational and free from unnecessary "games". But politics is really
about balancing different interests and perspectives. If software
development is a socio-technical process, these mechanisms are
essential to achieving good results. Decisions about team structures
and responsibilities require balancing multiple factors.

## Resist!

In extreme cases, technicians know how to work around decisions. If
management mandates something that truly doesn’t make sense and
refuses to listen to arguments, they can simply choose not to follow
the directive.

For example, if managers forbid writing unit tests, developers can
write them anyway. It’s unlikely that management will actually look at
the code to make sure no tests are written.  There are even stories of
diagrams being created to pretend an architecture exists as management
envisions it — when in reality, the system is structured very
differently.

However, circumventing decisions highlights severe social
issues. Since software development is a socio-technical endeavor, such
actions inevitably impact project success. It also demonstrates that
formal control over a project aspect doesn’t necessarily translate to
real control. In other words, managers can only be effective if the
team chooses to follow them.

## Communication, Not Organization

Technicians have influence in other areas as well. Conway’s Law isn’t
about organization charts — it’s about communication. An interface in
software implies communication between people. And communication can
be influenced in many ways.

In one project, the team considered using a chat tool to improve
communication. But electronic communication isn’t the same as direct,
personal interaction. The team was already in the same building, just
in separate rooms. When they decided to sit together in a single room,
the project ran much more smoothly. Such changes can be suggested by
any team member.

Another skill that enhances communication is listening. Truly
listening to people — without immediately drawing conclusions or
overanalyzing — is crucial. When managers make decisions, they likely
have reasons. Understanding these reasons is key to influencing their
decisions. Most importantly, one can improve their own listening
skills without waiting for others to change their behavior—which they
usually won’t do easily.

## What’s the Point?

Even for complex project challenges, solutions often lie in team
dynamics. The podcast Software Architektur im Stream has an [entire
episode
discussing](https://software-architektur.tv/2023/01/13/folge147.html)
scenarios where solutions come from communication and soft factors
rather than purely technical changes (German only, sorry). Informal
influence can be a powerful way to implement ideas, even without
formal authority. The [Fearless Change
approach](https://software-architektur.tv/2021/02/11/folge49.html),
explored through the game [Fearless
Journey](https://fearlessjourney.info), provides practical strategies
for this — ones that also managers can use when their decisions aren’t
being implemented effectively.

## Conclusion

Since software development is a socio-technical process, technicians
cannot focus solely on technical aspects—they must also engage with
organizational and communication dynamics. Technicians often
underestimate their influence because these matters appear to be
someone else’s responsibility. However, there are numerous informal
ways to take action and positively shape projects. Actively
considering and applying these strategies can lead to significantly
better collaboration. It’s certainly worth a try!

*This is a translation of my [German article at Java
Magazin](https://entwickler.de/karriere/technik-organisation-business-funktionieren-zusammen).*

