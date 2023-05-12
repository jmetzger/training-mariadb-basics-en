# Mariabackup 

## Installation (Ubuntu/Debian) 

```
apt install mariadb-backup 
```

## Walkthrough (Backup) 

```
# user eintrag in /root/.my.cnf
vi /root/.my.cnf
```

```
[mariabackup]
user=root 
# pass is not needed here, because we have the user root with unix_socket - auth 
```

```
mkdir /backups 
# target-dir needs to be empty or not present 
mariabackup --target-dir=/backups/20230511 --backup 
# apply ib_logfile0 to tablespaces 
# after that ib_logfile0 ->  0 bytes 
mariabackup --target-dir=/backups/20230511 --prepare 
```

## Walkthrough (Recover) 

```
systemctl stop mariadb 
mv /var/lib/mysql /var/lib/mysql.bkup 
mariabackup --target-dir=/backups/20230511 --copy-back 
chown -R mysql:mysql /var/lib/mysql
systemctl start mariadb 
```



## Ref. 
https://mariadb.com/kb/en/full-backup-and-restore-with-mariabackup/
