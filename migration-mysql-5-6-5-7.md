# Migration 


```
=========== 

1. Sicherung. 
xtrabackup 
Mysqldump 
16 GB 
————

1. 

Neue Location -> 5.6 
<-  Xtrbackup  
Server runterfahren
Update 5.7 
Fahrt den Server wieder hoch


2.  Source-Host (Old Host) -> mysqldump 
Neuen -> Installation von MySQL 5.7 
Test-einspielen. 
< mysqldump 

4-5 Stunden. 

—> Konfiguration von mysql -> was wollt ihr übernehmen. 

3. Replications - Slave auf neuem System -> 5.7 
Hängt in den Master.
Sicheren Transport 
—> ssh -tunnel .
-> Firewall-Regeln. 
—> ssl -absicherung 

```
