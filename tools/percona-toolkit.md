# Install percona - toolkit (ubuntu 20.04 LTS) 

## Walkthrough 

```
# Howto 
# https://www.percona.com/doc/percona-toolkit/LATEST/installation.html

# Step 1: repo installieren mit deb -paket 
wget https://repo.percona.com/apt/percona-release_latest.focal_all.deb;
apt update; 
apt install -y curl; 
dpkg -i percona-release_latest.focal_all.deb;
apt update;
apt install -y percona-toolkit; 
```
