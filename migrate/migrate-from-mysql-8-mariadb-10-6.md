# Migrate from MySQL 8.x to MariaDB 10.6 

## Normal route 

```
1. Create a dump of mysql-dataase 

mysqldump --events --routings --all-databases > all-databases.sql 

2. Stop MySQL 

3. Uninstall mysql 

4. mv away data - folder 
mv /var/lib/mysql /var/lib/mysql.bkup 

5. Install mariadb 

6. Start mariadb (we should already be the case) 

7. Import data from 1. 

mysql < all-databases.sql 
```

## Problems you might 

```
* MySQL has a new password authentication mechanism 
// so probably you need to recreated all passwords 

* JSON - datatype are completely different 

* user database (double check if users are working) 

* Are you using specific feature set from MySQL 8.x 

* Are you using virtual columns ? 
```

```


