# 1. Reliable, Scalable and Maintainable Applications

## Reliability
System should work correctly even in the face of adversity

## Scalability
As the system grows(data volume, traffic) there should be a reasonable way of dealing with that traffic

## Maintainability
Over time many different people should work on the system productively

### Reliability
- EC2 instances have no SLA (reported around 2-3 nines)
- know how to tolerate loss of entire machines
- human error is the most prevalent

### Scalability
- first describe the current load (Twitter example)
- Latency vs response time
  - response time is what client sees(network delays + processing time + ...)
  - latency is the duration that a request is waiting to he handled
- think about response time as a distribution
  - median vs average
- head-of-line blocking
  - important to measure response time on the client side, due to the queueing delays 

### Maintainability
- operability, simplicity, evolvability

# 2. Data Models and Query Language

## Impedance mismatch
- need for a translating layer between objects in code and SQL tables

- json representation of data has better locality

## Nice thought about foreign keys
- 'foreign keys have no meaning to humans just the data they represent', so it is easier to manipulate/change them

## Document vs Relational
- schema flexibility, better performance due to locality, closer to the structure used in apps
- better support for joins, N:1, N:N relationships

## Schema
- schema-on-read: structure of data is implicit, only interpreted when the data is read
- schema-on-write: traditional approach of relational DB

- keep documents fairly small to optimize speed of updates

## Merging of document and relational DBs
- json support in PostgreSQL and SQL-like queries in Mongo drivers

## Declarative vs imperative language
- declarative tells what
  - specify only the pattern of the result
- imperative tells how
  - hard to parallelize because of ordering

# 3. Storage and Retrieval

## Column oriented storage

- storing columns in segments instead of rows
- optimizing storage using bitmasks
- using precomputed results, e.g. OLAP cube