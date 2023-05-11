# Installation Debian 11 

## Install version from distribution (older version)

```
apt update
apt install mariadb-server 

```

## Install Newest version from mariadb

```
https://downloads.mariadb.org/mariadb/repositories/
```

```
# repo 
sudo apt-get install apt-transport-https curl
sudo curl -o /etc/apt/trusted.gpg.d/mariadb_release_signing_key.asc 'https://mariadb.org/mariadb_release_signing_key.asc'
sudo sh -c "echo 'deb https://ftp.agdsn.de/pub/mirrors/mariadb/repo/10.6/debian bullseye main' >>/etc/apt/sources.list"
```

```
apt update
apt install mariadb-server 
```

# Secure installation 

```
mariadb-secure-installation 
# OR: if not present before 10.4 
mysql_secure_installation 
```
