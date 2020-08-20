# 2. Data Models and Query Language

## Impedance mismatch
- need for a translating layer between objects in code and SQL tables

- json representation of data has better locality

## Nice thought about foreign keys
- 'foreign keys have no meaning to humans just the data they represent', so it is easier to manipulate/change them

## Document vs Relational
- schema flexibility, better performance due to locality, closer to the structure used in apps
- better support for joins, N:1, N:N relationships

## Schema
- schema-on-read: structure of data is implicit, only interpreted when the data is read
- schema-on-write: traditional approach of relational DB

- keep documents fairly small to optimize speed of updates

## Merging of document and relational DBs
- json support in PostgreSQL and SQL-like queries in Mongo drivers

## Declarative vs imperative language
- declarative tells what
  - specify only the pattern of the result
- imperative tells how
  - hard to parallelize because of ordering
