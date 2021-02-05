# Decoupling

## Methods
- value based or pointer based methods
- follow value semantics when:
  - dealing with reference types
  - dealing with built-in types(int, string...)

- follow pointer semantics when:
  - unmarshalling, decoding
  - using struct types

## Interfaces
- reference types
- 2 word structures that describe type and have a pointer to concrete data
- cannot send in a value of a struct inf using pointer semantics
- embedding one struct in another makes outer struct implement inner struct interface

