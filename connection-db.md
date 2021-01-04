# Connection to db 

## General Explanation 

 * Step 1: connection to db 
 * Step 2: using specific database 
 * 1. + 2. can be done in one step 
 
## Connection as Root (without using -u/--user and db) 

```
# If you are root and are connecting locally (socket), you do not need to enter a passwort on root
# Why ? 
mysql> use mysql
mysql> select user,host,plugin from user where user = 'root' and host = 'localhost';
```
```
root@mysql-server:~#whoami 
root 
# this work, because we are connecting locally
# by default mysql uses the user we are logged in with 
mysql 
```

## Connection with credentials

```
mysql -uroot -p  
# passwort auf der Kommandozeile eingeben 

```

## Connection to remote mysql - server 

```
mysql -u root -p -h 10.10.9.117
```

