# Examples insert/update/delete

## Prerequisites 

[setup database and table](/sql/alter-change-structure.md)

## INSERT 

```
-- only the case in mysql (in php using the appropriate php command to use specific database 
use training; 
```
```
INSERT INTO courses (id,name) values (1,'Galera Training');
INSERT INTO courses (id,name,room,price) values (2,'MariaDB Administration','Bukarest',1000.50);
-- better in terms of performance then select * FROM 
-- showing all
SELECT id,name FROM courses;
SELECT id,name FROM courses WHERE id = 2;
```

## UPDATE 

```
UPDATE courses SET room='Berlin',price=800.7555 WHERE id = 1;
```

## DELETE 

```
DELETE FROM courses WHERE id = 2;
```

## TRUNCATE (will delete all data) 

```
TRUNCATE courses;
```

