# Example join with sakila 

## Structure of join 

```
# In General 
# Do not execute, no real life example 
SELECT field_from_tablea,field_from_tableb 
FROM table_a a join table_b b 
ON a.id = b.actor_id;
```

```
# Step 1: get some data from table 1
select c.last_name,c.address_id from customer c;

# Step 2: Refer to the second table 
SELECT c.last_name,c.address_id,a.address_id FROM customer c LEFT JOIN address a ON c.address_id=a.address_id;

# Step 3: use the right fields -- Uups city is missing 
SELECT * from city;
SELECT c.first_name,c.last_name,a.address,a.postal_code,ct.city FROM customer c JOIN address a ON c.address_id=a.address_id JOIN city ct ON a.city_id =ct.city_id;

```


