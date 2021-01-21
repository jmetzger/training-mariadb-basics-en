# MySQL performance training (individual) + 18.01. - 21.01.2021 

## Agenda 

  1. Architectur of MariaDB 
     * [Architecture Server (Steps)](/performance/mysql-server-architecture.md)
     * [Query Cache Usage and Performance](/performance/query-cache.md)
     * [Optimizer-Basics](optimizer-basics.md) 
     * [Storage Engines](/basics/storage-engines.md) 

  1. Installation 
     * [Installation (Ubuntu)](installation-ubuntu.md)
     
  1. Security 
     * [Secure with SSL server/client](security/ssl.md) 

  1. InnoDB - Storage Engine 
     * [InnoDB - Storage Engine - Structure](/innodb/innodb-structure.md) 
     * [Important InnoDB - configuration - options to optimized performance](/innodb/innodb.md) 
  
  1. Training Data 
     * [Setup training data "contributions"](/indexes/setup-training-data-contributions.md)
     
  1. Performance 
     * [io-Last/CPU-Last](performance/last.md) 
     * [Views and performance](/performance/views.md)      

  1. Backup and Restore (Point-In-Time aka PIT) 
     * [Backup with mysqldump - best practices](backup-restore/mysqldump.md) 
     * [Flashback](backup-restore/flashback.md) 
     * [mariabackup](backup-restore/mariabackup.md) 
     * [Use xtrabackup for MariaDB 5.5](backup-restore/xtrabackup-for-mariadb-5-5.md)

  1. Optimal use of indexes
   
     * Index-Types 
       * [Describe and indexes](/indexes/describe-table.md)
       * [Find out indexes](indexes/findout-indexes.md) 
     * [Index and Functions (Cool new feature in MySQL 5.7)](index-and-functions.md) 
     * [Index and Likes](/indexes/like-index-not-index.md)   
     * [profiling-get-time-for-execution-of.query](/indexes/profiling.md) 
     * [Find out cardinality without index](/indexes/cardinality.md)

  1. Tools 
     * [Percona-toolkit-Installation](/tools/percona-toolkit.md) 
     * [pt-query-digist - analyze slow logs](/tools/pt-query-digest.md) 
     * [pt-online-schema-change howto](/tools/pt-online-schema-change.md)
  
  1. Documentation 
     * [MySQL - Performance - PDF](http://schulung.t3isp.de/documents/pdfs/mysql/mysql-performance.pdf)

## Add-Ons (Further read) 

  1. Diagnosis and measurement of performance 
     * [Best practices to narrow down performance problems](performance/best-practice-analyze.md
     
  1. Performance and optimization of SQL statements
     * [Do not use '*' whenever possible](/performance/select-no-star-please.md)
     * [Be aware of subselects - Example 1](/performance/subselects-1.md)
     * [Optimizer-hints (and why you should not use them)](performance/optimizer-hints.md)
     
  1. Replication 
     * [Replikation Read/Write](https://proxysql.com/blog/configure-read-write-split/)
     
  1. Performance 
     * [Best Practices](/performance/best-practices.md)
     * [Example sys-schema and Reference](/tools/sys.md)
     * [Change schema online (pt-online-schema-change)](https://www.percona.com/doc/percona-toolkit/3.0/pt-online-schema-change.html)
     * [Optimizer-Hints](performance/optimizer-hints.md) 
    
  1. Documentation / Literature 
     * [Effective MySQL](https://www.amazon.com/Effective-MySQL-Optimizing-Statements-Oracle/dp/0071782796)
     * [Last Training](https://github.com/jmetzger/training-mysql-developers-basics)
     * [MySQL - Performance - PDF](http://schulung.t3isp.de/documents/pdfs/mysql/mysql-performance.pdf)
     * [MariaDB Galera Cluster](http://schulung.t3isp.de/documents/pdfs/mariadb/mariadb-galera-cluster.pdf)
     * [MySQL Galera Cluster](https://galeracluster.com/downloads/)
     
   1. [Partitions and Explain](partitions/partitions-explain.md)    
   
   1. [Questions and Answers](q-and-a.md)
      * [migration-mysql-update-5.6->5.7](migration-mysql.md)
    
   1. [mysql-do-nots](/performance/mysql-do-nots.md)
   
