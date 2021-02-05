# Data structures

## Arrays
- access to L1 cache vs main memory
- try to use predictable access pattern
- for range(i, value) loop operates on a copy of the array

## Slices
- 3 word structure(pointer, len, cap) + backing array
- capacity is for growth
- empty != nil slice
- "append" doubles until 1k elements, from there increases by 25%
- when creating slices from other slices or arrays(slice operator) be careful when appending/updating
- use slice[a:a+len:len] to make sure appending doesn't update the original array/slice
- for range(i, value) works also on copies

## Map
- iterating over keys is random
  - you can store keys in slice and have guaranteed ordering