# Charset and Collations 

## Databases 

  * Only the default is set here 


```
use information_schema;
select * from schemata;
show tables like '%COL%';
select * from collation_character_set_applicability where character_set_name='utf8';
```

## Ref:

  * https://dev.mysql.com/doc/refman/5.7/en/charset-unicode-sets.html
