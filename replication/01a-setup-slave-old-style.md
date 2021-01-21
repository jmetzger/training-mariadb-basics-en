# Setting up new slave with master-slave replication (without gtid with mariadb 5.5)

## Step 1: mysqldump on master 
```
mkdir -p /backups/mysqldumpdir 
# in version 5.5. there is not --git so use it without --gtid
mysqldump --all-databases --single-transaction --master-data=2 --routines --events --compress > /backups/mysqldumpdir/master-databases.sql;

```

## Step 2: Transfer to new slave (from master) 

```
# root@master:
rsync -e ssh -avP /backups/mysqldumpdir/master-databases.sql kurs@10.10.9.144:/home/kurs/
```
## Step 3 (Optional): Be sure that slave is really fresh (no data yet) 

```
# if old not wanted data is present, e.g. other databases, start with fresh-installation by so:
# as root
cd /var/lib 
mv mysql mysql.bkup 
mariadb-install-db --user=mysql 
```

## Step 4: Setup replication user on master 

```
# as root@master 
#mysql>
CREATE USER repl@'10.10.9.%' IDENTIFIED BY 'password';
GRANT REPLICATION SLAVE ON *.*  TO 'repl'@'10
```

## Step 4a (Optional): Test repl user (connect) from slave 

```
# as root@slave 
# you be able to connect to 
mysql -urepl -p -h10.10.9.110


```


## Walkthrough 

https://mariadb.com/kb/en/setting-up-a-replication-slave-with-mariabackup/
