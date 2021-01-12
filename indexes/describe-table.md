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


