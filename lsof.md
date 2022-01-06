# Find out, if mariadb is listening to the outside world 


## not the case 

```
lsof -i 
# or 
netstat -ant
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN    

# <- in this case not - localhost 

```

## Yes ! 

```
# ubuntu 20.04
# change to listen on all interfaces 
# vi /etc/mariadb-conf.d/50-server.cnf 
# this is only for the mysqld standalone daemon
[mysqld]
bind-address = 0.0.0.0

# restart
systemctl restart mariadb 

lsof -i 
# connect to the server by external interface (e.g.  eth0 ) 
mysql -h 10.0.3.3 


```
