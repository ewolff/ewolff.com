---
title: "What Really Drives Software Architecture?"
layout: blog
description: "Quality — or non-functional requirements — is often said to drive software architecture, meaning the structure of the software and the technical decisions behind it. While this sounds plausible at first glance, a closer look reveals that the situation is far more complicated.
"
tags:
- Quality
---

It starts with terminology. Some people speak of *non-functional
requirements*, referring to the technical characteristics of a system,
in contrast to *functional requirements*, which describe the business
functionality the system implements. Today, the term *quality* is more
commonly used. It is somewhat more abstract than specific
requirements, but perhaps better captures the underlying
idea. Individual requirements can be expressed as *quality scenarios*,
which describe in concrete terms how the system should behave in
particular situations.

## Typical Quality Attributes

Every software system requires a different set of qualities because
every system solves a different problem. Nevertheless, quality models
such as ISO 25010 identify common quality dimensions. Typical examples
include:

* **Maintainability** is particularly important because poor
  maintainability can eventually make a system impossible to change,
  forcing a complete rewrite — a total loss of the original
  investment. The consequences primarily affect developers: working on
  an unmaintainable system is frustrating and can become
  demoralizing. Unsurprisingly, technical teams often value
  maintainability highly, even if other stakeholders do not.

* **Security** is usually about managing risk. Security
  vulnerabilities only become a problem if they are exploited or
  publicly disclosed. They can be introduced by only a few careless
  lines of code — or even by relying on a library with a
  vulnerability. The real question is therefore how much risk an
  organization is willing to accept.

* **Performance** can be important, but in many situations
  **scalability** matters more. A scalable system can improve
  performance by adding more resources, such as additional or more
  powerful servers.

## Achieving Scalability

Many architects believe that maintainability and scalability are the
most important qualities of a software system. Fortunately, software
architecture can significantly influence both.

Scalability can be supported by selecting appropriate technologies —
for example, cloud platforms — and by designing systems that scale
horizontally without obvious bottlenecks. If scalability later proves
insufficient, changing the system's structure or technology stack may
solve the problem through architectural changes.

However, architecture alone cannot solve scalability. A scalable
system still requires additional resources when demand
increases. Operations therefore play a crucial role. Besides providing
the necessary infrastructure, operations can also influence other
qualities such as security.

Scalability is a luxury problem.
{: .callout }

Furthermore, scalability is essentially a luxury problem. It only
becomes relevant when a system already has many users — in other
words, after the product has already succeeded in the market. Before
scalability matters, other qualities such as usability or valuable
features must attract users in the first place.

Usability, however, cannot really be achieved through traditional
architectural mechanisms. Almost any frontend technology can be used
to build either an excellent or a terrible user experience. Choosing
React over Angular — or vice versa — has little impact on
usability. Instead, UX practices determine whether users find a system
pleasant to use.

## What About Maintainability?

Maintainability also appears to be largely a technical
concern. Automated tests, a well-structured architecture, and high
code quality certainly help.

It is unrealistic to make every part of every system to the highly
changeable.
{: .callout }

Yet maintainability only matters if the software actually needs to
change. To invest wisely, developers need to know *which* parts of the
system must be adaptable. If flexible pricing is central to a
company's competitive advantage, then the pricing logic deserves
exceptional maintainability. It is unrealistic to build every part of
every system to the highest maintainability standard. Prioritization
is therefore essential.

Moreover, code quality is not the only way to achieve
adaptability. Pricing rules, for example, might be made configurable
or implemented in a rule engine, allowing business users to change
behavior without modifying code at all. In such cases, code quality
becomes largely irrelevant for adaptability.

## Do Technology and Architecture Matter at All?

Architecture can only create the prerequisites for
scalability. Whether scalability becomes relevant depends on the
product's success, which itself depends on qualities such as
usability — qualities that architecture can influence only indirectly.

Similarly, maintainability only becomes valuable when architects
understand where change is expected. Technical measures such as clean
code and testing help, but only in those strategically important
areas. If adaptability can instead be achieved through configuration
or business rules, code quality becomes much less important.

Architecture is only one part of ensuring quality.
{: .callout }

Architecture is therefore only one part of achieving the required
quality attributes.

Even fundamental technology choices may not be driven primarily by
quality requirements. Consider the choice between Java and
JavaScript. Does it determine maintainability? Other factors, such as
clean code, are often more influential. Does it determine performance?
Perhaps — but databases or other infrastructure components are
usually the real bottlenecks. Many performance problems do not
require switching programming languages, and scalable systems can
often compensate simply by adding resources.

Technology choices remain important for another reason: the team
itself. A team with years of Java experience will usually produce
better results with Java than with JavaScript. The determining factor
is therefore not necessarily the system's required qualities but the
composition and experience of the development team.

## What Should We Do?

If software quality cannot simply be achieved through architectural
decisions, how should organizations respond?

One common reaction is for architects to focus on technical qualities
such as maintainability and scalability. This makes sense because
architecture has the greatest influence on these characteristics. Yet
this focus alone may not be sufficient. A system capable of supporting
millions of users is of little value if its poor usability prevents
anyone from adopting it.

Ensure *all* relevant quality attributes are addressed sufficiently!
{: .callout }

Another approach is to consider *all* relevant quality attributes and
ensure they are addressed sufficiently. This extends beyond the
traditional responsibilities of software architects, since achieving
many qualities requires collaboration with UX specialists, operations
teams, and business stakeholders. Architects would need to coordinate
these efforts rather than focus solely on technical design.

Perhaps, in the future, quality requirements will be managed in the
same structured way as functional requirements—for example, by Product
Owners or similar roles. At least then, responsibility for quality
would no longer rest solely with architects.

## Conclusion

The common claim that quality attributes are architectural drivers is
only partially true. Many qualities depend on factors beyond software
architecture, and in many cases those other factors are actually more
influential. Conversely, even fundamental technical decisions — such as
choosing a programming language — cannot always be derived directly from
quality requirements.

Nevertheless, understanding and achieving the right quality attributes
remains essential to the success of any software
project. Unfortunately, many projects still lack a structured process
for identifying and managing quality. This stands in sharp contrast to
the disciplined treatment of functional requirements, which typically
receive much more systematic attention.

*This is a translation of my [German article at Java
Magazin](https://entwickler.de/reader/reading/java-magazin/9.2025/ef60864f86694a400730b97c).*

