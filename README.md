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
     * Index-Types 
     * Use indexes for complex scenarios (correctly ;o)) 
     * Analyze optimal and suboptimal indexing 
     * Index strategies for high performance 
 
  1. Replication 
     * Performance optimization through replication 
     
  1. Performance - Recap 
     * [Best Practices](/performance/best-practices.md)
    
## Sammlung 

```
keine Funktionsbasierten Indizes möglich -> Achtung !
Probleme mit views anhand von Beispielen 
Prepared Statements ? 
We need to have something with a subquery and compare the performance and also do a rewrite to select

# I think it would be a brilliant idea, if we have real life example from e.g. sakila. 

Es erscheint mir erst einmal wichtig zu sein, was ich wie testen will ? 
Bevor wir uns für eine oder mehrere Datenbanken entscheiden. 
```
* https://use-the-index-luke.com/de/sql/where/bereiche/like-filter (wie wirkt sich like auf den Index aus)

* Indizes über mehrere Spalten (ja/nein ?) : 
  * https://use-the-index-luke.com/de/sql/where/bereiche/index-merge
  * ```
Es ist die wahrscheinlich häufigste Frage zur Indizierung überhaupt: Ist es besser, einen Index pro Spalte anzulegen oder einen Index über alle Spalten einer where-Klausel? In den meisten Fällen ist die Antwort sehr einfach: Ein Index über mehrere Spalten ist besser.„Zusammengesetzte Schlüssel“ erklärt mehrspaltige Indizes im Detail.
```
## Myths 

### Most selective field first in compound index

  * This is simply one 
  * You have to design the compound like so, that the most used combination of fields is used.
