---
title: "Cephadm"
description: "cephadm CLI"
lead: "Cephadm and Ceph orch"
date: 2020-10-13T15:21:01+02:00
lastmod: 2020-10-13T15:21:01+02:00
draft: false
images: []
menu:
  docs:
    parent: "ceph"
weight: 132
toc: true
---
## Documentation

You can find the official documentation here:

[Official documentation](https://docs.ceph.com/en/latest/cephadm/install/)

## Usage

### Bootstrap Cluster

{{< btn-copy text="sudo cephadm bootstrap" >}}

```bash
$ sudo cephadm bootstrap --mon-ip <mon-ip> --cluster-network <cluster_net> --ssh-user <user>
$ sudo cephadm bootstrap --mon-ip 192.168.0.10  --ssh-user vagrant
```
We need to deploy ceph's ssh key on cluster's hosts

{{< btn-copy text="ssh-copy-id -f -i /etc/ceph/ceph.pub ">}}

```bash
$ ssh-copy-id -f -i /etc/ceph/ceph.pub <user>@<new-host>
```
Open a shell into your cluster
{{< btn-copy text="sudo cephadm shell --fsid" >}}
```bash
$ sudo cephadm shell --fsid 254961fc-6b7b-11eb-adbf-ab1c4f35b52e -c /etc/ceph/ceph.conf -k /etc/ceph/ceph.client.admin.keyring
```
### Configure network and monitor

Set the public network into centralized configuration
{{< btn-copy text="ceph config set mon public_network" >}}
```bash
# ceph config set mon public_network <mon-cidr-network>
```
Set number of monitor on your cluster and initialize it
{{< btn-copy text="ceph orch apply mon " >}}
```bash
# ceph orch apply mon <number-of-monitors>
# ceph orch apply mon <host1,host2,host3,...>
```
An other way to deploy monitors, labeled it and deploy all host who have th label
```bash
# ceph orch host label add <hostname> mon
# ceph orch host ls
# ceph orch apply mon label:mon
```

### Adding OSDs

Adding all device available in your cluster
{{< btn-copy text="ceph orch apply osd --all-available-devices" >}}
```bash
# ceph orch device ls
# ceph orch apply osd --all-available-devices
```
Adding one device
{{< btn-copy text="ceph orch daemon add osd" >}}
```bash
# ceph orch daemon add osd <host>:<device-path>
```

### Add filesystem
{{< btn-copy text="ceph fs volume create" >}}
```bash
# ceph fs volume create <fs_name> --placement="<placement>""
```

### Add RGW
{{< btn-copy text="ceph orch apply rgw" >}}
```bash
# ceph orch apply rgw <realm-name> <zone-name> --placement="<num-daemons> [<host>...]"
```
### Replace OSDs

Make sure it is safe to destroy the OSD:

```bash
# while ! ceph osd safe-to-destroy osd.{id} ; do sleep 10 ; done
```
Destroy the OSD first:

{{< btn-copy text="ceph osd destroy ID --yes-i-really-mean-it" >}}
```bash
# ceph osd destroy {id} --yes-i-really-mean-it
```
Zap a disk for the new OSD, if the disk was used before for other purposes. It’s not necessary for a new disk:
This command must be run on node who host the osd.

{{< btn-copy text="cephadm ceph-volume lvm zap" >}}
```bash
# cephadm ceph-volume lvm zap /dev/sdX
```
Adding the osd with `ceph orch` command
{{< btn-copy text="ceph orch daemon add osd" >}}
```bash
# ceph orch daemon add osd <host<>:<device-path>
```
