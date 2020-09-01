# Transactions

## ACID

### Atomicity
- Ability to abort a transaction on an error and have all writes in the transactions discarded

### Consistency
- property of the application, not the database
- some invariants (credits == debits) about your data must be true

### Isolation
- concurrently executing transactions are isolated from each other
- rarely used, carries performance penalties. some weaker forms are used

### Durability
- once a transaction is committed there is no fear in loosing that data
- using WAL, additional nodes, backups

## Handling errors
- ACID DBs don't allow half-finished transactions
- others (non ACID) reply on application logic
  - retries are simple and effective solution

## Weak isolation levels
- serializable isolation is too expensive

### Read committed
- no dirty reads
  - you can only see the data that was committed 
  - implementations don't use locks but keep old and new values of current transactions
  - doesn't slow down reads in case of a big write transaction
- no dirty writes
  - overwrite data that was committed
  - implemented by row-level locks
- problems:
  - read skew: reading data before transaction and new data after transaction. issue for backups, analytical queries
  - solution is snapshot isolation: every transaction that reads, reads data "frozen" at some point in time

### Snapshot isolation
- using locks to prevent dirty writes
- maintaining several different versions of an object to prevent dirty reads
  - garbage collection cleans old values after some time
- transaction IDs are used to present consistent snapshot 
- ways of preventing lost updates

### Serializable isolation
- serial execution
  - using one thread and avoiding concurrency
  - made possible by improvements in RAM and SSD
  - there is a hard limit in using cross platform transactions
- two phase locking
  - writers block other writers and readers
  - shared and exclusive lock
  - poor performance
