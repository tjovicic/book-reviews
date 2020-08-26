# Partitions

## Partitioning of key-value data

### By range
- automatically or manually choose ranges of keys
- easy to query for ranges
- risk of hotspots

### By hash key
- depends on the quality of the hash func
- cannot easily run range queries
- hotspots have to be handled in app logic(celebrity activity problem)

## Secondary indexes

### By document
- cares only about documents in its own partition
- reads have to cover all partitions

### By term
- global index, also needs to be partitioned
- making reads more efficient
- writes are slower, have to update multiple partitions

## Rebalancing 

### Fixed number of partitions
- have large number of partitions, many more than nodes
- when provisioning a new node, simply steal some partitions from existing nodes
- have to choose partition number at the start, difficult to predict the load

### Dynamic partitioning
- in use by key-range partitioned dbs
- newly created partitions can be transferred to another node

## Automatic vs manual rebalancing 
- automatic, although requires less admin interaction, can cause unexpected network and node load

## Choosing the right partition
- using coordination service like Zookeeper, mongos
