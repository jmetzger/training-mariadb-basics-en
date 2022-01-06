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

# Yes ! 

```

```
