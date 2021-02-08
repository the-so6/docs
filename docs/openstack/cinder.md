---
title: "Cinder"
description: "Administration CLI"
lead: "Volume Administration"
date: 2020-10-13T15:21:01+02:00
lastmod: 2020-10-13T15:21:01+02:00
draft: false
images: []
menu:
  docs:
    parent: "openstack"
weight: 220
toc: true
---
## Cinder's services
### List services and show state
```bash
$ openstack volume service list
```
## Manage Type
### Create a type
```bash
$ openstack volume type create <type_name>
```
### Delete a type
```bash
$ openstack volume type delete <type_name>
```
### List all type
```bash
$ openstack volume type list
```
## Manage Volume
### List volumes
```bash
$ openstack volume list
```
### List detail from a volume
```bash
$ openstack volume show <volume_id>
```
### Create a volume
```bash
$ openstack volume create --size <size_GB> <vol_name>
```
### Delete a volume
```bash
$ openstack volume delete <volume_id>
```
