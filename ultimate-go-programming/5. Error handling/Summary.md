# Error handling
- use if statement for negative path, rest for happy path
- err != nil asks if there is a concrete value inside the error interface
- use errors.New() string type first, then create custom error types if you want more details
- always return error interface and inspect type with switch-case
