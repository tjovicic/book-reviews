# Building blocks

# Goroutines
- hosting goroutines is implemented by M:N scheduler, that maps M goroutines to N OS threads
- fork-join model
  - "go" statement == fork
  - join can be done with Wait groups
- extremely lightweight

# Sync package
- low level memory access

## Mutex
- unlock with defer, to execute even when panicking

## Cond
- block goroutines using Wait() call and unblock using Signal()
- while Signal() signals just the first goroutine in the queue, Broadcast signals to all goroutines
- channels can't broadcast easily

# Channel 
## Closing a channel
- closed channel can signal to multiple goroutines (can be read indefinitely)

## Ownership
- best practice is to have goroutine that handles creating, writing, and closing a channel and others that just read 