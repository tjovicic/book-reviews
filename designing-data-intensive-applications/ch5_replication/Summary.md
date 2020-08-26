# Replication

- reduce access latency (closer to the user)
- increase availability (failover replicas)
- increase read throughput (read replicas)

## Leader-based replication
- writes are only accepted on the leader
- reads are acceptable everywhere
- using replication log changes are send to the followers

## Sync vs async replication
- should the leader wait for the followers response?
- with sync replication you are sure you have a full copy on another node but it the case of a node error the whole system could stop

## Follower failure
- each follower keep a track where it is in the replication process
- after failure it just needs to ask for the data from the point it stopped replicating

## Leader failure
- determining that is has failed, choosing a new leader, reconfiguring clients
- problems:
  - outside systems (like caches) might get corrupted if the new leader is not up to date
  - when to declare the leader dead?

## Replication logs implementation

### Statement based
- easy to implement
- problems with nondeterministic functions(rand, now), concurrency

### WAL
- append only sequence of bytes containing all reads
- very low level: which bytes where changed on what disk block
- closely coupled to the storage engine

### Logical log
- sequence of records describing writes at the row level

### Trigger based
- uses application logic

## Problems
- eventual consistency and replication lag
- read-after-write consistency
  - determining whether to read from a leader or follower
  - using clocks and timestamps to check if follower is up to date
- monotonic reads
  - user "goes back in time", sees different state on different replicas
  - makes sure same users get routed to the same replica
- consistent prefix reads
  - reading writes in the same order they are written

## Multi-leader replication
- makes sense in multi datacenter scenarion

### Handling write conflicts
- best way is to handle conflicts in the app logic

## Leaderless replication
- with no replication we use document version numbers to know which record is newer
- we don't care if some replicas missed a write as long as w+r>n
- if some replicas are missing a record, uses background processes to repair them
- difficult to monitor data staleness