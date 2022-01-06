# Server System Variables 

```
MariaDB [(none)]> show global variables like '%long%';
+--------------------------------------------------------+-----------+
| Variable_name                                          | Value     |
+--------------------------------------------------------+-----------+
| deadlock_search_depth_long                             | 15        |
| deadlock_timeout_long                                  | 50000000  |
| long_query_time                                        | 10.000000 |
| max_long_data_size                                     | 16777216  |
| performance_schema_events_stages_history_long_size     | -1        |
| performance_schema_events_statements_history_long_size | -1        |
| performance_schema_events_waits_history_long_size      | -1        |
+--------------------------------------------------------+-----------+
7 rows in set (0.001 sec)

MariaDB [(none)]> select @@long_query_Time
    -> ;
+-------------------+
| @@long_query_Time |
+-------------------+
|         10.000000 |
+-------------------+
1 row in set (0.000 sec)

MariaDB [(none)]> select @@long_query_time
    -> ;
+-------------------+
| @@long_query_time |
+-------------------+
|         10.000000 |
+-------------------+
1 row in set (0.000 sec)

MariaDB [(none)]> select @@GLOBAL.long_query_time
    -> ;
+--------------------------+
| @@GLOBAL.long_query_time |
+--------------------------+
|                10.000000 |
+--------------------------+
1 row in set (0.000 sec)

MariaDB [(none)]> select @@global.long_query_time
    -> ;
+--------------------------+
| @@global.long_query_time |
+--------------------------+
|                10.000000 |
+--------------------------+
1 row in set (0.000 sec)

 

```
