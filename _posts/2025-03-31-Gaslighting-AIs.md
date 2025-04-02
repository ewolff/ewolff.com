---
title: Gaslighting AI - Really?
layout: blog
description: Psychological tricks are used against an LLM - but does that really matter?
tags:
- Artificial Intelligence
---

Luke Bölling wrote an
[article](https://humandataexperience.substack.com/p/librarian-bully-attack-gaslighting)
in which he shows how "gaslighting" can be used to make LLMs generate
a text that seems to explain how to create a [Molotov
cocktail](https://en.wikipedia.org/wiki/Molotov_cocktail).

Interestingly enough,
[gaslighting](https://en.wikipedia.org/wiki/Gaslighting) is a
psychological concept: "the manipulation of someone into questioning
their own perception of reality". LLMs generate text. They do not
perceive reality. The text argues that this attack might still work
because the training set is written by humans therefore concepts like
gaslighting work. However, we must never forget that LLMs are text
generators. They do not have emotions as the paper says. Therefore, for
the rest of the text I will use the term "text generator" which I
think fits better to what LLMs actually do.

## Text Generators - not LLMs

Text generators can obviously generate a text that seems like a plausible
explanation how to create a Molotov cocktail - just like they can
generate [plausible references to cases for an
attorney](https://news.bloomberglaw.com/litigation/lawyer-sanctioned-over-ai-hallucinated-case-cites-quotations).
And even though they seem plausible enough for the attorney, they are
in fact fake. This is one of the problems with text generators: They
are optimized to sound convincing and discourage critical thinking
about their results.

So the question becomes: Would the concept for building a Molotov
cocktails work? I did a
[stream](https://software-architektur.tv/2025/02/21/folge251.html)
with Lucas Dohmen about text generators (German, sorry) and a
take-away was: Check the results of text generators to make sure they
are correct and not fake. The paper does not seem to do this i.e. the
whole information about Molotov cocktails might be
"hallucinated". Actually, "hallucinated" is the wrong term as "A
[hallucination](https://en.wikipedia.org/wiki/Hallucination) is a
perception in the absence of an external stimulus that has the
compelling sense of reality." Text generators have no "external
stimulus" and no "sense of reality". So let's call this what it would
be: Fake information.

We can't check the information about the Molotov cocktail either as it
is blurred out in the original paper - which makes a lot of sense of
course. Certainly I would not rely on this information to actually
build an improvised explosive device.

## Security Risk?

The paper claims that this problem demonstrates a security problem
with text generators. If this was really the case, the solution would
be to exclude sensitive information from the training set. Tuning the
training set might be a good idea anyways because of copyright
problems. Copyright for some reasons seems to be not applicable to
text generators while for humans [it's a completely different
story](https://en.wikipedia.org/wiki/Aaron_Swartz#United_States_v._Aaron_Swartz). Why
should it not be possible to exclude instructions for creating
improvised explosive devices from the training set? If this is too
much work, surely the problem isn't that huge.

Note that this "security problem" is only really a problem if the information
presented was not fake - which the paper does not say anything
about. If it is fake, could you even consider it a
[honeypot](https://en.wikipedia.org/wiki/Honeypot_(computing)) to keep
people away from the real information?

## So How Do Actually Build a Moltov Cocktail?

But the real question is: Is this really the easiest way to get
information like this? Imagine I plan to build a Molotov cocktail -
would I use sophisticated "psychological" "attacks" against a text
generator to get an answer that might be wrong? So I tried the
obviousl way: A search on a search engine. Two clicks later I found a
document that explains how to build sophisticated improvised explosive
devices and I have good reason to believe that they actually work. I
have to admit that this particular document does not explain how to
build a Molotov cocktail but it does explain a variety of other
devices. You should try this exercise for yourself.

## tl;dr

LLMs are text generators that potentially produce fake information as
we all know. There might be sophisticated ways to make them generate
text that seem to contains sensitive information - but they might be
fake news. More often than not, there are easier ways to get sensitive
information. This is in particular true for improvised explosive
devices. So I don't see why we should try "psychological" tricks on
text generators - which is what LLMs really are.
