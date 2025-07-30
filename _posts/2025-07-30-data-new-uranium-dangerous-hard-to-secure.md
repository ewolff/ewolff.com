---
title: "Data Is the New Uranium: Dangerous and Hard to Secure"
layout: blog
description: Software developers and software architects must handle data with great care. Otherwise, they create risks no one can fully assess.
tags:
- Data
- Security
---

At the end of last year, a [data
scandal](https://www.theregister.com/2025/01/06/volkswagen_ev_data_exposed/)
involving Volkswagen (VW) made headlines: the VW Group collects and
stores location data from many of its vehicles. Due to a
misconfiguration in Spring Boot, it was possible to generate a heap
dump of an application via a specific link. This application had
access to the cloud storage containing the location data. The heap
dump included the secrets needed to access the data — enabling
attackers to download it.

What can we learn from this? The obvious conclusion is: public-facing
applications must be properly secured. While true, the
[presentation](https://media.ccc.de/v/38c3-wir-wissen-wo-dein-auto-steht-volksdaten-von-volkswagen)
at the Chaos Communication Congress taught me something even more
important: knowing a car's past locations can reveal very sensitive
information. Suppose a car regularly parks at an intelligence agency
like the German BND, then spends nights at a specific residential
location, and occasionally appears at a brothel's parking lot. That's
valuable intelligence. It could likely be used to blackmail an easily
identifiable intelligence officer. In total, 800,000 vehicles were
affected in this scandal, and around one terabyte of data was exposed
— plenty of opportunity to extract highly valuable information.

These problems are older than digital computers. The Netherlands built
a population registration system. After invading, the Nazis used that
[data](https://digital.kenyon.edu/bulmash/1406/) to deport all Jewish
people.

## Protecting Data Alone Isn't Enough

Data that has the potential to blackmail intelligence personnel are so
valuable that intelligence agencies will go to great lengths to
acquire them. And IT systems can't be fully protected against such
adversaries. A prime example:
[Stuxnet](https://en.wikipedia.org/wiki/Stuxnet), the cyberattack
targeting Iranian gas centrifuges used in uranium enrichment. It
exploited several unknown Windows vulnerabilities (so-called zero-day
exploits). You can't defend against such attacks — because the
vulnerabilities are unknown, there are no countermeasures. So even
nuclear facility systems are vulnerable, which are probably not
connected to the internet and have tightly controlled physical access.

Even the data of the German parliament hasn't been safe from [Russian
hackers](https://cyberlaw.ccdcoe.org/wiki/Bundestag_Hack_(2015)).

VW didn't secure their data properly. But even if they had, it would
only have made access more difficult — not impossible. If an
intelligence agency wants that data, they'll get it.

And let's be honest: VW is unlikely to be the only company collecting
such data. Tesla, for example, [gathers telemetry and video
data](https://apnews.com/article/tesla-las-vegas-explosion-cybertruck-elon-musk-789dc864a0c138fd7c36ca8c94b0fbfd). This
data is accessible to a person some regard as the [new hero of the
far-right](https://www.wired.com/story/far-right-new-leader-elon-musk/). Other
manufacturers store data in authoritarian countries — which is hardly
ideal either.

## You Can't Fully Protect Data

But let's assume the data isn't in bad hands already, and the only
issue is keeping it safe. The example of cryptocurrencies shows how
difficult that is. Anyone with a private crypto key can access the
associated funds — whether they have a legitimate claim or are
stealing them. That's why such keys must be very well protected. Yet
there's a [website](https://www.web3isgoinggreat.com/) that
continuously reports massive crypto losses — often in the millions,
and once even [$1.5
billion](https://www.web3isgoinggreat.com/?id=bybit-hack). Even when
real money is at stake, data can't be adequately secured. Intelligence
agencies are active here too: North Korea [finances its
dictatorship](https://edition.cnn.com/2025/02/24/politics/north-korean-hackers-crypto-hack/index.html)
and its [nuclear weapons
program](https://apnews.com/article/technology-crime-business-hacking-south-korea-967763dc88e422232da54115bb13f4dc)
through crypto theft.

## Privacy by Design and Datensparsamkeit

So, securing data isn't the solution. That leaves only one option:
don't collect or store the data in the first place. This is where
[privacy by design](https://en.wikipedia.org/wiki/Privacy_by_design)
and
[datensparsamkeit](https://martinfowler.com/bliki/Datensparsamkeit.html)
come in: before storing data, we must ask which features require it
and only store what's truly necessary. For example, if you want to
locate your car, all you need is its current location. There's no need
to store historical location data. You could even ping the car only
when requested, retrieve the current location and never store any
data at all. At first glance, it's unclear why a company would need to
store a car's entire movement history.

Users could also be asked whether they want certain features enabled
in the first place. An intelligence agency like BND, for example,
might prefer to forego convenience features rather than risk exposing
their agents. Others may choose differently. But if companies never
ask clearly, store the data by default and hide the opt-out, users
are stripped of the ability to make meaningful choices.

Above all, we need to abandon the idea that "data is the new oil."
That mindset makes stockpiling data for later analysis seem
logical — and leads directly to scandals like VW's.

We see similar risks elsewhere: do we really want to collect all
Germans' health data and make it centrally accessible? How valuable is
that data — and [can we actually protect
it](https://www.heise.de/en/news/38C3-Major-security-flaws-uncovered-in-electronic-patient-file-3-0-10221396.html)?

There are, however, positive examples: the [German
Corona-Warn-App](https://en.wikipedia.org/wiki/Corona-Warn-App)
focused only on contact data and used a decentralized
architecture. Even the German hacker organization Chaos Computer Club
rated it [“very
good”](https://www.tagesschau.de/inland/coronavirus-app-107.html).

## So What Now?

Software developers and architects need to consider the implications
of the data their software collects. Before the VW hack, I hadn't
realized how valuable such data could be to interested parties. And
that's despite the fact that [smartwatches have already revealed the
locations of military
bases](https://www.newsweek.com/fitness-app-strava-reveals-location-secret-military-bases-around-world-793442)
in the past.

Development teams must always ask themselves: do we need to collect
this data at all?

In the U.S., DOGE (Department of Government Efficiency) has gained
[access to large quantities of
data](https://ash.harvard.edu/resources/understanding-doge-and-your-data/). The
public is reassured with claims that it's "read-only" access. But this
reveals a stunning naivety about the value of data. DOGE's [own
website](https://arstechnica.com/tech-policy/2025/02/doges-gov-site-lampooned-as-coders-quickly-realize-it-can-be-edited-by-anyone/)
was extremely insecure. Its staff fail to protect [even their own
data](https://www.businessinsider.com/doge-nasa-google-calendar-public-2025-3). So
it is not clear whether the plethora of data DOGE has access to is
actually safe.

Also it is worth asking what happens when stored data becomes publicly
accessible online — or falls into the hands of extremists or an
undemocratic government.

## tl;dr

Data is only truly secure if it's never collected or
stored. Development teams should therefore store only the data that is
absolutely necessary.

*This is a translation of my [German blog post at heise
Developer](https://www.heise.de/blog/Daten-sind-das-neue-Uran-Gefaehrlich-und-schwer-zu-sichern-10318961.html).*
