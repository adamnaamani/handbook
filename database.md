# Database

## Table of Contents
1. [Postgres](#postgres)
2. [SQL](#sql)
    1. [Indexes](#indexes)
    2. [Between](#between)
    3. [Coalesce](#coalesce)

## Postgres


## SQL
### Indexes
* Concurrent Indexing 
Creating an index can interfere with regular operation of a database. 
`CONCURRENTLY` option of `CREATE INDEX`.
* GIN
Best for static data, 3 times faster than GiST, takes 3 times longer to build than GiST

### Explain
```sql
EXPLAIN(ANALYZE, COSTS, VERBOSE, BUFFERS)
```

### Between
```sql
BETWEEN
```

### Coalesce
```sql
COALESCE
```

### Union
Combines the result sets of two queries.
```sql
UNION
```

### Matchers
`ILIKE` allows matching of strings based on comparison with a pattern (case-insensitive)
