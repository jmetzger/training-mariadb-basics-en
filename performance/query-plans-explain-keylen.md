# Query Plan Explain -> key_len 

## Example 

```
 select table_schema,table_name,character_set_name,column_name from information_schema.columns where table_name = 'donors'
and column_name = 'city';
+---------------+------------+--------------------+-------------+
| table_schema  | table_name | character_set_name | column_name |
+---------------+------------+--------------------+-------------+
| contributions | donors     | utf8               | city        |
+---------------+------------+--------------------+-------------+
1 row in set (0.00 sec)
```

```
mysql> describe donors;
+--------------------+-------------+------+-----+---------+----------------+
| Field              | Type        | Null | Key | Default | Extra          |
+--------------------+-------------+------+-----+---------+----------------+
| donor_id           | int(11)     | NO   | PRI | NULL    | auto_increment |
| last_name          | varchar(70) | YES  | MUL | NULL    |                |
| first_name         | varchar(35) | YES  |     | NULL    |                |
| address_1          | varchar(35) | YES  |     | NULL    |                |
| address_2          | varchar(36) | YES  |     | NULL    |                |
| city               | varchar(20) | YES  | MUL | NULL    |                |
| state              | varchar(15) | YES  |     | NULL    |                |
| zip                | varchar(11) | YES  |     | NULL    |                |
| employer           | varchar(70) | YES  |     | NULL    |                |
| occupation         | varchar(40) | YES  |     | NULL    |                |
| last_name_reversed | varchar(70) | YES  | MUL | NULL    |                |
+--------------------+-------------+------+-----+---------+----------------+
11 rows in set (0.00 sec)
```

```
# only the first part of the combined index is used, because 213 bytes is a varchar(70) for utf8 - characters in index 
# utf8 takes up to 3 bytes per character.
mysql> explain select first_name,last_name from donors where last_name like 'Wi%';
+----+-------------+--------+------------+-------+-------------------+-------------------+---------+------+-------+----------+--------------------------+
| id | select_type | table  | partitions | type  | possible_keys     | key               | key_len | ref  | rows  | filtered | Extra                    |
+----+-------------+--------+------------+-------+-------------------+-------------------+---------+------+-------+----------+--------------------------+
|  1 | SIMPLE      | donors | NULL       | range | donors_donor_info | donors_donor_info | 213     | NULL | 18722 |   100.00 | Using where; Using index |
+----+-------------+--------+------------+-------+-------------------+-------------------+---------+------+-------+----------+--------------------------+
1 row in set, 1 warning (0.00 sec)

# both last_name and first_name are used to filter 
# 3 bytes + 70x3 (varchar(70)) + 3Bytes + 35x3 (varchar(35)) = 321  
mysql> explain select first_name,last_name from donors where last_name like 'Williams' and first_name like 'A%';
+----+-------------+--------+------------+-------+-------------------+-------------------+---------+------+------+----------+--------------------------+
| id | select_type | table  | partitions | type  | possible_keys     | key               | key_len | ref  | rows | filtered | Extra                    |
+----+-------------+--------+------------+-------+-------------------+-------------------+---------+------+------+----------+--------------------------+
|  1 | SIMPLE      | donors | NULL       | range | donors_donor_info | donors_donor_info | 321     | NULL |   46 |   100.00 | Using where; Using index |
+----+-------------+--------+------------+-------+-------------------+-------------------+---------+------+------+----------+--------------------------+
1 row in set, 1 warning (0.00 sec)

mysql>
```
