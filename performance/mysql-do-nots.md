# MySQL Dont's - performance 

## 1. No function in where (column_name) 

```
# Never use a function for the column name in where 
# e.g. 
select * from donors where upper(last_name) like 'Willia%'
```
