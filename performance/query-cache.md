# Query Cache 

## Performance query cache 

  * Always try to optimize innodb with disabled query cache first (innodb_buffer_pool) 
  * If you use query_cache system can only use on CPU-Core. !! 
  
## How to enable query cache 

```
# have_query_cache means compiled in mysql 
# query_cache_type off means not enable by config
-- query cache is diabled 
mysql> show variables like '%query_cache%';
+------------------------------+---------+
| Variable_name                | Value   |
+------------------------------+---------+
| have_query_cache             | YES     |
| query_cache_limit            | 1048576 |
| query_cache_min_res_unit     | 4096    |
| query_cache_size             | 1048576 |
| query_cache_type             | OFF     |
| query_cache_wlock_invalidate | OFF     |
+------------------------------+---------+
6 rows in set (0.01 sec)

root@trn01:/etc/mysql/mysql.conf.d# tail mysqld.cnf
[mysqld]
pid-file        = /var/run/mysqld/mysqld.pid
socket          = /var/run/mysqld/mysqld.sock
datadir         = /var/lib/mysql
log-error       = /var/log/mysql/error.log
# By default we only accept connections from localhost
bind-address    = 0.0.0.0
# Disabling symbolic-links is recommended to prevent assorted security risks
symbolic-links=0
query-cache-type=1

systemctl restart mysql 

mysql> show variables like '%query_cache%';
+------------------------------+---------+
| Variable_name                | Value   |
+------------------------------+---------+
| have_query_cache             | YES     |
| query_cache_limit            | 1048576 |
| query_cache_min_res_unit     | 4096    |
| query_cache_size             | 1048576 |
| query_cache_type             | ON      |
| query_cache_wlock_invalidate | OFF     |
+------------------------------+---------+
6 rows in set (0.01 sec)


mysql> show status like '%Qcache%';
+-------------------------+---------+
| Variable_name           | Value   |
+-------------------------+---------+
| Qcache_free_blocks      | 1       |
| Qcache_free_memory      | 1031832 |
| Qcache_hits             | 0       |
| Qcache_inserts          | 0       |
| Qcache_lowmem_prunes    | 0       |
| Qcache_not_cached       | 0       |
| Qcache_queries_in_cache | 0       |
| Qcache_total_blocks     | 1       |
+-------------------------+---------+
8 rows in set (0.00 sec)

# status in session zurücksetzen. 
mysql> flush status;
Query OK, 0 rows affected (0.00 sec)

```

## Performance bottleneck - mutex 

https://mariadb.com/de/resources/blog/flexible-mariadb-server-query-cache/

```

```

## Something planned ?

  * Nope ;o( Demand is new  
  * You might be able to use Demand together with maxscale 
  * Refer to: 
  https://mariadb.com/de/resources/blog/flexible-mariadb-server-query-cache/
  
  
  ```
  A mutual exclusion object (mutex) is a programming object that allows multiple program threads to share a resource (such as a folder) but not simultaneously. Mutex is set to unlock when the data is no longer needed or when a routine is finished. Mutex creates a bottleneck effect. The blocking means only one query can look at the Query Cache at a time and other queries must wait. A query that must wait to look in the cache only to find it isn’t in the cache will be slowed instead of being accelerated.
  ```
