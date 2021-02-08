---
title: "Glance"
description: "Administration CLI"
lead: "Cloud image Administration"
date: 2020-10-13T15:21:01+02:00
lastmod: 2020-10-13T15:21:01+02:00
draft: false
images: []
menu:
  docs:
    parent: "openstack"
weight: 210
toc: true
---
## List images

{{< btn-copy text="openstack image list" >}}
```bash
$ openstack image list
```

## Create image

{{< btn-copy text="openstack image create" >}}
```bash
$ openstack image create <image_name> \
    --disk-format <disk_format> \
    --public \
    --file <file>
```
## Download Image

{{< btn-copy text="openstack image save" >}}
```bash
$ openstack image save <image_id> --file <image_file_name.img>
```
