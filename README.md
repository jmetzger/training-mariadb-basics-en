# MySQL performance training (individual) + 13.01. - 15.01.2021 

## Agenda 

  1. Performance related aspects of the MySQL architecture  
  
     * [Architecture Server (Steps)](/performance/mysql-server-architecture.md)
     * [Query - Cache](/performance/query-cache.md)
     * [Views and performance](/performance/views.md) 
  
  1. Diagnosis and measurement of performance 
     * Best practices to narrow down performance problems
     * Identify slow and not-optimal queries
     
  1. Performance and optimization of SQL statements 
     * Optimal use of MySQL datatypes 
     * [Do not use '*' whenever possible](/performance/select-no-star-please.md) 
     * Query Plans 
     * [Be aware of subselects - Example 1](/performance/subselects-1.md)
     * SELECT- and JOIN-TYPES 
     * Redesign of performance-critical statements 
     * Optimizer-hints (and why you should not use them) 
    
  1. Joins and performance
     * The different types of joins and their optimal use concerning performance 
     
  1. Locking 
     * Practical examples: How to work with locks 
     * Identifying long running locks and how to avoid them 
  
  1. InnoDB - Storage Engine 
     * [InnoDB - Storage Engine - Structure](/innodb/innodb-structure.md) 
     * Important InnoDB - configuration - options to optimized performance
    
  1. Optimal use of indexes
     * [Setup training data "contributions"](/indexes/setup-training-data-contributions.md)
     * Index-Types 
       * [Describe and indexes](/indexes/describe-table.md)
       * [Find out indexes](indexes/findout-indexes.md) 
     * Use indexes for complex scenarios (correctly ;o)) 
     * Analyze optimal and suboptimal indexing 
     * Index strategies for high performance 
     * [Index and Functions (Cool new feature in MySQL 5.7)](index-and-functions.md) 
  1. Replication 
     * Performance optimization through replication 
     * Replikation mit GTID :: https://www.admin-magazin.de/Das-Heft/2017/02/MySQL-Replikation-mit-GTIDs
     * Replikation Read/Write - Split: https://proxysql.com/blog/configure-read-write-split/
     
  1. Performance - Recap 
     * [Best Practices](/performance/best-practices.md)
     * [Example sys-schema](https://github.com/mysql/mysql-sys/blob/master/README.md)
     
  1. Documentation / Literature 
     * [Effective MySQL](https://www.amazon.com/Effective-MySQL-Optimizing-Statements-Oracle/dp/0071782796)
     
    
