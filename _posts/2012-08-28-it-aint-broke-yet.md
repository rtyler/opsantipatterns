---
layout: post
title: Conservative Operations and bad red states
tags:
- upgrades
- workflow
- faulttolerance
- highavailibility
---


### Pattern

1. Any changes to a functional system will put its stability in jeopardy (also
   known as "*if it ain't broke, don't fix it*")


---

### Story

(**Editor's Note:** *In order to preserve the anonymity of my sources, the
company in question will be referred to as "Friendly Business", or "FB."
And I will pick a random name for ops engineers, such as "Mark."*)


The name of the game for FB Ops was stability and scale, if FB could keep the
service online with as many Nines as possible, everybody would make billions on
their stock options and be able to start space companies.

FB's software stack was based on Linux, and had the same version of Plebian
Linux across the entire production cluster. Striving for stability, the version
of Plebian originally used by the FB Ops team was "stable," which in the
Plebian Linux community means "older than dirt."

As weeks turned into months and then into years, Mark's team found themselves
struggling backport more and more security fixes to their ancient version of
Plebian stable. Drift became so bad that Mark's team collected an impressive
array of backported patches for everything from OpenSSH and Apache, down to
OpenSSL and glibc itself.

Plebian stable was working fine for FB, so they continued on with it because
"hey, it ain't broke!"

---

When December rolled around, Mark's team was looking forward to a nice relaxing
Christmas and New Year's holiday. The developers seemed to have stopped working
shortly before Thanksgiving (slackers) so the Ops team hadn't had much to worry
about.


Shortly after midnight on January 1st, a slightly intoxicated Mark received a
page about one host down, another host down, another host down, another host
down. The text messages were coming in too fast to Mark to care at this point,
something was *fucked*.

Mark couldn't access any of the hosts; he called his colleagues, they had the
same issue. Everything seemed to be entirely unresponsive, locked up even from
the remote consoles. Without any choice, the not-safe-to-drive FB Ops team started
rolling reboots through the datacenter of machines as fast as the crap external
consoles would allow them.


After the dust had settled and the team was able to investigate, they
discovered the root cause: a leap year bug in the kernel. Much to their dismay,
the bug had been fixed for at least a year prior, but somehow it was never
backported all the way back to the stone-age-kernel running at FB.


Fortunately for FB, most of the datacenter was back online before the
thundering herd of hungover users signed in the next day, many of which hadn't
even noticed the outage the night before.

