# HTTP 1.x

# Keepalive connections
- total latency savings is (N-1) * RTT when connection keepalive is enabled

# HTTP pipelining
- sending multiple requests in parallel from the client and processing them in parallel on the server
- problem with head-of-line blocking that results in suboptimal delivery: if the first request hangs indefinitely all requests behind it are blocked and have to wait
- servers must buffer pipelined responses which may exhaust server resources
- used only in cases where you control both servers and clients

