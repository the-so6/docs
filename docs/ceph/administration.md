---
title: "Ceph cluster"
description: "Administration CLI"
lead: "General ceph administration"
date: 2020-10-13T15:21:01+02:00
lastmod: 2020-10-13T15:21:01+02:00
draft: false
images: []
menu:
  docs:
    parent: "ceph"
weight: 100
toc: true
---

## Cluster

### Get cluster health


```bash
   $ ceph -s
```

```bash
   $ ceph health
```


```bash
   $ ceph -w
```

### Get OSD stats

```bash
   $ ceph osd stat
```

### Get MON stats
```bash
   $ ceph mon stat
```

### Get MDS stats

```bash
   $ ceph mds stat
```

### Dump placement group

```bash
   $ ceph pg dump
```

### Dump stunked placement group

```bash
   $ ceph pg dump_stuck
```


### Get MON quorum status

```bash
   $ ceph quorum_status
```



## Monitor

### Dump monmap

```bash
   $ ceph mon getmap -o <path>
```

### Print monmap

```bash
   $ monmaptool --print <monmap_path>
```



