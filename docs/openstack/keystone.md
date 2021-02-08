---
title: "Keystone"
description: "Administration CLI"
lead: "User / Role / project Administration"
date: 2020-10-13T15:21:01+02:00
lastmod: 2020-10-13T15:21:01+02:00
draft: false
images: []
menu:
  docs:
    parent: "openstack"
weight: 200
toc: true
---

## User Management

### List users

{{< btn-copy text="openstack user list" >}}
```bash
$ openstack user list
```
### Create user

{{< btn-copy text="openstack user create" >}}
```bash
$ openstack user create --password <user_pssword> <username>
```
### Update curent user password

{{< btn-copy text="openstack user password set" >}}
```bash
$ openstack user password set --password <new-password>
```
### Delete User

{{< btn-copy text="openstack user delete" >}}
```bash
$ openstack user delete <username>
```
## Catalog managamenet

### Create service

{{< btn-copy text="openstack service create" >}}
```bash
$ openstack service create --name <service_name> \
    --description "<service_description>" <openstack_service_name>
```
example:
```bash
$ openstack service create --name glance \
        --description "OpenStack Image service" image
```
### Create endpoint

{{< btn-copy text="openstack endpoint create" >}}
```bash
$ openstack endpoint create --region <region_name>\
    image public <endpoint_url>
```
example:
``` bash
$ openstack endpoint create --region RegionOne \
    image public http://controller:9292
```
## Project Management
### List project

{{< btn-copy text="openstack project list" >}}
```bash
$ openstack project list
```
### Create project

{{< btn-copy text="openstack project create" >}}
```bash
$ openstack project create <project>
```
### Delete project

{{< btn-copy text="openstack project delete" >}}
```bash
$ openstack project delete <project>
```
## Role Management

### List Role

{{< btn-copy text="openstack role list" >}}
```bash
$ openstack role list
```
### Show role detail

{{< btn-copy text="openstack role show" >}}
```bash
$ openstack role show <role_ip>
```
### Create Role

{{< btn-copy text="openstack role create" >}}
```bash
$ openstack role create <role_name>
```
### Delete Role

{{< btn-copy text="openstack role delete" >}}
```bash
$ openstack role delete <role_id>
```
### Assign role to a user

{{< btn-copy text="openstack role add" >}}
```bash
$ openstack role add --project <project_id> --user <user> <role>
```
### List role assignemnt

{{< btn-copy text="openstack role assignment list" >}}
```bash
$ openstack role assignment list
```
### Remove role to a user

{{< btn-copy text="openstack role remove" >}}
```bash
$ openstack role remove --project <project_id> --user <user> <role>
```
