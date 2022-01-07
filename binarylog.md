# Binary Log 

## General

  * It is disabled by default 

# Why and when to use it ? 

  * Needed Galera Cluster (3 - Node - Cluster)  
  * Replication 
  * PIT (Point-In-Time) - Recovery (e.g. recover to start from 4 a.m. with full backup + binary log)

# How to enable it ? 

```
# Ubuntu 
# vi /etc/mysql/mariadb.conf.d/50-server.cnf 
[mysqld]
log-bin 

# Restart server 
systemctl restart mariadb 

```

# How to view the binary-log 

```
cd /var/lib/mysql

mysqlbinlog -vv mysqld-bin.000001
# in the special configuration from /etc/mysql/... gets in the way 
mysqlbinlog --no-defaults -vv mysqld-bin.000001

```

