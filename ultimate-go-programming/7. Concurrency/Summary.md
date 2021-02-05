# Concurrency
- equal number of OS threads and processors
  - mapping multiple Go routines to one thread

# Data races
- test data race with `-race` flag
- interface data race
 - you can end up having interface type and pointer differ

# Channels
- pooling pattern
 - fixed number of consumers
- fan-out pattern
 - dangerous if you don't control number of threads
- fan-out semaphore
 - have additional chan that rate limits pushing to the result channel
- drop pattern
 - using select command and default case

 # Context
 - you HAVE to call `cancel` method
  - even if using withTimeout
  - usually placed with defer at the beginning
