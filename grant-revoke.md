# Grant / Revoke / Create User 

## Create user 

```
create user training@localhost identified by 'yourpassword';
```

## Drop user (=delete user) 

```
drop user training@localhost 
```

## Change User (e.g. change authentication) 

```
# change pass
alter user training@localhost identified by 'newpassword';
```

## Set global or db rights for a user 

```
grant all on *.* to training@localhost
# only a specific db 
grant all on mydb.* to training@localhost 
```

## Revoke global or revoke right from a user 

```
revoke select on *.* from training@localhost 
# only from a specific db 
revoke select on training.* from training@localhost 
```

## Useful command to find out users:

```
select user,host from mysql.user;
```


## Refs:

  * https://mariadb.com/kb/en/grant/#the-grant-option-privilege
  * https://mariadb.com/kb/en/revoke/
