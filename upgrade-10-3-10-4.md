# Upgrade 10.3 to 10.4 (Ubuntu 20.04) 

## Prerequisites

```
Ubuntu 20.04 
MariaDB-Server from Distri

Install new 10.4 from Mariadb.org 

```
## Prepare 

  * Create backup of system (with mariabackup and/or mysqldump) 

## Steps 

```
# 1. systemctl stop mariadb 
# 2. apt remove mariadb-* 
# 3. Doublecheck if components left: apt list --installed | grep mariadb
# 4. Setup repo for mariadb
# 5. apt update 
# 6. apt install mariadb-server 

# 7. systemctl enable --now mariadb # enable for next reboot and start immediately 
# necessary for redhat 

# 8. Doublecheck if mysql_upgrade was done
cat /var/lib/mysql_upgrade_info 

```

## Important - Check mysql - configuration structure

```
# Which directories are loaded in 
/etc/mysql/my.cnf 

# Eventually move files to the right directory
# As needed in migration from 10.3 (Distri) to 10.4 (mariadb.org) on Ubuntu 20.04

```

## Documentation 

  * https://mariadb.com/kb/en/upgrading-from-mariadb-103-to-mariadb-104/
