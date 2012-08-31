---
layout: post
title: Walls are an important part of success
tags:
- workflow
- devops
- process
---


### Patterns

1. *Production is sacred, giving developers any access is too dangerous.*
1. *The Ops team has its own set of goals and priorities, that are separate
   from the dev teams.*


---

### Story


(**Editor's Note:** *In order to preserve the anonymity of my sources, the
company shall be referred to as "Secret Company Organization", or "SCO." And I
will pick a random name for ops engineers, such as "Daryl."*)


Prior to working for SCO, Daryl had several "less than ideal" encounters with
app developers. Developers who would check code into CVS without building it,
let alone testing it. The kind of app developers that always seemed to break
anything and everything they touched. In order to operate effectively, Daryl
had to protect his production infrastructure from the application developers.

When Daryl joined SCO and was tasked with building out infrastructure for new
products, and began assembling a team of bright Ops people and made sure that
the service was managed well, From his years of experience, Daryl knew that
part of "well managed" meant keeping application developers away from
production, lest they somehow ruin everything.


After months of keeping those pesky app developers in check, Larry, the head of the
dev team, came to Daryl with a question:

> "The support team is seeing some data corruption for a small percentage of
> users, we think there's a race condition but we haven't been able to
> reproduce it locally. We need live access to production logs to try ot
> pin-point how this issue is occuring"


Daryl had seen this kind of subterfuge before, fat chance these app developers
were getting access to **live** logs from production! "File a ticket with the
patterns to look for and a time range, and I'll have one of my
guys pull some log data for you next week."


Frustrated, the dev team played this game of "ticket ping-pong" for about three
weeks before finally finding the issue, an improperly cleared cache value by the
application was being used before requests. Daryl knew the issue was in the
application, those devs always seemed to be screwing something up. His belief
that production needed to be protected from the dev team was stronger than
ever.


Larry learned a valuable lesson too, Operaitons was not going to cooperate, no
matter how much he kicked and screamed.

The following year, Larry was tasked with building out a brand new application.
Having worked with Daryl before, Larry decided to use a hosted service (such as
[Heroku](http://www.heroku.com)) for the development of the new app. He was
able to afford it under the dev team's budget, and the setup allowed the dev
team a *lot* more insight into the production environment. If they wanted a new
database table, it was there, if they wanted to tail production logs, they
could, everything was at their fingertips!

The new application was launched faster than expected, Larry's team was
applauded and he was ultimately promoted.


The wall between Dev and Ops teams was so high and so thick that the new
application was managed by the devs and ran for almost a year before the
"Operations team" found out about it.


The business ultimately failed (for multiple reasons).

