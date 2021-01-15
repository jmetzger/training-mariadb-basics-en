# Break-Down performance problems 

## Pre-Requisites

  * System is slow 

## Analyze - Checklist  - Step 1

```
# Are there slow queries ? 
# look for time 
show full processlist 

## or time - in seconds  
select * from information_schema.processlist where time > 10;
```

## Re-Execute SELECT or where from UPDATE / DELETE 
```
# Is it still slow ? 
# Eventually kill 
mysql>show processlist 
mysql>--kill <Thread-id> 
mysql>-- example
mysql>kill 44 
```


## Explain what is going on

```
Explain Select.... 
```
