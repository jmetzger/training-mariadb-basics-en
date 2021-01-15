# Joins and Indexes 

## Take a look which order the optimizer uses 


### With date

```
-- Using a date which has no index 
-- Needs to do a table scan 
explain select c.* from contributions c join donors d using (donor_id) join recipients r using (recipient_id) where c.date_recieved > '1999-12-01' and c.date_recieved < '2000-07-01';
+----+-------------+-------+------------+--------+-------------------------+---------+---------+------------------------------+---------+----------+-------------+
| id | select_type | table | partitions | type   | possible_keys           | key     | key_len | ref                          | rows    | filtered | Extra       |
+----+-------------+-------+------------+--------+-------------------------+---------+---------+------------------------------+---------+----------+-------------+
|  1 | SIMPLE      | c     | NULL       | ALL    | donor_idx,recipient_idx | NULL    | NULL    | NULL                         | 2028240 |    11.11 | Using where |
|  1 | SIMPLE      | r     | NULL       | eq_ref | PRIMARY                 | PRIMARY | 4       | contributions.c.recipient_id |       1 |   100.00 | Using index |
|  1 | SIMPLE      | d     | NULL       | eq_ref | PRIMARY                 | PRIMARY | 4       | contributions.c.donor_id     |       1 |   100.00 | Using index |
+----+-------------+-------+------------+--------+-------------------------+---------+---------+------------------------------+---------+----------+-------------+
3 rows in set, 1 warning (0.00 sec)

60626 rows in set (7.22 sec)
```

### With date and filter on donor 

```
 explain select c.*,d.last_name from contributions c join donors d using (donor_id) join recipients r using (recipient_id)
where c.date_recieved > '1999-12-01' and c.date_recieved < '2000-07-01' and d.last_name like 'A%';
+----+-------------+-------+------------+--------+---------------------------+-------------------+---------+------------------------------+-------+----------+--------------------------+
| id | select_type | table | partitions | type   | possible_keys             | key               | key_len | ref                          | rows  | filtered | Extra                    |
+----+-------------+-------+------------+--------+---------------------------+-------------------+---------+------------------------------+-------+----------+--------------------------+
|  1 | SIMPLE      | d     | NULL       | range  | PRIMARY,donors_donor_info | donors_donor_info | 213     | NULL                         | 65894 |   100.00 | Using where; Using index |
|  1 | SIMPLE      | c     | NULL       | ref    | donor_idx,recipient_idx   | donor_idx         | 5       | contributions.d.donor_id     |     2 |    11.11 | Using where              |
|  1 | SIMPLE      | r     | NULL       | eq_ref | PRIMARY                   | PRIMARY           | 4       | contributions.c.recipient_id |     1 |   100.00 | Using index              |
+----+-------------+-------+------------+--------+---------------------------+-------------------+---------+------------------------------+-------+----------+--------------------------+
3 rows in set, 1 warning (0.00 sec)
```

### With date and filter on donor, less specific 
```
select c.*,d.* from contributions c join donors d using (donor_id) join recipients r using (recipient_id) where c.date_recieved > '1999-12-01' and c.date_recieved < '2000-07-01' and d.last_name like 'A%';
 explain select c.*,d.* from contributions c join donors d using (donor_id) join recipients r using (recipient_id) where c.date_recieved > '1999-12-01' and c.date_recieved < '2000-07-01' and d.last_name like 'A%';
+----+-------------+-------+------------+--------+---------------------------+-------------------+---------+------------------------------+-------+----------+-----------------------+
| id | select_type | table | partitions | type   | possible_keys             | key               | key_len | ref                          | rows  | filtered | Extra                 |
+----+-------------+-------+------------+--------+---------------------------+-------------------+---------+------------------------------+-------+----------+-----------------------+
|  1 | SIMPLE      | d     | NULL       | range  | PRIMARY,donors_donor_info | donors_donor_info | 213     | NULL                         | 65894 |   100.00 | Using index condition |
|  1 | SIMPLE      | c     | NULL       | ref    | donor_idx,recipient_idx   | donor_idx         | 5       | contributions.d.donor_id     |     2 |    11.11 | Using where           |
|  1 | SIMPLE      | r     | NULL       | eq_ref | PRIMARY                   | PRIMARY           | 4       | contributions.c.recipient_id |     1 |   100.00 | Using index           |
+----+-------------+-------+------------+--------+---------------------------+-------------------+---------+------------------------------+-------+----------+-----------------------+
3 rows in set, 1 warning (0.00 sec)


```

### With date and filter on donor and filter on recipient 
```
mysql> explain select c.*,d.last_name,r.* from contributions c join donors d using (donor_id) join recipients r using (recipient_
id) where c.date_recieved > '1999-12-01' and c.date_recieved < '2000-07-01' and d.last_name like 'A%' and r.name like 'Cit%';
+----+-------------+-------+------------+--------+---------------------------+---------------+---------+------------------------------+------+----------+-------------+
| id | select_type | table | partitions | type   | possible_keys             | key           | key_len | ref                          | rows | filtered | Extra       |
+----+-------------+-------+------------+--------+---------------------------+---------------+---------+------------------------------+------+----------+-------------+
|  1 | SIMPLE      | r     | NULL       | ALL    | PRIMARY                   | NULL          | NULL    | NULL                         | 6063 |    11.11 | Using where |
|  1 | SIMPLE      | c     | NULL       | ref    | donor_idx,recipient_idx   | recipient_idx | 5       | contributions.r.recipient_id |  305 |    11.11 | Using where |
|  1 | SIMPLE      | d     | NULL       | eq_ref | PRIMARY,donors_donor_info | PRIMARY       | 4       | contributions.c.donor_id     |    1 |     9.39 | Using where |
+----+-------------+-------+------------+--------+---------------------------+---------------+---------+------------------------------+------+----------+-------------+
3 rows in set, 1 warning (0.00 sec)


```
