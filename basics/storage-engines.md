# Storage Engines 

## Why ?

```
Let's you choose:
How your data is stored
```

## What ?

  * Performance, features and other characteristics you want


## What do they do ?

  * In charge for: Responsible for storing and retrieving all data stored in MySQL
  * Each storage engine has its:
    * Drawbacks and benefits
  * Server communicates with them through the storage engine API 
    * this interface hides differences
    * makes them largely transparent at query layer
    * api contains a couple of dozen low-level functions e.g. “begin a transaction”, “fetch the row that has this primary key”

## Storage Engine do not ....

  * Storage Engines do not parse SQL
  * Storage Engines do not communicate with each other

## They simply .....

  * They simply respond to requests from the server

## Which are the most important one ?

  * MyISAM/Aria
  * InnoDB
  * Memory
  * CSV
  * Blackhole (/dev/null)
  * Archive
  * Federated/FederatedX
