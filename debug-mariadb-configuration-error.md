# Debug Service 

## Producing 

```
# make an nonsense entry 
/etc/mysql/mariadb.conf.d/50-server.cnf 
[mysqld]
nonsense 
```


## Walkthrough 

```
# Service is not restarting - error giving
systemctl restart mariadb.service 

# Step 1 : status -> what do the logs tell (last 10 lines) 
systemctl status mariadb.service 

# no findings -> step 2:
journalctl -xe

# no findings -> step 3:
journalctl -u mariadb.service 
# or journalctl -u mariadb 

# no findings -> step 4:
# search specific log for service 
# and eventually need to increase the log level
# e.g. with mariadb (find through internet research)
less /var/log/mysql/error.log 

# Didn't find something -> step 5 
# General Log 
# Debian/Ubuntu 
/var/log/syslog
# REdhat/Centos 
/var/log/messages 
```

## Find errors in logs quickly

```
cd /var/log/mysql 
# -i = case insensitive // no matter if capital or lower letters 
cat error.log | grep -i error
```

