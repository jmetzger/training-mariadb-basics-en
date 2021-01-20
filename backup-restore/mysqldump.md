# mysqldump 

## Useful options for PIT 

```
# —quick not needed, because included in —opt which is enabled by default 
mysqldump —-all-databases —-single-transaction —-gtid —-master-data=2 —-routines 
--events —-flush-logs > /usr/src/all-databases.sql 
```
