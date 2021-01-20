# mysqldump 

## Useful options for PIT 

```
# —quick not needed, because included in —opt which is enabled by default 

# on local systems using socket, there are no huge benefits concerning --compress
# when you dump over the network use it for sure 
mysqldump --all-databases --single-transaction --gtid --master-data=2 --routines --events --flush-logs --compress > /usr/src/all-databases.sql;
```

## Version with zipping 

```
mysqldump —-all-databases —-single-transaction —-gtid —-master-data=2 —-routines 
--events —-flush-logs --compress | gzip > /usr/src/all-databases.sql.gz  
```
