# Install sakila - test - database 

```

cd /usr/src
wget https://downloads.mysql.com/docs/sakila-db.tar.gz
tar xvf sakila-db.tar.gz
cd sakila-db/
ls -la
mysql < sakila-schema.sql 
mysql < sakila-data.sql 
# verify - database is present 
mysql -e 'show databases;';

```
