# Variables

## Structs
- you cannot assign one struct type to another without conversion(although they maybe have the same fields)
- one exception are anonymous structs
- conversion vs type assertion
  - use type assertion when dealing with interfaces
  - use conversion when converting from one concrete type to another

## Pointers
- everything is pass by value
- goroutine can only operate inside a limited stack frame
- escape analysis: placed on stack or heap
  - compiler determines that
- constants of a kind vs constants of a type
