# Installation Ubuntu 22.04 

## Install version from distribution (older version)

```
apt update
apt install mariadb-server 

```

## Install Newest version from mariadb

```
https://downloads.mariadb.org/mariadb/repositories/
# repo 
sudo apt-get install software-properties-common
sudo apt-key adv --fetch-keys 'https://mariadb.org/mariadb_release_signing_key.asc'
sudo add-apt-repository 'deb [arch=amd64,arm64,ppc64el] https://mirror.dogado.de/mariadb/repo/10.5/ubuntu focal main'

apt update
apt install mariadb-server 

```

# Secure installation 

```
mariadb-secure-installation 
# OR: if not present before 10.4 
mysql_secure_installation 
```
