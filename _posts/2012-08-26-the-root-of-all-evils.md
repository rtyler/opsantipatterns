---
layout: post
title: Accidental censorship with DNS
tags:
- dns
---

### Pattern

1. DNS as a global system is straight-forward and tolerant to mistakes


---

### Story

(**Editor's Note:** *Unlike [our last
story](/2012/08/19/tear-down-this-wall.html), this one has no need for
anonymization, since your editor was the one who screwed up here.*)


For various reasons, I decided to move registrars which included moving a lot
of domains, including the most important one I manage:
[jenkins-ci.org](https://jenkins-ci.org).

For domains whose root DNS servers were managed by another service other than
the registrar, things went relatively smoothly. One by one, I moved domains
over over the course of a couple afternoons, to make sure that everything went
swimmingly in the lead up to "the big one."

When it came time to move `jenkins-ci.org` over, I followed the same procedure
I had been using before. Yes the registrar also ran DNS for this domain, that
shouldn't matter though, that's a separate "service" offered by the registrar,
this should work just fine!

After making the changes, and noticing that the domain wasn't responding
correctly, I carefully read over the instructions for migrating this domain and
noticed there was a mention of a special step for "domains using the hosted DNS
service."

As luck would have it, when the domain was marked as "moved" in registrar it
also removed the NS records for the domain, effectively letting
`jenkins-ci.org` go dark for about 48 hours while the registrar transfer
process completed.

Within about 15 minutes of realizing what had happened, the panic set in. The
level of frustration increased when I was informed that having the domain online was
a pretty important part of the development process, and the blackout was
causing all sorts of troubles for developers.


I was able to provide a work-around to developers within less than an hour by
using Puppet to quickly provision a new authoritative nameserver, something we
didn’t have before. When the dust finally settled, the positive that came out
of the experience was that we ended up with DNS fully under our control, and
project contributors can add new CNAMEs and A records by simply updating our
Puppet repository.


Whenever dealing with DNS read the documentation and check, double check, sober
up, then check again; only then should you make major changes.
