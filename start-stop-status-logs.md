# Start / Stop / Status / Logs 

```
# How to find out if it is running 
systemctl status mariadb 

# To stop it 
systemctl stop mariadb 

# To start it 
systemctl start mariadb 

# to restart it 
systemctl restart mariadb 

# How it the configuration of the service 
systemctl cat mariadb 

# Logs 
# last 10 lines 
systemctl status mariadb
journalctl -u mariadb 



```
