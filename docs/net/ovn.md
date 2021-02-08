---
title: "Open Virtual Network"
description: "Open Virtual Network tricks & tips"
lead: "Open Virtual Network tricks& tips"
date: 2020-10-13T15:21:01+02:00
lastmod: 2020-10-13T15:21:01+02:00
draft: false
images: []
menu:
  docs:
    parent: "net"
weight: 101
toc: true
---

## CLI

*  Logical configuration (Northdound DB) `ovn-nbctl`
*  Physical configuration (Southbound DB) `ovn-sbctl`
*  Packet tracing `ovn-trace`

## Northbound configuration

### Show configuration

{{< btn-copy text="ovn-nbctl show" >}}
```bash
$ ovn-nbctl show
```
#### switch configuration

{{< btn-copy text="ovn-nbctl show" >}}
```bash
$ ovn-nbctl show <switch>
```
#### router configuration

{{< btn-copy text="ovn-nbctl show" >}}
```bash
$ ovn-nbctl show <router>
```
### Add a switch

{{< btn-copy text="ovn-nbctl ls-add" >}}
```bash
$ ovn-nbctl ls-add <switch>
```
### Delete a switch

{{< btn-copy text="ovn-nbctl ls-del" >}}
```bash
$ ovn-nbctl ls-del <switch>
```
### Add a port into a switch

{{< btn-copy text="ovn-nbctl lsp-add" >}}
```bash
$ ovn-nbctl lsp-add <switch> <port>
```
### Delete a port into a switch

{{< btn-copy text="ovn-nbctl lsp-del" >}}
```bash
$ ovn-nbctl lsp-del <port>
```
### Router Creation

{{< btn-copy text="ovn-nbctl lr-add" >}}
```bash
$ ovn-nbctl lr-add <router>
```
### Delete router

{{< btn-copy text="ovn-nbctl lr-del" >}}
```bash
$ ovn-nbctl lr-del <router>
```
### Create port on router

{{< btn-copy text="ovn-nbctl lrp-add" >}}
```bash
$ ovn-nbctl lrp-add <router> <port> <mac_addr> <net/mask>
```
### Delete port on router

{{< btn-copy text="ovn-nbctl lrp-del" >}}
```bash
$ ovn-nbctl lrp-del <port>
```
### Set IP address on switch

{{< btn-copy text="ovn-nbctl lsp-set-addresses" >}}
```bash
$ ovn-nbctl lsp-set-addresses <port> <mac_addr> <ip_addr>
```

## Southbound configuration

### Show configuration

{{< btn-copy text="ovn-sbctl show" >}}
```bash
$ ovn-sbctl show
```
### Add chassis

{{< btn-copy text="ovn-sbctl chassis-add" >}}
```bash
$ ovn-sbctl chassis-add <server> <encap_type> <ip_addr>
```
### Delete chassis

{{< btn-copy text="ovn-sbctl chassis-del" >}}
```bash
$ ovn-sbctl chassis-del <server>
```
