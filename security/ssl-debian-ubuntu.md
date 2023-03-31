# ssl - mariadb - Ubuntu/Debian
## Variant 1: Setup 1-way ssl encryption 

### Create CA and Server-Key 

```

# On Server - create ca and certificates 
mkdir -p /etc/mysql/ssl; cd /etc/mysql/ssl

# create ca.  
openssl genrsa 4096 > ca-key.pem

# create ca-certificate 
# Common Name: MariaDB CA 
openssl req -new -x509 -nodes -days 365000 -key ca-key.pem -out ca-cert.pem

# create server-cert 
# Common Name: server1.training.local 
# Password: --- leave empty ----
openssl req -newkey rsa:2048 -days 365000 -nodes -keyout server-key.pem -out server-req.pem

# Next process the rsa - key 
openssl rsa -in server-key.pem -out server-key.pem

# Now sign the key 
openssl x509 -req -in server-req.pem -days 365000 -CA ca-cert.pem -CAkey ca-key.pem -set_serial 01 -out server-cert.pem

```

### Verify certificates 

```
openssl verify -CAfile ca-cert.pem server-cert.pem 


```

### Configure Server 
```
# create file 
# /etc/mysql/mariadb.conf.d/z_ssl.cnf 
[mysqld]
ssl-ca=/etc/mysql/ssl/ca-cert.pem
ssl-cert=/etc/mysql/ssl/server-cert.pem
ssl-key=/etc/mysql/ssl/server-key.pem
## Set up TLS version here. For example TLS version 1.2 and 1.3 ##
# Starts from mariadb 10.4.6 not possible before. !!!! 
tls_version = TLSv1.2,TLSv1.3
```

```
# Set ownership 
chown -vR mysql:mysql /etc/mysql/ssl/

```

### Restart and check for errors 
```
systemctl restart mariadb
journalctl -u mariadb 

```

### Test connection on client 

```
# only if we use option --ssl we will connect with ssl 
mysql --ssl -uxyz -p -h <ip-of-server>
mysql>status
SSL:                    Cipher in use is TLS_AES_256_GCM_SHA384

```

### Force to use ssl 


```
# on server 
# now client can only connect, when using ssl 
mysql> grant USAGE on *.* to remote@10.10.9.144 require ssl;
```

