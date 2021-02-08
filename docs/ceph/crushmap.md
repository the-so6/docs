---
title: "CRUSH map and rules"
description: "Administration CLI"
lead: "Ceph objects administration"
date: 2020-10-13T15:21:01+02:00
lastmod: 2020-10-13T15:21:01+02:00
draft: false
images: []
menu:
  docs:
    parent: "ceph"
weight: 105
toc: true
---

## CrushMap

Get CrushMap

```bash
   $ ceph osd getcrushmap -o <binary_file>
```

### Convert crushMap

From binary to text

```bash
   $ crushtool -d <binary_file> -o <text_file>
```

From text to binary

```bash
   $ crushtool -c <text_file> -o <binary_file>
```


### Set CrushMap

```bash
   $ ceph osd setcrushmap -i <binary_file>
```

### Create new bucket

```bash
   $ ceph osd crush add-bucket <name> <type>
```

List of types :

* osd
* host
* chassis
* rack
* row
* pdu
* pod
* room
* datacenter
* region
* root

### Delete bucket

```bash
   $ ceph osd crush remove <bucket>
```

### Move object to new bucket


```bash
   $ ceph osd crush move <object> <bucket_type>=<bucket_name>
```

### Create new replicated rule

```bash
   $ ceph osd crush rule create-replicated <rule_name> <bucket_location> <bucket_rep> <osd_class>
```

Example will create a replicated rule limited on datacenter **dc1** with SSD :

```bash
   $ ceph osd crush rule create-replicated dc1-fast dc1 host ssd
```

### List rules

```bash
   $ ceph osd crush rule ls
```
### Dump rules

```bash
   $ ceph osd crush rule dump <rule>
```

### Remove rule

```bash
   $ ceph osd crush rule rm <rule_name>
```


