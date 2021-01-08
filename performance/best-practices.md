# Best Practices

## Indexes 

### 2 Indexes vs. Combined Index 

  * In most cases a combined index is better than 2 indexes. 
  
## Joins 

### Field-Type 

  * Do not use varchar() or char() aka string types of join field 
  * better: integer (unsigned) && same size 
    * e.g. actor_id id int unsigned 

## Views 

### General 

  * Only use views with merge 
  * NO temptable please, these CANNOT be indexed. 

## Where 

### No functions in where please 

  * Why ? Index cannot be used.
  * example:
    * select first_name from actor where upper(first_name) like 'A%'

#### Alternative solution 

  * use a virtual field and index virtual field (possible from mysql > 5.7) 
  * Massive improvements in mysqL 8 
