# Chapter 3

## Log-structured vs page-oriented storage engines

### Log-structured storage engines
- append to file is very efficient
- reading is not: O(n) complexity
- introducing indexes slows down writes, have to update them for every write

#### Hash index
- keeping value offset for every file and keeping it in RAM
- compacting log segments: deleting duplicate keys and merging bunch of smaller files together
- can be done in another thread while read and writes are happening
- deleting a record means putting a "tombstone" and ignoring older records in the log
- fast, great for concurrency and crash recovery
- bad for range queries and have to keep everything in RAM

### SSTables and LSM-trees

#### SSTables
- segments(smaller log files) sorted by keys
- easy to search, merge and compress
- red-black, AVL trees used as memtable before writing to a file
- using Bloom filters for checking if keys exist

#### BTrees
- saving references to pages in a tree structure
- use write-ahead logs for crash recovery and locks for thread safety

- challenges using fuzzy or multi-column indexes

## In-memory
- either for caching only or saves log/snapshot on disk for durability
- they are faster because they avoid the overhead of encoding in-mem data structures to a form for saving to disk

## OLAP vs OLTP
- ETL jobs getting data from OLAP to OLTP DBs
- although relational DBs are good for both workloads, there are more and more specialized ones for data warehousing

### Schemas for Analytics
- star schema: big "fact" tables with events that points to "dimension" tables with specific data

## Column oriented storage

- storing columns in segments instead of rows
- optimizing storage using bitmasks
- using precomputed results, e.g. OLAP cube
