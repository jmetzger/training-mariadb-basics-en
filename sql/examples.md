# SQL-Examples 

```
# Connect to the server with mysql-client
mysql
```
## Create database/table and inserting 

```
create database training;
show databases;
use training;
create table courses (id smallint, name varchar(80), primary key(id));
insert into courses (id,name) values (2,'MariaDB Administration');
```

## Administrative Commands 


```
use mysql;
show tables;

# Want to know more about a specific table
show create table user;
```

