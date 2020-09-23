# Troubles with Distributed Systems

## Unreliable networks

- you don't know if the network packet got dropped before, after or at the recipient
- using something like Chaos Monkey to deliberately cause network outages
- timeout is the only sure way of detecting a fault
  - difficult to determine what value timeout should be

## Clocks
- synced and corrected by smth like NTP
- time-of-day vs monotonic clocks
  - ToD clocks can move backwards
  - monotonic always move forward but have no meaning

- in multi-master DB, clocks inaccuracies can cause data corruption
- threads and processes can pause for unbounded amount of time

- issues with GC pauses

- usage of quorum algorithms to declare nodes dead; a node cannot be relied on to know it's own health/status
- Byzantine fault-tolerant systems
  - functions in case of malicious nodes/actors
  - very expensive to get right
