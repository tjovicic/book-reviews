# Consistency and Consensus

## Consistency
- eventual consistency is a weak form of consistency, doesn't say when the sync will happen

## Linearizability
- make the system appear as if there is one copy of data
- locking and leader election systems must be linearizable

### CAP theorem
- kind of misleading, network partitions will happen whether you like it or not
- when network partitions happen you can choose between consistency or availability

- linearizability is slow, not only during a network fault
-  response time of read and write requests is proportional to the uncertainty of delays in the network

## Ordering
- Lamport timestamps ensure total ordering of operations using tuple of node and message id
  - cannot be used in ensuring uniqueness of username

### Total order broadcast
- protocol for exchanging messages between nodes
- can build linearizable compare-and-set operation from it

## Consensus
- atomic commit and leader election

### Two-phase commit
- uses a coordinator that first checks if the nodes are ready
- can be stuck waiting for coordinator to recover
- when a transaction is in doubt, it still keeps row locks
- sometimes consensus algorithms are really sensitive to network issues
