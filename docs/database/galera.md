---
title: "Galera"
description: "Some galera tricks"
lead: "Some galera tricks"
date: 2020-10-13T15:21:01+02:00
lastmod: 2020-10-13T15:21:01+02:00
draft: false
images: []
menu:
  docs:
    parent: "database"
weight: 130
toc: true
---



## Recover Disaster

### Restart a stopped Galera Cluster

On one of the node change ``safe_to_bootstrap`` to ``1`` in ``/var/lib/mysql/grastate.dat``

```bash
   # GALERA saved state
   version: 2.1
   uuid:    34546540-er30-1223-rsa0-23343fesf25c
   seqno:   -1
   cert_index:
   safe_to_bootstrap: 1
```

{{< alert icon="👉" text="On a running node `seqno: -1` is a normal behaviour, in case of crash find the highest to be sure to bootstrap from the safety node">}}

#### Start a new cluster

{{< btn-copy text="galera_new_cluster" >}}
```bash
   $ galera_new_cluster
```

The others nodes

{{< btn-copy text="systemctl restart mariadb" >}}
```bash
   $ systemctl restart mariadb
```

### Monitoring Galera Cluster

#### Show all wsrep

{{< btn-copy text="SHOW GLOBAL STATUS LIKE 'wsrep_%';" >}}
```bash
   MariaDB [(none)]> SHOW GLOBAL STATUS LIKE 'wsrep_%';
```

#### Check cluster integrity

{{< btn-copy text="SHOW GLOBAL STATUS LIKE 'wsrep_cluster_state_uuid';" >}}
```bash
   MariaDB [(none)]> SHOW GLOBAL STATUS LIKE 'wsrep_cluster_state_uuid';
```

#### Show cluster size

{{< btn-copy text="SHOW GLOBAL STATUS LIKE 'wsrep_cluster_size';" >}}
```bash
   MariaDB [(none)]> SHOW GLOBAL STATUS LIKE 'wsrep_cluster_size';
```

#### Show cluster status


{{< btn-copy text="SHOW GLOBAL STATUS LIKE 'wsrep_cluster_status';" >}}
```bash
   MariaDB [(none)]> SHOW GLOBAL STATUS LIKE 'wsrep_cluster_status';
```

### Show node status

Show if the node can accept queries :

{{< btn-copy text="SHOW GLOBAL STATUS LIKE 'wsrep_ready';" >}}
```bash
   MariaDB [(none)]> SHOW GLOBAL STATUS LIKE 'wsrep_ready';
```

Show if the node has network connectivity to other nodes inside the cluster :

{{< btn-copy text="SHOW GLOBAL STATUS LIKE 'wsrep_connected';" >}}
```bash
   MariaDB [(none)]> SHOW GLOBAL STATUS LIKE 'wsrep_connected';
```

Show the node state :

{{< btn-copy text="SHOW GLOBAL STATUS LIKE 'wsrep_local_state_comment';" >}}
```bash
   MariaDB [(none)]> SHOW GLOBAL STATUS LIKE 'wsrep_local_state_comment';
```
The typical values are :

* Joining
* Waiting
* SST
* Joined
* Synced
* Donor

### Format unreadable output

Running queries on wide tables using the MySQL command line can often result in unreadable output:
```bash
SELECT * FROM mysql.user;
+----------------------------+-----------------+-------------------------------------------+-------------+-------------+-------                            ------+-------------+-------------+-----------+-------------+---------------+--------------+-----------+------------+----------                            -------+------------+------------+--------------+------------+-----------------------+------------------+--------------+-------                            ----------+------------------+------------------+----------------+---------------------+--------------------+------------------                            +------------+--------------+------------------------+----------+------------+-------------+--------------+---------------+----                            ---------+-----------------+----------------------+--------+-----------------------+
| Host                       | User            | Password                                  | Select_priv | Insert_priv | Update                            _priv | Delete_priv | Create_priv | Drop_priv | Reload_priv | Shutdown_priv | Process_priv | File_priv | Grant_priv | Reference                            s_priv | Index_priv | Alter_priv | Show_db_priv | Super_priv | Create_tmp_table_priv | Lock_tables_priv | Execute_priv | Repl_s                            lave_priv | Repl_client_priv | Create_view_priv | Show_view_priv | Create_routine_priv | Alter_routine_priv | Create_user_priv                             | Event_priv | Trigger_priv | Create_tablespace_priv | ssl_type | ssl_cipher | x509_issuer | x509_subject | max_questions | max                            _updates | max_connections | max_user_connections | plugin | authentication_string |
+----------------------------+-----------------+-------------------------------------------+-------------+-------------+-------                            ------+-------------+-------------+-----------+-------------+---------------+--------------+-----------+------------+----------                            -------+------------+------------+--------------+------------+-----------------------+------------------+--------------+-------                            ----------+------------------+------------------+----------------+---------------------+--------------------+------------------                            +------------+--------------+------------------------+----------+------------+-------------+--------------+---------------+----                            ---------+-----------------+----------------------+--------+-----------------------+
| %                          | someuser            |                                           | Y           | Y           | Y                                       | Y           | Y           | Y         | Y           | Y             | Y            | Y         | Y          | Y                                           | Y          | Y          | Y            | Y          | Y                     | Y                | Y            | Y                                           | Y                | Y                | Y              | Y                   | Y                  | Y                                            | Y          | Y            | Y                      |          |            |             |              |             0 |                                       0 |               0 |                    0 |        |                       |
| localhost      | someuser            |                                           | Y           | Y           | Y                                       | Y           | Y           | Y         | Y           | Y             | Y            | Y         | Y          | Y                                           | Y          | Y          | Y            | Y          | Y                     | Y                | Y            | Y                                           | Y                | Y                | Y              | Y                   | Y                  | Y                                            | Y          | Y            | Y                      |          |            |             |              |             0 |                                       0 |               0 |                    0 |        |                       |
```
You can format this output so that the columns are displayed as key: value pairs by using \G rather than ;, like so:

```bash
SELECT * FROM mysql.user \G

*************************** 1. row ***************************
                  Host: localhost
                  User: someuser
              Password:
           Select_priv: N
           Insert_priv: N
           Update_priv: N
           Delete_priv: N
           Create_priv: N
             Drop_priv: N
           Reload_priv: N
         Shutdown_priv: N
          Process_priv: N
             File_priv: N
            Grant_priv: N
       References_priv: N
            Index_priv: N
            Alter_priv: N
          Show_db_priv: N
            Super_priv: N
 Create_tmp_table_priv: N
      Lock_tables_priv: N
          Execute_priv: N
       Repl_slave_priv: N
      Repl_client_priv: N
      Create_view_priv: N
        Show_view_priv: N
   Create_routine_priv: N
    Alter_routine_priv: N
      Create_user_priv: N
            Event_priv: N
          Trigger_priv: N
Create_tablespace_priv: N
              ssl_type:
            ssl_cipher:
           x509_issuer:
          x509_subject:
         max_questions: 0
           max_updates: 0
       max_connections: 0
  max_user_connections: 0
                plugin:
 authentication_string:
*************************** 12. row ***************************
                  Host: %
                  User: someuser
              Password:
           Select_priv: N
           Insert_priv: N
           Update_priv: N
           Delete_priv: N
           Create_priv: N
             Drop_priv: N
           Reload_priv: N
         Shutdown_priv: N
          Process_priv: N
             File_priv: N
            Grant_priv: N
       References_priv: N
            Index_priv: N
            Alter_priv: N
          Show_db_priv: N
            Super_priv: N
 Create_tmp_table_priv: N
      Lock_tables_priv: N
          Execute_priv: N
       Repl_slave_priv: N
      Repl_client_priv: N
      Create_view_priv: N
        Show_view_priv: N
   Create_routine_priv: N
    Alter_routine_priv: N
      Create_user_priv: N
            Event_priv: N
          Trigger_priv: N
Create_tablespace_priv: N
              ssl_type:
            ssl_cipher:
           x509_issuer:
          x509_subject:
         max_questions: 0
           max_updates: 0
       max_connections: 0
  max_user_connections: 0
                plugin:
 authentication_string:
 ```
