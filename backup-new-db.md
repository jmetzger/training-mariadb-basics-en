# Backup (and create new db based on data) 

```
mysqldump sakila > sakila.sql 
mysql -e 'create schema sakilanew'
# or
echo "create schema sakilanew" | mysql 

mysql sakilanew < sakila.sql 


```
