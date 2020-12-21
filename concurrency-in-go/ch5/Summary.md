# Concurrency at scale

# Error handling
- check out Dave Cheney's blog

# Timeouts and cancellation
- when to support timeout:
 - system saturation:
  - don't have the resources to store the request
  - if the data will go stale
- stale data
 - data has a window before newer data is available
 - using context with timeout
- prevent deadlocks

- when to support cancellation
 - user intervention
 - parent cancellation
 - replicated requests
  - sending multiple requests to get a faster response

- supporting rollback in case of cancellation
 - try to keep rollback code small

- duplicated messages
 - parent sees child unresponsive and sends the same request to a new child
 - make it unlikely by using heartbeats
 - accept first or last message in the downstream code
 