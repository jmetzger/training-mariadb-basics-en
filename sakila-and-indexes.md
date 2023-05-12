# Sakila and indexes (Example session) 

```
use sakila;
select * from actor;

show create table from actor;
show indexes from actor; 

```

## Index is being used (System can only read indexes from left to right)

```
select * from actor where last_name like 'A%';
explain select * from actor where last_name like 'A%';

+------+-------------+-------+-------+---------------------+---------------------+---------+------+------+-----------------------+
| id   | select_type | table | type  | possible_keys       | key                 | key_len | ref  | rows | Extra                 |
+------+-------------+-------+-------+---------------------+---------------------+---------+------+------+-----------------------+
|    1 | SIMPLE      | actor | range | idx_actor_last_name | idx_actor_last_name | 182     | NULL | 7    | Using index condition |
+------+-------------+-------+-------+---------------------+---------------------+---------+------+------+-----------------------+
1 row in set (0.000 sec)

```

## Index cannot be used, because index would need to be read from right to left (and cannot) 

```
select * from actor where last_name like '%N';
explain select * from actor where last_name like '%N';

-- NO INDEX BEIG USED -> type -> ALL -> which means table scan (looking into every single line in the table) 
+------+-------------+-------+------+---------------+------+---------+------+------+-------------+
| id   | select_type | table | type | possible_keys | key  | key_len | ref  | rows | Extra       |
+------+-------------+-------+------+---------------+------+---------+------+------+-------------+
|    1 | SIMPLE      | actor | ALL  | NULL          | NULL | NULL    | NULL | 200  | Using where |
+------+-------------+-------+------+---------------+------+---------+------+------+-------------+
1 row in set (0.000 sec)


```

## Creating index for better performance 

```
use sakila;
create table actor2 as select * from actor;
explain select * from actor2 where first_name like 'D%';

create index idx_actor2_first_name on actor2 (first_name);
show indexes from actor2;
-- index is used 
explain select * from actor2 where first_name like 'D%';
```

```
-- output 
+--------+------------+-----------------------+--------------+-------------+-----------+-------------+----------+--------+------+------------+---------+---------------+---------+
| Table  | Non_unique | Key_name              | Seq_in_index | Column_name | Collation | Cardinality | Sub_part | Packed | Null | Index_type | Comment | Index_comment | Ignored |
+--------+------------+-----------------------+--------------+-------------+-----------+-------------+----------+--------+------+------------+---------+---------------+---------+
| actor2 |          1 | idx_actor2_first_name |            1 | first_name  | A         |         201 |     NULL | NULL   |      | BTREE      |         |               | NO      |
+--------+------------+-----------------------+--------------+-------------+-----------+-------------+----------+--------+------+------------+---------+---------------+---------+
1 row in set (0.001 sec)

MariaDB [sakila]> explain select * from actor2 where first_name like 'D%';
+------+-------------+--------+-------+-----------------------+-----------------------+---------+------+------+-----------------------+
| id   | select_type | table  | type  | possible_keys         | key                   | key_len | ref  | rows | Extra                 |
+------+-------------+--------+-------+-----------------------+-----------------------+---------+------+------+-----------------------+
|    1 | SIMPLE      | actor2 | range | idx_actor2_first_name | idx_actor2_first_name | 182     | NULL | 7    | Using index condition |
+------+-------------+--------+-------+-----------------------+-----------------------+---------+------+------+-----------------------+
1 row in set (0.000 sec)
```

