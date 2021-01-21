# Setting up new slave with master-slave replication (without gtid with mariadb 5.5)

## Step 1: mysqldump on master 
```
mkdir /backups 
mkdir mysqldumpdir 
# in version 5.5. there is not --git so use it without --gtid
mysqldump --all-databases --single-transaction --master-data=2 --routines --events --compress > /backups/mysqldumpdir/master-databases.sql;

```




## Walkthrough 

https://mariadb.com/kb/en/setting-up-a-replication-slave-with-mariabackup/
