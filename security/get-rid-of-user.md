# Getting rid of user 

## Why ? 

  * You might have changed the grants, but they only reflect after a reconnect
 
## Howto 

```
# step 1: git thread_id id of user 
MariaDB [information_schema]> select id,user,host,command from processli
st where user='training';
+----+----------+-------------------+---------+
| id | user     | host              | command |
+----+----------+-------------------+---------+
| 75 | training | jochen-wt6y:42026 | Sleep   |
+----+----------+-------------------+---------+
1 row in set (0.001 sec)

# step 2: kill thread_id = connection_id  = id
kill 75

```
