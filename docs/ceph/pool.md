---
title: "Pools"
description: "Administration CLI"
lead: "Pools management "
date: 2020-10-13T15:21:01+02:00
lastmod: 2020-10-13T15:21:01+02:00
draft: false
images: []
menu:
  docs:
    parent: "ceph"
weight: 110
toc: true
---
## Pools

### List pools

```bash
   $ ceph osd pool ls detail
```

Here ``detail`` is optionnal

### Get pool information

```bash
   $ ceph osd pool get <pool_name> all
```

### Delete pool

```bash
   $ ceph osd pool rm <pool_name> <pool_name> --yes-really-really-mean-it
```

### Create new replicated pool

```bash
   $ ceph osd pool create <pool_name> <pg_number>
   $ ceph osd pool set <pool_name> size <replicas_number>
```

### Create new erasure coding pool

Get erasure coding profile :

```bash
   $ ceph osd erasure-code-profile get default
```

Or create new erasure coding profile :

```bash
   $ ceph osd erasure-code-profile set <profile_name> k=<k_num> m=<m_num> crush-failure-domain=<failure_domain>
```

Refer to your crushmap for ``crush-failure-domain``


Create erasure coding pool :

```bash
   $ ceph osd pool create ecpool <pg_number> erasure <profile_name>
```

In Luminous, partial writes enabling :

```bash
   $ ceph osd pool set <pool_name> allow_ec_overwrites true
```

### List all Erasure Coding profiles

```bash
   $ ceph osd erasure-code-profile ls
```

### Get information about Erasure Coding profile

```bash
   $ ceph osd erasure-code-profile get <ec_profile>
```
## Quotas

### Set objects quota

```bash
   $ ceph osd pool set-quota <pool_name> max_objects <object_number>
```

### Set bytes quota

```bash
   $ ceph osd pool set-quota <pool_name> max_bytes <bytes_number>
```

### Get quota

```bash
   $ ceph osd pool get-quota <pool_name>
```

