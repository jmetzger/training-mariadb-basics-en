# MySQL performance training (individual) + 13.01. - 15.01.2021 

## Agenda 

  1. Architectur of MariaDB 
     * [Architecture Server (Steps)](/performance/mysql-server-architecture.md)
     * [Query Cache Usage and Performance](/performance/query-cache.md)
     * [Optimizer-Basics](optimizer-basics.md) 
     * [Storage Engines](/basics/storage-engines.md) 

  1. Documentation 
     * [MySQL - Performance - PDF](http://schulung.t3isp.de/documents/pdfs/mysql/mysql-performance.pdf)






  1. Performance related aspects of the MySQL architecture  
     * [Views and performance](/performance/views.md) 
  
  1. Diagnosis and measurement of performance 
     * [Best practices to narrow down performance problems](performance/best-practice-analyze.md
)
     * Identify slow and not-optimal queries
     
  1. Performance and optimization of SQL statements 
     * Optimal use of MySQL datatypes 
     * [Do not use '*' whenever possible](/performance/select-no-star-please.md) 
     * Query Plans 
     * [Be aware of subselects - Example 1](/performance/subselects-1.md)
     * SELECT- and JOIN-TYPES 
     * Redesign of performance-critical statements 
     * [Optimizer-hints (and why you should not use them)](performance/optimizer-hints.md)
    
  1. Joins and performance
     * The different types of joins and their optimal use concerning performance 
     
  1. Locking 
     * Practical examples: How to work with locks 
     * Identifying long running locks and how to avoid them 
  
  1. InnoDB - Storage Engine 
     * [InnoDB - Storage Engine - Structure](/innodb/innodb-structure.md) 
     * [Important InnoDB - configuration - options to optimized performance](/innodb/innodb.md) 
    
  1. Optimal use of indexes
     * [Setup training data "contributions"](/indexes/setup-training-data-contributions.md)
     * Index-Types 
       * [Describe and indexes](/indexes/describe-table.md)
       * [Find out indexes](indexes/findout-indexes.md) 
     * Use indexes for complex scenarios (correctly ;o)) 
     * Analyze optimal and suboptimal indexing 
     * Index strategies for high performance 
     * [Index and Functions (Cool new feature in MySQL 5.7)](index-and-functions.md) 
     * [Index and Likes](/indexes/like-index-not-index.md)
     * [Percona-toolkit](/tools/percona-toolkit.md) 
     * [pt-query-digist - analyze slow logs](/tools/pt-query-digest.md) 
     * [pt-online-schema-change howto](/tools/pt-online-schema-change.md)
     * [profiling-get-time-for-execution-of.query](/indexes/profiling.md) 
     * [Find out cardinality without index](/indexes/cardinality.md)
     
  1. Replication 
     * Performance optimization through replication 
     * Replikation mit GTID :: https://www.admin-magazin.de/Das-Heft/2017/02/MySQL-Replikation-mit-GTIDs
     * Replikation Read/Write - Split: https://proxysql.com/blog/configure-read-write-split/
     
  1. Performance 
     * [Best Practices](/performance/best-practices.md)
     * [Example sys-schema and Reference](/tools/sys.md)
     * [Change schema online (pt-online-schema-change)](https://www.percona.com/doc/percona-toolkit/3.0/pt-online-schema-change.html)
     * [io-Last/CPU-Last](performance/last.md) 
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
   
