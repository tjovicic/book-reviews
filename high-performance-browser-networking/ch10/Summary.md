# Primer on Web Performance

# Bandwidth vs Latency
- improving bandwidth helps with page loads speed until a certain point (5Mbps)
  - after that every increase in bandwidth has negligible improvements in page loads speed
- most of the HTTP data flows consist of small, bursty data transfers, whereas TCP is optimized for long-lived connections and bulk data transfers
- network roundtrip is the limiting factor in TCP throughput and consequently, latency is the performance bottleneck for HTTP 

