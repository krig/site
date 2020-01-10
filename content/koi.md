---
title: "Koi"
date: 2020-01-10T19:28:50+01:00
Description: "Koi"
Tags:
  - code
Categories:
  - whatever
---

{{< img src="/img/2koi.png" width="320px" height="320px" title="koi" alt="Two koi fishes" >}}


> Koi is a self-contained cluster management software package, written in C++. The main purpose of koi is to maintain a small cluster of machines (usually 3 or 5) where a subset of those machines run services. Services usually consist of a set of bash scripts that start, stop and monitor some other piece of software. This software only runs in active mode on one of the machines, with the other nodes functioning as backup servers. In the event of a monitoring error, the software is stopped on the faulty node and started on another machine.

I wrote `koi` while working for Procera Networks around 2011-2012, and as far as
  I know it is still in use. Now that I've worked on much larger and more
    ambitious clustering solutions like Pacemaker and Kubernetes, I have to say
    that I appreciate the minimalistic approach - although I would make very
    different choices around some of the algorithms used.

Released under the ISC license, source code available
[here](https://github.com/krig/koi).
