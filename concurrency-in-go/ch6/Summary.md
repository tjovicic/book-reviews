# Goroutines and runtime

# Work stealing
- separating x tasks to n processors
 - naively splitting n/x has downsides
  - poor cache locality
  - underutilization because some tasks depend on others
- using one FIFO queue
 - single point of failure that all processors have to access
 - also poor cache locality
