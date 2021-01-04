# InnoDB 

## InnoDB Structure 

![InnoDB Structure](/images/InnoDB-Structure.jpg)


## Innodb buffer pool

  * How much data fits into memory 
  * Free buffers = pages of 16 Kbytes 
  * Free buffer * 16Kbytes = free innodb buffer pool in KByte  
```
pager grep -i 'free buffers'
show engine innodb status \G
Free buffers       7905
1 row in set (0.00 sec)
```

## Overview innodb server variables / settings 

  * https://dev.mysql.com/doc/refman/5.7/en/innodb-parameters.html

## Change innodb_buffer_pool 

```
# /etc/mysql/mysql.conf.d/mysqld.cnf 
# 70-80% of memory on dedicated mysql
[mysqld]
innodb-buffer-pool-size=6G

#
systemctl restart mysql

# 
mysql
mysql>show variables like 'innodb%buffer%';
```

## Ref:

  * https://dev.mysql.com/doc/refman/5.7/en/innodb-buffer-pool-resize.html
  

## Privilegs for show engine innodb status 

```
 show engine innodb status \G
ERROR 1227 (42000): Access denied; you need (at least one of) the PROCESS privilege(s) for this operation

```
