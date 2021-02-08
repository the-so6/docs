---
title: "OSD"
description: "Administration CLI"
lead: "Manage OSDs"
date: 2020-10-13T15:21:01+02:00
lastmod: 2020-10-13T15:21:01+02:00
draft: false
images: []
menu:
  docs:
    parent: "ceph"
weight: 112
toc: true
---
## OSD

### Get OSD metadata

```bash
   $ ceph osd metadata <id_osd>
```

### Count object store by type

```bash
   $ ceph osd count-metadata osd_objectstore
```

### Get all OSDs version

```bash
   $ ceph tell osd.* version
```

### Get OSD tree

```bash
   $ ceph osd tree
```

### List all OSD device class

```bash
   $ ceph osd crush class ls
```

### List OSD by class

```bash
   $ ceph osd crush class ls-osd <class>
```

### Remove OSD device class

```bash
   $ ceph osd crush rm-device-class osd.<id_osd>
```

Multiple OSD could be specified at the same time

### Add an OSD device class

```bash
   $ ceph osd crush set-device-class <class> osd.<id_osd>
```

Multiple OSD could be specified at the same time

### Map device and osd

```bash
    $ ceph device ls
```



OLD WAYS
### Dump OSD config

```bash
   $ ceph daemon osd.<id_osd> config show
```

### Dump all OSD config

```bash
   $ ceph tell osd.* config get <key>
```


