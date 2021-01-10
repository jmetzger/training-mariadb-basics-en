# Index and functions 

## No index can be used on an index:

```
explain select * from actor where upper(last_name) like 'A%';
+----+-------------+-------+------------+------+---------------+------+---------+------+------+----------+-------------+
| id | select_type | table | partitions | type | possible_keys | key  | key_len | ref  | rows | filtered | Extra       |
+----+-------------+-------+------------+------+---------------+------+---------+------+------+----------+-------------+
|  1 | SIMPLE      | actor | NULL       | ALL  | NULL          | NULL | NULL    | NULL |  200 |   100.00 | Using where |
+----+-------------+-------+------------+------+---------------+------+---------+------+------+----------+-------------+
```

## Workaround with virtual columns (possible since mysql 5.7) 

```
# 1. Create Virtual Column with upper 
alter table sakila add idx_last_name_upper varchar(45) GENERATED ALWAYS AS upper(last_name);
# 2. Create an index on that column 
create index idx_last_name_upper on actor (last_name_upper);
```

## Now we try to search the very same 

```
explain select * from actor where last_name_upper like 'A%';
+----+-------------+-------+------------+-------+---------------------+---------------------+---------+------+------+----------+-------------+
| id | select_type | table | partitions | type  | possible_keys       | key                 | key_len | ref  | rows | filtered | Extra       |
+----+-------------+-------+------------+-------+---------------------+---------------------+---------+------+------+----------+-------------+
|  1 | SIMPLE      | actor | NULL       | range | idx_last_name_upper | idx_last_name_upper | 183     | NULL |    7 |   100.00 | Using where |
+----+-------------+-------+------------+-------+---------------------+---------------------+---------+------+------+----------+-------------+
1 row in set, 1 warning (0.00 sec)

```




## Preview MysQL 8 

  * MySQL 8 support functional indexes 
