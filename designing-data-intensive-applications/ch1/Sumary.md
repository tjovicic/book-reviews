# Chapter 1

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
