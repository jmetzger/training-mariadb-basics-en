# Describe and indexes 

## Walkthrough 

### Step 1:

```
# Database  and Table with primary key
create database descindex;
use descindex; 
create table people (id int unsigned auto_increment, first_name varchar(25), last_name varchar(25), primary key (id), passcode mediumint unsigned);
# add an index 
# This will always !! translate into an alter statement. 
create index idx_last_name_first_name on people (last_name,first_name) 
# 
create unique index idx_passcode on people (passcode)   

desc people;
+------------+-----------------------+------+-----+---------+----------------+
| Field      | Type                  | Null | Key | Default | Extra          |
+------------+-----------------------+------+-----+---------+----------------+
| id         | int(10) unsigned      | NO   | PRI | NULL    | auto_increment |
| first_name | varchar(25)           | YES  |     | NULL    |                |
| last_name  | varchar(25)           | YES  |     | NULL    |                |
| passcode   | mediumint(8) unsigned | YES  |     | NULL    |                |
+------------+-----------------------+------+-----+---------+----------------+
4 rows in set (0.01 sec)
```

### Step 2: 

```
# Add simple combined index on first_name, last_name 
create index idx_first_name_last_name on people (first_name, last_name);
Query OK, 0 rows affected (0.05 sec)
Records: 0  Duplicates: 0  Warnings: 0
desc people;

-- show the column where the combined index starts (MUL = Multi) 

+------------+-----------------------+------+-----+---------+----------------+
| Field      | Type                  | Null | Key | Default | Extra          |
+------------+-----------------------+------+-----+---------+----------------+
| id         | int(10) unsigned      | NO   | PRI | NULL    | auto_increment |
| first_name | varchar(25)           | YES  | MUL | NULL    |                |
| last_name  | varchar(25)           | YES  |     | NULL    |                |
| passcode   | mediumint(8) unsigned | YES  |     | NULL    |                |
+------------+-----------------------+------+-----+---------+----------------+
4 rows in set (0.01 sec)


```

### Step 3:

```
# Add a unique index on passcode 
create index idx_passcode on people (passcode) 
mysql> desc people;

-- Line with UNI shows this indexes. 
+------------+-----------------------+------+-----+---------+----------------+
| Field      | Type                  | Null | Key | Default | Extra          |
+------------+-----------------------+------+-----+---------+----------------+
| id         | int(10) unsigned      | NO   | PRI | NULL    | auto_increment |
| first_name | varchar(25)           | YES  | MUL | NULL    |                |
| last_name  | varchar(25)           | YES  |     | NULL    |                |
| passcode   | mediumint(8) unsigned | YES  | UNI | NULL    |                |
+------------+-----------------------+------+-----+---------+----------------+
4 rows in set (0.01 sec)
```


### Step 4: 

```
# Get to know all your indexes on a table 
show indexes for people 
mysql> show index from people;
+--------+------------+--------------------------+--------------+-------------+-----------+-------------+----------+--------+------+------------+---------+---------------+
| Table  | Non_unique | Key_name                 | Seq_in_index | Column_name | Collation | Cardinality | Sub_part | Packed | Null | Index_type | Comment | Index_comment |
+--------+------------+--------------------------+--------------+-------------+-----------+-------------+----------+--------+------+------------+---------+---------------+
| people |          0 | PRIMARY                  |            1 | id          | A         |           0 |     NULL | NULL   |      | BTREE      |         |               |
| people |          0 | idx_passcode             |            1 | passcode    | A         |           0 |     NULL | NULL   | YES  | BTREE      |         |               |
| people |          1 | idx_first_name_last_name |            1 | first_name  | A         |           0 |     NULL | NULL   | YES  | BTREE      |         |               |
| people |          1 | idx_first_name_last_name |            2 | last_name   | A         |           0 |     NULL | NULL   | YES  | BTREE      |         |               |
+--------+------------+--------------------------+--------------+-------------+-----------+-------------+----------+--------+------+------------+---------+---------------+
4 rows in set (0.01 sec)

