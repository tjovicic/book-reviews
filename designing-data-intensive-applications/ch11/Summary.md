# Streaming

# Main concerns
- what if producers send messages faster than consumers can process them?
 - queue, apply backpressure
- what if node crashes?
 - replicate or better performance

# Message Brokers
- responsible for durability
- consumers are async

## Difference with DBs
- brokers usually delete messages when delivered
- brokers do not support random queries

# Multiple consumers
- load balancing vs fanout

# Acks
- client must explicitly tell the broker when it has finished processing
- consumer crashes combined with LB can lead to message reordering

# Log-based message brokers
- appending msgs to a log
- log is partitioned for higher throughput
  - topic is then defined as a group of partitions that all carry messages of the same type
- great for high message throughput cases with ordering priority

# Databases and Streams
- using dual writes to keep different systems in sync is problematic:
 - overwriting because of concurrency
 - inconsistency due to failure

## Change Data Capture (CDC)
- process of observing all data changes written to a database

# Processing streams
- using as analytics
- searching data
- time concerns
 - event time and processing time differ, especially when delays happen

# Fault tolerance 
- microbatching, atomic commit, idempotence(using unique id)