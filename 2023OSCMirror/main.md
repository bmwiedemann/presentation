# Introduction

## Who is that guy?

* Bernhard M. Wiedemann
* working for SUSE
* involved with our download infra for some years
* did also: reproducible builds, openQA, OpenStack, OBS

# Typical problems

## Number of users growing
![metrics/users/3y](img/20230519-metrics-users-s.png)

## spikes from full rebuilds (1-3 per year)
![download/year](img/20230519-if_publish-year.png)

## spikes from Leap+Tumbleweed updates

![downloadcontent2/day](img/20230518-if_eth0-day.png)

## short spikes from a company's mass-updates
![muninapache/day](img/20230519-apache_accesses-day.png)

## Why do we need to improve?

* high latency causes poor performance outside Europe
* bottleneck on disk+net IO on download/stage
* number of users is growing
* some SPOFs can cause annoying outages
* current MirrorCache output is not trivial to cache

## What we already did

* regional mirrorcache in US, BR, JP, AU
* stage3
* downloadcontent2, -us1, -br
* CDN WIP

## What we could do (1)

* patch libzypp to
* * not do one req per file, but per dir
* * cache `/media` file for some time
* * not use too small chunks

## What we could do (2)
* patch MirrorCache to
* * return cachable mirrorlist(lat+lon+stability)
* * let server decide if to send metalink/302/rpm
* * integrate downloadcontent fallback for main repos into origin

## What we could do (3)

* split stage.o.o off download.o.o ; with or without /repositories
* rethink /repositories repopush to reduce write-only data
* use CDN to handle load-spikes and small files

# Questions & Answers & Discussion
