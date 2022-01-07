# Backup / Restore over the network 

## Assumptions 

```
Server 1: 192.168.1.1
Server 2: 192.168.1.2

Create new db -> sakilaremote on server 1
Backup data from sakila on server2 and send to server 1 

```

## Preparation (on server 1) 

```
# is server listening to the outside world
lsof -i | grep mysql 

# create user on server 
mysql>create user ext@'%' identified by 'mysecretpass'
mysql>grant all on *.* to ext@'%' 

```

## Testing (on server 1) 

```
mysql -uext -p -h 192.168.1.1 
mysql>create schema sakilaremote 

```

## Executing (on server 2) 

```
mysqldump sakila | mysql -uext -p -h 192.168.1.1 sakilremote 
```

## Validating (on server 2) 

```
mysql -uext -p -h 192.168.1.1 
mysql> use sakilaremote;
mysql> show tables;

```
