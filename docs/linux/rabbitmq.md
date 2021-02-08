---
title: "RabbitMQ"
description: "RabbitMB sheet cheat"
lead: "RabbitMB sheet cheat"
date: 2020-10-13T15:21:01+02:00
lastmod: 2020-10-13T15:21:01+02:00
draft: false
images: []
menu:
  docs:
    parent: "linux"
weight: 130
toc: true
---

## RabbitMQCtl

### Queue management

#### List all queues

{{< btn-copy text="rabbitmqctl list_queues" >}}

```bash
   $ rabbitmqctl list_queues
```
### App management

#### Stop RabbitMQ app

{{< btn-copy text="rabbitmqctl stop_app" >}}

```bash
   $ rabbitmqctl stop_app
```

#### Start RabbitMQ app

{{< btn-copy text="rabbitmqctl start_app" >}}
```bash
   $ rabbitmqctl start_app
```

### Users management

#### List RabbitMQ users

{{< btn-copy text="rabbitmqctl list_users" >}}
```bash
   $ rabbitmqctl list_users
```
### Status

#### Get RabbitMQ status

{{< btn-copy text="rabbitmqctl status" >}}
```bash
   $ rabbitmqctl status
```

#### Get Cluster status

{{< btn-copy text="rabbitmqctl cluster_status" >}}
```bash
   $ rabbitmqctl cluster_status
```

### Cluster management

#### Set Cluster name

{{< btn-copy text="rabbitmqctl set_cluster_name" >}}
```bash
   $ rabbitmqctl set_cluster_name $(NAME)
```

#### Joining the cluster

{{< btn-copy text="rabbitmqctl join_cluster rabbit@" >}}
```bash
   $ rabbitmqctl join_cluster rabbit@$(NODE_SHORT_NAME)
```

Option :

* ``--ram``: Add node as a ram node

#### Changing the node type

{{< btn-copy text="rabbitmqctl change_cluster_node_type" >}}
```bash
   $ rabbitmqctl change_cluster_node_type $(NODE_TYPE)
```

### Vhost management

#### List vhost

{{< btn-copy text="rabbitmqctl list_vhosts" >}}
```bash
   $ rabbitmqctl list_vhosts
```

#### Create vhost

{{< btn-copy text="rabbitmqctl add_vhost" >}}
```bash
   $ rabbitmqctl add_vhost $(VHOST_NAME)
```

#### Delete vhost

{{< btn-copy text="rabbitmqctl delete_vhost" >}}
```bash
   $ rabbitmqctl delete_vhost $(VHOST_NAME)
```

#### Clustering

#### Share the Erlang cookie

An Erlang cookie should be in on server.

On a linux server the erlang cookie should be in **/var/lib/rabbitmq/.erlang.cookie**

#### Add node to cluster

We asume than have those servers rabbit1, rabbit2 and rabbit3. We add rabbit2 and 3 in the cluster.

```bash
   $ rabbitmqctl stop_app
   $ rabbitmqctl reset
   $ rabbitmqctl join_cluster rabbit@rabbit1
   $ rabbitmqctl start_app
```
