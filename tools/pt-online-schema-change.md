# pt-online-schema-change 

## Requirements 

  * Install percona-toolkit 

## What does it do ?

```
# Altering table without blocking them 
# Do a dry-run beforehand 
pt-online-schema-change --alter "ADD INDEX idx_city (city)" --dry-run D=contributions,t=donors
# 
pt-online-schema-change --alter "ADD INDEX idx_city (city)" --execute D=contributions,t=donors

```

## Problems -> high cpu load 

```
# fine - tune params 
# e.g. --max-load 
# refer to docs 
https://www.percona.com/doc/percona-toolkit/3.0/pt-online-schema-change.html#:~:text=pt%2Donline%2Dschema%2Dchange%20works%20by%20creating%20an%20empty,it%20with%20the%20new%20one.

```
