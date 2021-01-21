# Setting up new slave with master-slave replication 

## Step 1: mariabackup on master 

```
mkdir /backups 
# target-dir needs to be empty or not present 
mariabackup --target-dir=/backups/20210121 --backup 
# apply ib_logfile0 to tablespaces 
# after that ib_logfile0 ->  0 bytes 
mariabackup --target-dir=/backups/20210121 --prepare 
```




## Walkthrough 

https://mariadb.com/kb/en/setting-up-a-replication-slave-with-mariabackup/
