# Query Plans AKA explain 

   * Query Plans are the same as Query Execution Plans (QEP's) 
   * You will see the Query Plan's with explain 
   
## Example 

```
mysql> explain select * from recipients where recipient_id > 1 and recipient_id < 5;
+----+-------------+------------+------------+-------+---------------+---------+---------+------+------+----------+-------------+
| id | select_type | table      | partitions | type  | possible_keys | key     | key_len | ref  | rows | filtered | Extra       |
+----+-------------+------------+------------+-------+---------------+---------+---------+------+------+----------+-------------+
|  1 | SIMPLE      | recipients | NULL       | range | PRIMARY       | PRIMARY | 4       | NULL |    1 |   100.00 | Using where |
+----+-------------+------------+------------+-------+---------------+---------+---------+------+------+----------+-------------+
1 row in set, 1 warning (0.01 sec)
```

## Output-Format json 

```
-- includes costs 
EXPLAIN format=json SELECT * from audit_log WHERE yr in (2011,2012);
```

## Select_Type 
  
  * simple = one table 


## Types (in order of performance

### system 

```
Only one row in table is present (only one insert) 
```

### const only one result 

```
 EXPLAIN select contribution_id  from contributions where contribution_id = 262611;
+----+-------------+---------------+------------+-------+---------------+---------+---------+-------+------+----------+-------------+
| id | select_type | table         | partitions | type  | possible_keys | key     | key_len | ref   | rows | filtered | Extra       |
+----+-------------+---------------+------------+-------+---------------+---------+---------+-------+------+----------+-------------+
|  1 | SIMPLE      | contributions | NULL       | const | PRIMARY       | PRIMARY | 4       | const |    1 |   100.00 | Using index |
+----+-------------+---------------+------------+-------+---------------+---------+---------+-------+------+----------+-------------+
1 row in set, 1 warning (0.00 sec)

```

### ALL - Full table scan. (slowest) 

EXPLAIN select * from contributions where vendor_last_name like 'W%';
+----+-------------+---------------+------------+------+---------------+------+---------+------+---------+----------+-------------+
| id | select_type | table         | partitions | type | possible_keys | key  | key_len | ref  | rows    | filtered | Extra       |
+----+-------------+---------------+------------+------+---------------+------+---------+------+---------+----------+-------------+
|  1 | SIMPLE      | contributions | NULL       | ALL  | NULL          | NULL | NULL    | NULL | 2028240 |    11.11 | Using where |
+----+-------------+---------------+------------+------+---------------+------+---------+------+---------+----------+-------------+
1 row in set, 1 warning (0.00 sec)


## Extra 

### Using index - cover index is used 

```
Looking data in index is sufficient 
- no lookup of data on disk is necessary 
```

```
mysql> EXPLAIN select contribution_id  from contributions where contribution_id = 262611;
+----+-------------+---------------+------------+-------+---------------+---------+---------+-------+------+----------+-------------+
| id | select_type | table         | partitions | type  | possible_keys | key     | key_len | ref   | rows | filtered | Extra       |
+----+-------------+---------------+------------+-------+---------------+---------+---------+-------+------+----------+-------------+
|  1 | SIMPLE      | contributions | NULL       | const | PRIMARY       | PRIMARY | 4       | const |    1 |   100.00 | Using index |
+----+-------------+---------------+------------+-------+---------------+---------+---------+-------+------+----------+-------------+
1 row in set, 1 warning (0.00 sec)

mysql> show warnings;
+-------+------+--------------------------------------------------------------------------------------------------+
| Level | Code | Message                                                                                          |
+-------+------+--------------------------------------------------------------------------------------------------+
| Note  | 1003 | /* select#1 */ select '262611' AS `contribution_id` from `contributions`.`contributions` where 1 |
+-------+------+--------------------------------------------------------------------------------------------------+
1 row in set (0.00 sec)



