# TCP

- abstraction of a reliable network running on a unreliable channel
- hides retransmission, congestion control, packet ordering

## Three-way handshake

### SYN
- client picks a random seq number x and sends a SYN packet, with additional TCP flags and options

### SYN ACK
- server increases x by one, picks its own random sequence and appends its own set of flags and options

### ACK
- client increases both x and y by one and completes the handshake

- implication on performance, each new connection will have a full roundtrip of latency before any data is transferred
  - connection reuse is a critical optimization

## Congestion avoidance
- asymmetric bandwidth capacity between the nodes is the cause

### Flow control
- mechanism to prevent sender overwhelming the receiver
- each side communicates available buffer space to hold the incoming data, called "receive window (rwnd)"
- adjustments continue throughout the lifetime of every TCP connection
- talks about sender and receiver, not the network state

### Slow start
- flow control prevents sender from overwhelming the receiver, but we don't check the network
  - network bandwidth is always changing
- congestion window size(cwnd)
  - amount of data sender can have in flight
- start slow and grow window sizes as packets are acknowledged
- we start with a small cwnd and double it every roundtrip
- throughput of a new TCP connection is minimum of cwnd and rwnd

### Congestion avoidance 
- once the packet is lost we adjust the window
- throughput trace of a TCP connection has a sawtooth pattern
- this is an area of active research

## Bandwith-Delay Product
- product of capacity and end-to-end delay
  - the result is max unack data that can be in flight

## Head-of-line blocking
- if a packet is lost, then all subsequent packets must be held in the receivers TCP buffer until the lost packet is retransmitted
- our app just sees delay
- UDP can be better for some use cases(video call, gaming...)