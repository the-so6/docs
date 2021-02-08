---
title: "Ceph Benchmark"
description: "Administration CLI"
lead: "Benchmarking ceph"
date: 2020-10-13T15:21:01+02:00
lastmod: 2020-10-13T15:21:01+02:00
draft: false
images: []
menu:
  docs:
    parent: "ceph"
weight: 130
toc: true
---
## Rados write

```bash
   $ rados bench -p <pool> <time_in_seq> write --no-cleanup
```

## Rados sequencial read

```bash
   $ rados bench -p <pool> <time_in_seq> seq
```

## Rados random read

```bash
   $ rados bench -p <pool> <time_in_seq> rand
```

## RBD Benchmark

```bash
   $ rbd bench-write <image> --pool=<pool_rbd>
```

