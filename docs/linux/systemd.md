---
title: "Systemd"
description: "Systemd reminder"
lead: "Systemd reminder"
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

## Command line

### Common

The `--user` option limit command on the user scope

The `--system` option do the same but for the system and is the default.

The user systemd unit file can be found in :

* ~/.local/share/systemd/user/
* ~/.config/systemd/user/

### Get system status


{{< btn-copy text="systemctl status" >}}

```bash
$ systemctl status
```


List all units in running state
-------------------------------

{{< btn-copy text="systemctl list-units --state running" >}}

```bash
$ systemctl list-units --state running
```

List all failed units
---------------------

{{< btn-copy text="systemctl --failed" >}}

```bash
$ systemctl --failed
```

Get a list of all installed units
---------------------------------

{{< btn-copy text="systemctl list-unit-files" >}}

```bash
$ systemctl list-unit-files
```

Get unit status
---------------

{{< btn-copy text="systemctl status" >}}

```bash
$ systemctl status $(UNIT_NAME)
```

Start unit
----------

{{< btn-copy text="systemctl start" >}}

```bash
$ systemctl start $(UNIT_NAME)
```

Stop unit
---------

{{< btn-copy text="systemctl stop" >}}

```bash
$ systemctl stop $(UNIT_NAME)
```

Restart unit
------------

{{< btn-copy text="systemctl restart" >}}

```bash
$ systemctl restart $(UNIT_NAME)
```

Reload unit
-----------

{{< btn-copy text="systemctl reload" >}}

```bash
$ systemctl reload $(UNIT_NAME)
```

Check if unit is enabled
------------------------

{{< btn-copy text="systemctl is-enabled" >}}

```bash
$ systemctl is-enabled $(UNIT_NAME)
```

Enable unit at boot
-------------------

{{< btn-copy text="systemctl enable" >}}

```bash
$ systemctl enable $(UNIT_NAME)
```

Disable unit
------------

{{< btn-copy text="systemctl disable" >}}

```bash
$ systemctl disable $(UNIT_NAME)
```
Mask a given unit
-----------------

{{< btn-copy text="systemctl mask" >}}

```bash
$ systemctl mask $(UNIT_NAME)
```

Unmask a given unit
-------------------

{{< btn-copy text="systemctl unmask" >}}

```bash
$ systemctl unmask $(UNIT_NAME)
```

List all timer
--------------

{{< btn-copy text="systemctl list-timers" >}}

```bash
$ systemctl list-timers
```

Reload the systemd manager configuration
----------------------------------------

Usefull when you change or create an unit file

{{< btn-copy text="systemctl daemon-reload" >}}

```bash
$ systemctl daemon-reload
```

Show cgroups ressources usage
-----------------------------

{{< btn-copy text="systemd-cgtop" >}}

```bash
$ systemd-cgtop
```

Show ressources of given cgroup
-------------------------------

{{< btn-copy text="systemd-cgls $(CGROUP)" >}}

```bash
$ systemd-cgls $(CGROUP)
```

Systemd unit management
~~~~~~~~~~~~~~~~~~~~~~~

Create service unit
-------------------

The unit name must be finish by .service for example : **my-greatest-unit.service**.
The units path location are in **/etc/systemd/system/** or **/lib/systemd/system/**.
For new units **/etc/systemd/system/** is the better location.

```bash
   [Unit]
   Description=$(UNIT_DESCRIPTION)
   After=$(AFTER_WHICH_TARGET)

   [Service]
   Type=$(SYSTEMD_TYPE)
   User=$(USER)
   ExecStartPre=$(PRE_EXEC)
   ExecStart=$(EXEC_COMMAND)
   ExecStop=$(EXEC_COMMAND)
   Restart=$(RESTART POLICY)
```

Types :

* ``simple``
* ``forking``
* ``oneshot``
* ``dbus``
* ``notify``
* ``idle``
