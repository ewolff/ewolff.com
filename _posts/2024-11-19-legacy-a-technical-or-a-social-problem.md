---
title: Legacy - A Social or a Technical Problem?
layout: blog
description: Legacy software is old, unmaintainable software — clearly a technical issue. But it’s worth looking at this problem from a social perspective as well.
tags:
- Legacy
- Sociotechnical
---

Sociotechnical approaches are currently a hot topic in software
development. While hypes often mean exaggeration, there's usually
something valuable to learn at the core. This posting explores whether
these approaches make sense to deal with legacy system.

First, we should ask why legacy is such a problem. The main challenge
is poor maintainability, which can make any change virtually
impossible. This seems to be a purely technical problem: a poorly
structured system with complex code and few tests is, of course,
difficult to modify. So the solution seems clear: You invest in
code quality and are rewarded with software that is easier to
change.

However, in reality, things might be different. For example, there was
a case where a team identified the lack of modifiability of a system
as an issue. A review found that the system’s structure was fine, and
adequate tests were in place. The explanation? Another team had
designed and implemented the system. The current team had taken over
the system without a formal handover. As a result, the new team could
hardly navigate the code; while the structure was solid, the
underlying concepts were unfamiliar to them.

In a way, poor maintainability means that a particular team is unable
to maintain a particular piece of software. In this example, the
original team could maintain the software, but the new team could
not. While the structure and quality of tests and code play a role in
maintainability, so does something like a lack of handover.

## Sociotechnical Systems

Here, we applied a sociotechnical concept: sociotechnical approaches
view systems not as purely technical constructs but as outcomes of the
social relationships among participants. This idea stems from studies
in coal mining. One finding from this research was that the success of
an organization depends on how it functions as a sociotechnical
system, not simply as a technical system with replaceable individuals
who must adapt.

What applies to coal mining is also helpful for software development,
as the example above shows. In software projects, the individuals
involved and their relationships play a major role.

Recognizing that maintainability is a sociotechnical phenomenon has
far-reaching implications:

- Handover of software to a maintenance team has the potential to turn
  the software into legacy if no appropriate measures, like an
  explicit handover, are taken. So, one must be careful — or perhaps
  even avoid the handover by having the same team handle maintenance.
- Personnel turnover is inherently a potential problem because new
  people need to get to know the system. In extreme cases, they may
  not understand the ideas behind the system’s structure and make
  changes that don't align with its design. Thus, changes in the team
  can lead to a maintenance problem and, subsequently, to a structural
  issue in the software.
  
The strategy to resolve such issues may not involve system
improvements, but rather, the team needs to familiarize itself with
the system or the original creators must explain the ideas behind its
design and code.  One can organize sessions where the team explores
the system together or one can arrange a handover. Thus, the solution
lies on a social rather than a technical level. It would be
entirely unnecessary, for example, to invest in further architectural
improvements to an already well-structured system.

Solutions that view software as a sociotechnical system can also be
useful in other scenarios. If you want to continue developing a system
in an old programming language like COBOL, you can rewrite it in a
newer language like Java. But often, this approach attempts to address
a social problem: COBOL developers are retiring or are otherwise
unavailable. Consequently, there’s a social alternative: training
developers in the old technology. Some companies offer training
positions for IT newbies in COBOL to address the shortage caused by
retirements. For more modern technologies like Oracle Forms or Delphi,
you may be able to find developers in the job market. However, these
developers still need to learn the specifics of the legacy system,
which can take time. Nonetheless, this approach provides an
alternative to rewriting the system. Having more options to solve a
problem can only be beneficial. Whether to choose this option is
another matter. But setting a hard deadline to fully migrate the
system before the last developer retires is not particularly
attractive either. You can reasonably estimate how likely it is that a
rewrite succeeds by comparing the retirement age with the estimated
duration of the rewrite. If the rewrite is likely to take much longer,
it may not be the solution, and you may need to find people to
maintain the old system. In practice, quite some projects haven't done
this estimation but instead just hope that the chosen solution will
somehow work out.

A social strategy can also help prevent legacy: approaches like
[Behavioral Code
Analysis](https://software-architektur.tv/2023/06/07/folge168.html)
consider how the team interacts with the software. If, for instance,
only one person regularly modifies a specific part of the code, that
part would immediately become legacy if that person left the team. If
frequent changes are required, this could become a major issue.

The countermeasures should also be social: Pair Programming or
Ensemble Programming (also known as Mob Programming) ensure that
multiple people make and understand each change. Solutions like better
documentation or code quality may not be as effective; working on the
code together teaches you a lot more about the code and the system
than reading some documentation. These techniques are basically a
continuous handover of code to other developers. For reasons like
this, it’s wise to evaluate systems not only by code quality but also
by how people work with the code.

## Conclusion

Viewing software development not only as a technical challenge leads
to concrete ideas for dealing with legacy. Most developers and
technicians already rely on such approaches intuitively. Doing so more
deliberately and systematically is certainly sensible and
helpful. After all, software development is a team effort that relies
on the performance of teams—teams composed of individuals with their
own strengths, weaknesses, and experiences.

*This is a translation of my [German article at Java Magazin](https://entwickler.de/reader/reading/java-magazin/9.2024/c4ce890074919380aa4addb3).*


