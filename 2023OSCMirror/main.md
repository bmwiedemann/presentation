# Introduction

## Who is that guy?

* Bernhard M. Wiedemann
* working for SUSE
* involved with our download infra for some years
* did also: reproducible builds, openQA, OpenStack, OBS

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

## What we could do

* patch libzypp to
* * not do one req per file, but per dir
* * cache `/media` file for some time
* * not use too small chunks
* patch MirrorCache to
* * return cachable mirrorlist(lat+lon+stability)
* * let server decide if to send metalink/302/rpm
* * integrate downloadcontent fallback for main repos into origin

## Typical problems

# Questions & Answers

# Discussion
