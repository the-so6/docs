---
title: "Ceph configuration"
description: "Administration CLI"
lead: "Ceph configuration"
date: 2020-10-13T15:21:01+02:00
lastmod: 2020-10-13T15:21:01+02:00
draft: false
images: []
menu:
  docs:
    parent: "ceph"
weight: 104
toc: true
---
## Ceph centralized configuration

### Dump configuration
{{< btn-copy text="ceph config dump" >}}
```bash
ceph config dump
```
### Set parameter
{{< btn-copy text="ceph config set" >}}
```bash
ceph config set <who> <name> <value>
```
### Help on a particular parameter
{{< btn-copy text="ceph config help" >}}
```bash
ceph config help <parameter>
```
Example:
```bash
ceph config help mon_allow_pool_delete
mon_allow_pool_delete - allow pool deletions
  (bool, advanced)
  Default: false
  Can update at runtime: true
  Services: [mon]
```
### Configuration history
{{< btn-copy text="ceph config log" >}}
```bash
ceph config log
```
### Rollback configuration
{{< btn-copy text="ceph config reset" >}}
```bash
ceph config reset <log_to_reset>
```
### Assimilation from standart ceph.conf
{{< btn-copy text="ceph config assimilate-conf" >}}
```bash
ceph config assimilate-conf -i <source_conf_file> -o <new_conf_file>
```
