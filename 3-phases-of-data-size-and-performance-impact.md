# Table development phases (regarding size of table) 

## Phase 1: Table content is small (only some rows) 

```
# table scan is quicker than index search 
# e.g. 10 entries 

# so eventually index is not needed 

```

## Phase 2: Index is good !! 

```
# performance gain by using index
# Step 1: Obtaining id's from index (primary key id) 
# Step 2: Retrieving data 
```

## Phase 3: Index is not improve performance / or would makes performance worse

```
Step 1: lookup in index:
1
70
1040
2100
35000
-> there is a lot of space (other rows) in between.

Step 2: Lookup data, but a lot lookups needed 


-> random reads
-> So mysql might be better off to do a table scan. 

```


