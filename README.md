# MySQL Performance Training - Individuell 

## Agenda 

  1. Performance-relevante Aspekte der MySQL-Architektur 
  
     * Architecture Server (Steps)
     * [Query - Cache](/performance/query-cache.md)  
  
  1. Allgemeine Performance-Messung und Diagnose 
   
  1. Performance und Optimierung von SQL-Statements 
  
  1. Joins- Die verschiedenen Typen von Joins und der optimale Einsatz in Bezug auf Performance 
  
  1. Locking 
  
  1. InnoDB - Storage Engine 
  
     * [Wie ist die Storage - Engine aufgebaut](/innodb/innodb-structure.md) 
     * Welche entscheideneden Parameter sind wichtig und zielführend für die Performance 
    
  1. Optimaler Einsatz von Indizes   
  
  1. Replikation 
  
     * Performance-Optimierung durch Replikation 
    
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
```
