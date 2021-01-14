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
