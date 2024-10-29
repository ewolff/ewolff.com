---
title: AI in Software Development - Overhyped
layout: blog
description: The end is near — AI will soon take over all software development! This is an exaggeration that shows how little we understand what software development is truly about.
tags:
- AI
- Software Development
---

First off, AI helps generate code. This is undoubtedly a significant advancement that will change a lot. Anyone can try the numerous tools and see how powerful they are.

## Software development is not about generating code!

It may sound paradoxical, but writing code isn't the main challenge in
software development. The real challenge is figuring out which code
needs to be written. For that, you need clear requirements. However,
in practice, requirements are often too vague to successfully develop
software from them. Even when they seem clear, misunderstandings often
arise later in the process. This is why interacting with domain
experts is crucial. Developers need to learn enough about the domain
to create software that addresses the right business challenges.

Additionally, requirements tend to change. As the software is
developed and used, users and domain experts reflect on how they
interact with the software, leading to new requirements. Developers
must be part of this process to understand what needs to be
built. They can also provide feedback whether requirements are
especially easy or difficult to implement, or if changing them could
significantly simplify the solution.


## Problem: People

The importance of human factors is already apparent in the area of
requirements. But humans are central to the entire process: software
development is a team effort. A team usually includes several
developers but also other roles such as UX experts, architects, or
product owners (POs). As a result, communication plays a key role:
tasks need to be distributed and organized. And the organization
impacts the software itself: Conway's Law states that the architecture
of a system mirrors the communication structures of the team. Since
the social structure has such a strong influence on development, this
is where the main challenges lie — and AI cannot help with this.

One might imagine that AI could increase productivity so much that a
single person could replace an entire team, making human factors less
important. This seems unlikely. And interaction with people to clarify
requirements is still necessary. Besides, productivity improvements
existed long before AI tools. But instead of shrinking teams, software
teams subjectively seem to be growing to build even more complex
systems and cover more business areas. If this trend continues, we will
build even more complex systems with AI and we will not decrease the
size of the teams.


## AI: Just Another Level of Abstraction

Simplifying code generation isn’t new. In fact, there’s a long history
of technical innovations aimed at simplifying software
development. Typically, these innovations elevate development to a new
level of abstraction. Software development began by writing binary
code directly into the computer’s memory. Then, assembly languages
defined commands corresponding to binary codes but were easier to
remember and understand. This abstracted away the binary
code. High-level languages introduce concepts that abstract from
assembly, making it even easier to express algorithms and logic. At
the same time, many tasks moved to the infrastructure: operating
systems and databases now handle persistence, memory, and process
management. Libraries and frameworks offer ready-made solutions for
common functionalities at the code level. And the cloud abstracts over
many infrastructure elements like databases or servers, making it
easier to implement infrastructure for projects.

AI is the next step on this journey. The progress is so impressive
that we can confidently call it a new level of abstraction. There are
prototype tools like [GPT Engineer](https://gptengineer.app/) that can
build entire applications based on specifications and ask clarifying
questions when requirements are unclear. But as mentioned earlier,
software development with clear requirements isn’t the problem. So AI
simplifies the less challenging part of software development, not the
core.

## AI-Generated Code Is Only Seemingly Better—and That's Dangerous

AI even poses risks: a [study](https://arxiv.org/abs/2211.03622)
evaluated how developers write security-relevant code and found that
those using AI tools rated their solutions as more secure than those
without. But in reality, the opposite was true: their code was less
secure. This is clearly dangerous: software development is not just
about generating code; the goal is to solve a
problem. Security-relevant software with security flaws creates new
problems instead of solving them. The gap between subjective
assessment and objective reality can be devastating: believing the
software is secure when it isn't can have serious
consequences. Security vulnerabilities, unlike functional or
performance issues, aren't immediately obvious, so the damage can
occur in secret. Managing such risks and designing solutions that
offer qualities like security are also tasks AI can hardly solve.


## Reading Code: More Important Than Writing

Another issue: it’s not just about generating code, but modifying
it. Developers need to read and understand existing code to make
meaningful changes. Obviously, code is written once but modified and
read multiple times. Therefore, the biggest optimization potential
lies not in one-time code generation, but in reading, understanding,
and modifying it, which happens far more often. AI can help here as
well: you can ask tools like ChatGPT to explain code, at this point in
time typically small snippets. But the potential is enormous: for
legacy code, an AI trained on a specific system could be an
interesting tool to improve system understanding and make changes
easier.

## tl;dr

The problem in software development isn’t generating code, but
understanding what needs to be implemented. AI’s productivity benefits
don’t solve this problem. AI will significantly change software
development, but it won’t address the core issue.

*This is a translation of my [German blog post at heise
Developer](https://www.heise.de/blog/KI-in-der-Softwareentwicklung-Ueberschaetzt-9336902.html).*
