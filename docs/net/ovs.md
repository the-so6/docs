---
title: "Openvswitch"
description: "Openvswitch tricks"
lead: "Openvswitch tricks"
date: 2020-10-13T15:21:01+02:00
lastmod: 2020-10-13T15:21:01+02:00
draft: false
images: []
menu:
  docs:
    parent: "net"
weight: 100
toc: true
---

## Openvswitch DB
### Print Version

{{< btn-copy text="ovs-vsctl -V" >}}
```bash
$ ovs-vsctl -V
```
### Show configuration

{{< btn-copy text="ovs-vsctl show" >}}
```bash
$ ovs-vsctl show
```
### List bridges

{{< btn-copy text="ovs-vsctl list-br" >}}
```bash
$ ovs-vsctl list-br
```
### List ports on bridge

{{< btn-copy text="ovs-vsctl list-ports" >}}
```bash
$ ovs-vsctl list-ports <bridge>
```

### Add bridge

{{< btn-copy text="ovs-vsctl add-br" >}}

```bash
ovs-vsctl add-br <bridge>
```
### Add port on bridge

{{< btn-copy text="ovs-vsctl add-port" >}}
```bash
ovs-vsctl add-port <bridge> <interface>
```

### Set controller

{{< btn-copy text="ovs-vsctl set-controller" >}}
```bash
ovs-vsctl set-controller <bridge> tcp:<IP>:<port> tcp:<IP>:<port>
```

### Get controller information

{{< btn-copy text="ovs-vsctl get-controller" >}}
```bash
ovs-vsctl get-controller <bridge>
```
### Delete controller

{{< btn-copy text="ovs-vsctl del-controller" >}}
```bash
ovs-vsctl del-controller <bridge>
```

### Set fail mode
#### Standalone

{{< btn-copy text="ovs-vsctl set-fail-mode" >}}
```bash
ovs-vsctl set-fail-mode <bridge> standalone
```

#### Secure

{{< btn-copy text="ovs-vsctl set-fail-mode" >}}
```bash
ovs-vsctl set-fail-mode <bridge> secure
```
### Get fail mode

{{< btn-copy text="ovs-vsctl get-fail-mode" >}}
```bash
ovs-vsctl get-fail-mode <bridge>
```
## Openvswitch Open Flows

### Dump flows for a bridge

{{< btn-copy text="ovs-ofctl dump-flows" >}}
```bash
ovs-ofctl dump-flows <bridge>
```
### Delete flows for a bridge

{{< btn-copy text="ovs-ofctl del-flows" >}}
```bash
ovs-ofctl del-flows <bridge>
```
