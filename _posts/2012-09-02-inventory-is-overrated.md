---
layout: post
title: Inventory is overrated
tags:
- datacenter
- management
- workflow
---

### Pattern

1. Inventory is low-priority busy work.


---

### Story

(**Editor's Note:** *In order to preserve the anonymity of my sources, the
company in question will be referred to as "Excited Monkey Company", or "EMC."
And I will pick a random name for ops engineers, such as "Ryan."*)


Managing Operations at EMC was a monumental task, where most companies stress
about multiple racks in the data center, EMC stresses about multiple data
centers on multiple continents. With a centralized team at the head office
responsible for managing software and configuration, and smaller on-site teams
managing the provisioning and physical machines, the "Ops Team" was more like
an "Ops Army."

Following a period of dramatic growth and expansion, bean counters realized
that the Ops Army had a little too much money, and cut their budget.

In an effort to reduce costs, the team decided to consolidate two of their
datacenters into one. The entire organization pitched in to help plan the move,
assessing power needs, updated network topologies, service maintenance windows,
the whole nine yards!

Ryan, the engineer in charge of coordinating the entire effort was feeling
really good about the move as "D-Day" inched closer and closer. He knew that
*something* would go wrong, but felt confident that all the bases were covered,
ensuring that whatever mistake was lying in wait would be a small one.


D-Day fell on a Saturday, giving Ryan's team roughly 48 hours to take down
machines, get them loaded onto trucks and unload them into waiting racks in the
other data center.

30 minutes after the team started shutting down machines
and packing them up, Ryan got a call from a colleague asking if he knew
anything about "Service X" having service issues. Looking over his list of
affected services, Service X was nowhere to be found.

A few more phone calls later, Ryan had determined that the former datacenter
was running a *lot* more than he was led to believe.

At this point there wasn't anything to be done but finish the migration, and
hope Customer Support wouldn't have him tarred and feathered for causing
weekend-long availability issues for subsets of EMC's userbase.


With the weekend coming to a close, Ryan's team brought more and more machines
online at the new datacenter, things went pretty smooth, adequate power and
great power meant all racks were online by the end of Sunday.

Unfortunately the victory was short-lived, what Ryan had assumed was correct in
Inventory had somehow drifted from reality, how far was anybody's guess. His
team spent the next two weeks doing a full-scale audit of **every machine** in
the data center and making sure that Inventory was 100% correct.

It remains a mystery how Inventory drifted the way it did but EMC's Ops team
has a renowned focus on the correctness of Inventory.
