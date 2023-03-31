# Incremental backup with mariabackup 

## Prerequisites: Setup user to be used in /root/.my.cnf 

```
# user eintrag in /root/.my.cnf
[mariabackup]
user=root 
# pass is not needed here, because we have the user root with unix_socket - auth 
```

## Backup-Phase 

### Day 1: First full backup (directory always needs to be empty) 

```
# create some data 
mysql -e "create schema if not exists backuptest" 
mysql -e "create table if not exists data (id int, content varchar(50), primary key(id))" backuptest
mysql -e "insert into data (id, content) values (1, 'day1 - dataset 1'),(2, 'day 1 - dataset 2')" backuptest
mysql -e "select * from data" backuptest 

# create a folder for our backup 
mkdir -p /var/mariadb 

# Day 1: let us do the full backup 
mariabackup --backup --target-dir=/var/mariadb/backup/ 

```

### Day 2: Let us add some data and then do the incremental backup 

```
mysql -e "insert into data (id, content) values (3, 'day2 - dataset 1'),(4, 'day 2 - dataset 2')" backuptest
mysql -e "select * from data" backuptest 
# now do the backup - folder inc1 needs to be empty !!! 
mariabackup --backup \
   --target-dir=/var/mariadb/inc1/ \
   --incremental-basedir=/var/mariadb/backup/ 

```

### Day 3: Let us even add more more data and the do the incremental backup 

```
mysql -e "insert into data (id, content) values (5, 'day3 - dataset 1'),(6, 'day 3 - dataset 2')" backuptest 
mysql -e "select * from data" backuptest 

# now we do the backup based on the last incremnental backup (so basedir is inc1) 

mariabackup --backup \
   --target-dir=/var/mariadb/inc2/ \
   --incremental-basedir=/var/mariadb/inc1/
```

## Recovery Phase 

### Prepare 

```
# Step 1: Apply the changes from recovery/redo log of full backup 
mariabackup --prepare --target-dir=/var/mariadb/backup

# Step 2: Add the changes from inc1 
mariabackup --prepare --target-dir=/var/mariadb/backup --incremental-dir=/var/mariadb/inc1

# Step 3: Add the changes from inc2 
mariabackup --prepare --target-dir=/var/mariadb/backup --incremental-dir=/var/mariadb/inc2
```

### Copy-Back 

```
systemctl stop mariadb
cd /var/lib/
mv mysql mysql.mybkup 
mariabackup --copy-back --target-dir=/var/mariadb/backup 
chown -R mysql:mysql mysql 
systemctl start mariadb 

# Check if we have all data again 
mysql -e "select * from data" backuptest 
```

## Ref:

  * https://mariadb.com/kb/en/incremental-backup-and-restore-with-mariabackup/
