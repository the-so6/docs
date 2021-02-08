---
title: "MGR"
description: "Administration CLI"
lead: "Manage MGR service"
date: 2020-10-13T15:21:01+02:00
lastmod: 2020-10-13T15:21:01+02:00
draft: false
images: []
menu:
  docs:
    parent: "ceph"
weight: 115
toc: true
---

## List modules

```bash
   $ ceph mgr module ls
```

## Enable module

```bash
   $ ceph mgr module enable <module>
```

## Disable module

```bash
   $ ceph mgr module disable <module>
```

## List modules endpoint

```bash
   $ ceph mgr services
```
