# When to use mysql and when mariadb ? 

## What specfic feature set do you need from MariaDB or MySQL 

## MariaDB 

  * Should use it, when you want to use Galera Cluster 
  * Why ? Because the patch for galera (wsrep-patch) is not in MySQL be default 
    * https://galeracluster.com/downloads/#downloads (alternative for mysql) 
  * But: Galera does not work on Windows
  * Oracle Mode for the procedures (but not implemented) well.   

## MySQL 

  * Windows: Group Replication which mainly nearly the same as the cluster but available with Windows 
  * If you want to use Online Physical you need to have subscription (mysqlbackup) 
 
## Cluster (MySQL: group replication) ? MariaDB or MySQL 

  * Always go for galera if possible 

### Why ? 

  * Because galera has 14 years of experience under their belt (group replication was invented way later) 
  * It is rock solid and they are spending time, to make easier and easier to setup on each iteration 
  * And on windows you have a lot components, which makes things unclear (e.g. Group Replication, InnoDB Cluster on top) 

## How to decide ?

  * Look for the feature you specifically need (cutting edge) and if they are implement in mysql or mariadb 
  * Important: If you are on system it is hard to move to the other as time goes by (as they divert over time
    - especially, when using cutting edge features)
  
## Working with a software from a specific Vendor 

  * What support do they have ? 
 
## Flashback (MariaDB) 

```
DML - Insert / Update -- Revert the 20 minutes from your data, but only DML 
```


