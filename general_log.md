# General log 

## Activate during runtime 

```
# Hint hostname:  myserver 
mysql>set global general_log = 1 

ls -la /var/lib/mysql/myserver.log 

```
## Implications 

  * By default 
  * Will massively increase in size, because all queries are documented 

## Truncate while running 

```
# will be empty that 
cd /var/lib/mysql 
> myserver.log 

# and keeps on writing in there

# Attention
# Delete logfile does not work, needs restart 
# or 
# set global general_log = 0; set global general_log = 1 # after deletion 


```
