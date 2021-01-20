# Mariabackup 

## Walkthrough 

```
# user eintrag in /root/.my.cnf
[mariabackup]
user=root 
# pass is not needed here, because we have the user root with unix_socket - auth 

mkdir /backups 
# target-dir needs to be empty or not present 
mariabackup --target-dir=/backups/20210120 --backup 
# apply ib_logfile0 to tablespaces 
# after that ib_logfile0 ->  0 bytes 
mariabackup --target-dir=/backups/20210120 --prepare 

## Recover 
systemctl stop mariadb 
mv /var/lib/mysql /var/lib/mysql.bkup 
mariabackup --target-dir=/backups/20200120 --copy-back 
chmod -R mysql:mysql /var/lib/mysql
systemctl start mariadb 
```

## Ref. 
https://mariadb.com/kb/en/full-backup-and-restore-with-mariabackup/
