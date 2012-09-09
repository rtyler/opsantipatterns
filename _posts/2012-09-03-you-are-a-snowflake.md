---
layout: post
title: We are all special and unique
tags:
- nih
- configurationmanagement
- software
- tools
---

### Pattern

1. The only way to solve our problems is to build it ourselves.

---

### Story

(**Editor's Note:** *This is a very special anti-pattern in that I've
personally seen it at multiple companies at varying levels. In order to
preserve the anonymity of my sources however, I will group all of these stories
together under one over-arching pretend org: "Great Operations
Over-engineering Group" or "GOOG."*)


As one of the most senior Ops engineers at GOOG, Sergey has helped scale the
company's infrastructure practically from the beginning. If you find a good
peaty scotch, Sergey might just share some of the stories "from the olden
days."

A few years ago when GOOG's infrastructure was only a couple of Linux
servers, Sergey would just SSH to the hosts to make changes as needed. After
the machine count grew into double digits, Sergey the ever creative sysadmin
created a bash script to SSH into all the hosts and run commands. Sergey had
heard of tools like [Capistrano](http://capistranorb.com/) and
[Fabric](http://fabfile.org/) but they seemed like a bit overkill for somebody
that just wanted to SSH into a few hosts and restart Apache. For now, Sergey's
SSH Shell ("SSSHSH" pronounced "shush") was doing the job just fine.

When more people joined GOOG's growing Ops team, SSSHSH had become a standard
tool that everybody was using, and in turn everybody had bug reports and
feature requests. 

* "*Can it be used to SCP files to all the servers?*"
* "*When one host dies, it breaks the entire SSSHSH command*"
* "*SSSHSH should handle piping data through stdin to send to the hosts*"
* "*SSSHSH doesn't work properly on Zsh*"
* "*Sometimes I just need to run a command against the www pool, SSSHSH should
  support groups*"
* "*SSSHSH should check for a file's presence before over-writing it with a new
  one*"
* "*SSSHSH isn't fast enough, can it control hosts in parallel?*"


Sergey's little pet project had blossomed into thousands of lines of shell code
spread across multiple files. As the project grew, it intertwined into more and
more of GOOG's infrastructure. Want to upgrade to a new version of a package?
No problem, just use this package management tool built on top of SSSHSH! Need
to tail multiple logs from multiple servers? No problem! Just use this
multi-tail tool that was also written on top of SSSHSH.


As the rest of the world has moved forward with common open source
configuration management and orchestration tools, GOOG's Ops team is still
hammering away with SSSHSH, exhibiting the classic symptoms of SSSHSHSS
(Sergey's SSH Shell Stockholm Syndrome).
