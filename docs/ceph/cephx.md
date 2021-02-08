---
title: "User Management "
description: "Administration CLI"
lead: "CephX usage"
date: 2020-10-13T15:21:01+02:00
lastmod: 2020-10-13T15:21:01+02:00
draft: false
images: []
menu:
  docs:
    parent: "ceph"
weight: 111
toc: true
---

## List all CephX auth

```bash
   $ ceph auth list
```

## Get an user

```bash
   $ ceph auth get-or-create <user>
```

## Create an user

```bash
   $ ceph auth get-or-create <user> mon <mon_caps> osd <osd_caps>
```

## Update user caps

```bash
   $ ceph auth caps <user> mon <mon_caps> osd <osd_caps>
```

## Delete user

```bash
   $ ceph auth caps <user> mon '' osd ''
```
