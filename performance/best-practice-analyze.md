# Break-Down performance problems 

## Pre-Requisites

  * System is slow 

## Analyze - Checklist 

```
# Are there slow queries ? 
# look for time 
show full processlist 

## or time - in seconds  
select * from information_schema.processlist where time > 10;
```



