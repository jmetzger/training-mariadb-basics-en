# Change structure with alter 

## Example - Step 1: Create structure first 

```
-- done within the mysql interface 
create database training;
use training;

CREATE TABLE courses (
  id smallint(6) NOT NULL,
  name varchar(80) DEFAULT NULL,
  PRIMARY KEY (id)
);

show tables;
show create table courses;
```

## Example - Step 2: Modify structure 

```
ALTER TABLE courses ADD room VARCHAR(40), ADD price DECIMAL(5,2);
ALTER TABLE courses MODIFY price DECIMAL(6,2);
```
