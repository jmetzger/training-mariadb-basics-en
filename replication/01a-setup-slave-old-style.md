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
# test if grants are o.k. 
show grants 
```

## Step 5a: Set server-id on master -> 1 

```
[mysqld]
server-id=1

systemctl restart mariadb 
## 
```

# Step 5b: Set server-id on slave -> 2 + same config as server 1

```
[mysqld]
server-id              = 2
# activate master bin log, if this slave might be a master later 
log_bin                = /var/log/mysql/mysql-bin.log

systemctl restart mariadb 
## auf dem master mit rsync rüberschrieben 
## root@master 
rsync -e ssh -avP /etc/mysql/mariadb.conf.d/z_uniruhr.cnf kurs@10.10.9.144:/home/kurs/
## root@slave 
mv /home/kurs/z_uniruhr.cnf /etc/mysql/mariadb.conf.d/
chown root:root /etc/mysql/mariadb.conf.d 
systemctl restart mariadb 

```

## Walkthrough 

https://mariadb.com/kb/en/setting-up-a-replication-slave-with-mariabackup/
