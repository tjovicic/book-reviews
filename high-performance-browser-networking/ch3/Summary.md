# UDP

## Datagram
- self-contained, independent entity of data carrying sufficient info to be routed from the source to the destination nodes
- packets delivered on an unreliable service - no delivery guarantees, no failure notifications

## UDP Header
- source port, destination port, length, checksum, payload

## What iy does not provide
- no guarantee of message delivery
- no guarantee pf order of delivery
- no connection state tracking
- no congestion control

- because there is no retransmission, datagrams cannot be fragmented

## Connection state timeout
- because UDP is stateless, NAT devices use times to know when to drop packets
- so one of the best practices for long running sessions over UDP is to introduce bidirectional keep alive packets

## NAT Traversal
- STUN(Session Traversal Utilities) answers applications question about it's public IP
- if that fails clients can use TURN relay server instead
