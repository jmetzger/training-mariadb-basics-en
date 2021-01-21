# Questions and answers.

## 1. Do you recommend Aurora

```
In my current humble opinion Aurora is a double edged sword.
Aurora looks promising for scalablity, but a lot of stuff is modified
mysql-stuff and in my opinion has a lot of restrictions.

You should be aware, that moving to Aurora might be a tasks
and reverting back even more.
```

   * Refer to: https://ahmedahamid.com/aurora-mysql/

I would like to point you to a performance measurement report here:

   * https://galeracluster.com/2019/09/everdata-reports-galera-cluster-outshines-amazon-aurora-and-rds/

## 2. Get rid of unattended - upgrades problem (dirty hack) 

```
ps aux | grep unatt
kill <process-id-von-unattended-upgrades>
```

## 3. Archive Data 

```

https://www.percona.com/doc/percona-toolkit/LATEST/pt-archiver.html
```

## 4. Does innodb do defragmentation by itself ?

```
# Some background while doing research.
# Nil performance benefits of defragmentation in index.
https://stackoverflow.com/questions/48569979/mariadb-table-defragmentation-using-optimize
```

## 5. Defragmentation 

```
# Optimize table 
ALTER TABLE contributions engine = InnoDB 


# mariadb has a patch for defragmentation  
https://mariadb.org/defragmenting-unused-space-on-innodb-tablespace/

# alter table xyz engine=InnoDB - defragements 
# but is also invasive.
# with ibdata1 innodb_file_per_table it lets the size grow


```

## 6. Is it possible to do select, update, deletes without using innodb_buffer in specific 

```
No, this is not possible 
```

## 7. Unit test framework in MySQL 

```
No, there is no testing framework with MySQL 
```

## 8. MariaDB - Advantages

  * flashback 
  * Verschlüsselung von Tabellen // mariabackup 
  * Einige Storage Engine (Aria -> MyISAM - crash-recovery) 
  * JSON anders implementiert 
  * galera 
  * feature: defragementation 
  
  ```
  MysqL 8 does not:
  decode 
  set profiling (still available but deprecated )
  ```
  
## 9. Select without locking 

  ``` 
  SET TRANSACTION ISOLATION LEVEL READ UNCOMMITTED ;
  BEGIN ;
  SELECT * FROM TABLE_NAME ;
  COMMIT ;
  ```

