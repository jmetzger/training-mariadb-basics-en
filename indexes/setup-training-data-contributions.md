# Setup training data contributions (ubuntu 20.04) 

## Walkthrough 

  * Complete process takes about 10 minutes 

```bash 
cd /usr/src 
apt update; apt install -y git 
git clone https://github.com/jmetzger/dedupe-examples.git
cd dedupe-examples 
cd mysql_example 
# Eventually you need to enter (in mysql_example/mysql.cnf)  
# Only necessary if you cannot connect to db by entering "mysql" 
# password=<your_root_pw> 
./setup.sh 
```
