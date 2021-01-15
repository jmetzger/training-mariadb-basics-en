# Lock tables - Example 

## Example 

```
mysql> LOCK TABLES people write,people_data write;
Query OK, 0 rows affected (0.00 sec)

mysql> UNLOCK TABLES
    -> ;
Query OK, 0 rows affected (0.00 sec)


# LOCK TABLES .... WRITE 
-- We cannot read + write in other session  

# LOCK TABLES ..... READ 
-- We cannot write, but read in other session 


```
