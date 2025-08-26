---
title: "Designing Models Together - Collaborative Modeling"
layout: blog
description: At first glance, designing a software system seems like a purely technical task. In reality, however, it requires collaboration among different roles to build a shared understanding. This involves not only shaping technical artifacts but also social processes.
tags:
- Domain-driven Design
- Collaborative Modeling
---

Software development is, at its core, the creation of models: Code
models reality and business logic. If an insurance premium needs to be
calculated, the code performs this calculation and thus models the
insurance’s business logic. Besides code, there are various other
models. These include formal models such as UML (Unified Modeling
Language), which can be used to model many different domains. UML is
formal because every element has precise, fixed semantics. This has
been leveraged, for example, in generating code from UML. Naturally,
there are also informal models, which we use spontaneously to discuss
software collaboratively. These models are particularly useful for
informal communication.

Ultimately, informal models must at some point be transformed into
formal models. For software to run, at least one formal model must
exist — the code. Like UML, code has a clear semantics, defined by the
programming language used. Creating code is the responsibility of
technical people. Typically, they can also express themselves well with
other formal models, since they can transfer their programming
knowledge to these.

But in order to write code and create other formal models, they need an
understanding of the business logic. That’s where domain experts come
in. They know how the domain is structured and which domain logic must
be implemented. However, they are usually not able to write code, and
other formal models may also be difficult to understand for them.

## Collaboration

Therefore, technicians and domain experts must agree on a shared model
to express their understanding of the domain. This allows knowledge to
move from the heads of domain experts into those of technicians, and
eventually into formal models such as code.

In this context, communication becomes the primary focus of
models. Event Storming has established itself as a technique here:
Domain experts write events that happen in the domain on orange
Post-its and arrange them on a timeline, often on a wall. The benefit
of this technique is its low barrier to entry. No complex formal
models need to be understood — simply writing Post-its suffices to
informally express logic.

Other techniques work in a similar way:

- Specification by Example captures example processes or values from
  the domain. This concept is closely related to Behavior-Driven
  Design (BDD). One describes what happens in the domain under certain
  conditions. These scenarios can be expressed in natural language
  while following a defined structure, making them executable as
  automated tests. Tools such as [Cucumber](https://cucumber.io/)
  support this approach.

- Spreadsheets can also serve as inputs for such modeling. For
  example, a spreadsheets might calculate the interest rate for a loan
  depending on credit rating, term, and other parameters. Such
  spreadsheets can be created with familiar tools like Excel, then
  read and parsed by tests to verify the implemented code against
  these requirements. This way, domain experts can use tools they
  already know to express logic.
  
These models are not informal. They are clearly formal enough to be
executed as tests — just like code.

It is not uncommon for domain experts to work with formal
languages. Machine operator program CNC machines. Office workers use
Excel, often with complex macros. BPMN (Business Process Model and
Notation) can also be used by domain experts. Business processes are
modeled in this formal language and thus made executable by
computers. While domain experts may not be able to create BPMN
diagrams themselves, they can often understand them and collaborate
with technical people to create them.

Domain experts can even be provided with DSLs (Domain-Specific
Languages) to express their logic. For instance, a DSL could be
created for modeling tax calculation rules, enabling the development
of systems for tax filing and consulting.

The way collaboration around models is organized defines the
development process: With Event Storming, technical people learn about
the domain logic and then implement it in code. With DSLs, developers
create tools that let domain experts express the logic in code
themselves. This is a sociotechnical perspective: Depending on the
division of work, systems can be implemented in very different ways.

## Sociotechnical Influences

There is another sociotechnical dimension: These models primarily
facilitate communication. Event Storming, for instance, has many
advantages here. Writing Post-its and sticking them on a wall is
something even introverted people can do. Multiple people can work on
the model in parallel. This enables a different style of collaboration
than a classic meeting, where one person — or only extroverts — are active
while others remain passive. Model quality and shared understanding
benefit greatly from the active involvement of as many participants as
possible. Because these models explicitly foster collaboration, we
speak of collaborative modeling.

Practices from this approach can be carried over into other
meetings. Post-its, for example, can also play a role outside Event
Storming. Of course, there are many other ways to structure group
collaboration so that more people actively contribute their
knowledge. One example is Liberating Structures. Collaborative
modeling is just one concept among many to strengthen collaboration.

## Social Relationships

In such meetings and design sessions, something else becomes visible
beyond the artifacts themselves: How people collaborate in context,
where knowledge silos exist, and what social interactions in this
environment look like. Since collaboration is often at the core of
project challenges, these insights can be very valuable for project
success.

It is especially important to look not just at the artifacts but also
at the process of creating them. Certainly, artifacts contain
knowledge about the domain and thus important information. But perhaps
we overvalue them compared to the insights gained into social
structures, the practice of collaboration and communication, and the
knowledge exchange that happens during artifact creation. For example,
collaborative modeling reveals who understands which part of the logic
or which people enjoy working together.

Thus, models have more than just the dimension of formal
or informal. They can also either support or hinder collaboration and
communication. Event Storming, for instance, enables parallel,
interactive work with minimal effort. Many people can simultaneously
contribute to different parts of the model and discuss their
ideas. Textual models may not be as strong in this regard. But even
with textual models like code, collaboration is possible — for example
through pair programming. Whole groups can even work on code together,
with one person at the keyboard and the others discussing the next
steps — this is called ensemble or mob programming. Different
collaboration models can therefore be implemented with different
artifacts like code, or requirements.

Modeling thus has not only a technical aspect but also helps establish
social systems such as pairs or ensembles. These systems foster
knowledge exchange and joint work. In fact, whether a specific piece
of information is captured on a Post-it may be less important than
knowing who wrote it and who to approach for further details. Perhaps
that conversation already happened during the modeling session, making
further collaboration easier. In that case, the social impact of the
modeling session is crucial. Modeling must therefore be seen as a
sociotechnical activity.

Agile software development has long followed a similar principle: The
goal of a story was never to document every detail but to enable later
conversations about functionality. Collaborative modeling can likewise
be used to establish and prepare communication pathways.

## Conclusion

Collaborative work on models — including code — is a central
activity in software development. There are many different models
intended to support developers in coding. But working on models
collaboratively ensures that everyone is involved in shaping
them. This not only improves the quality of the models but also
fosters collaboration. This aspect is what makes collaborative
modeling special, while other approaches tend to focus only on
artifacts and the knowledge captured in them.

*This is a translation of my [German article at Java
Magazin](https://entwickler.de/reader/reading/java-magazin/3.2025/6f24108c52d9b4fbb0fe809a).*
