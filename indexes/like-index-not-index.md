# Working with like (index)  

## 1. like 'Will%' - Index works 

explain select last_name from donors where last_name like 'Will%';

## 2. like '%iams' - Index does not work 

```
-- because like starts with a wildcard 
explain select last_name from donors where last_name like '%iams';
```

## 3. How to fix 3, if you are using this often ? 

```
# Walkthrough 
# Step 1: modify table 
alter table donors add last_name_reversed varchar(70) GENERATED ALWAYS AS (reverse(last_name));
create index idx_last_name_reversed on donors (last_name_reversed);

# besser - Variante 2 - untested 
alter table donors add last_name_reversed varchar(70) GENERATED ALWAYS AS (reverse(last_name)), add index idx_last_name_reversed on donors (last_name_reversed);

# Step 2: update table - this take a while 
update donors set last_name_reversed = reversed(last_name)
# Step 3: work with it 
select last_name,last_name_reversed from donor where last_name_reversed like reverse('%iams');  
```

```
# Version 2 with pt-online-schema-change 

```
