# Database

## Table of Contents
1. [SQL](#sql)
    1. [Entity Relationship](#entity-relationship-model)
    1. [Keys](#keys)
    1. [Temporary Tables](#temporary-tables)
    1. [Comments](#comments)
    1. [Filtering](#filtering)
    1. [Operators](#operators)
    1. [Matchers](#matchers)
1. [Postgres](#postgres)
    1. [Operators](#operators)
    1. [PostGIS](#postgis)


## SQL
### Entity Relationship Model
![ER Diagram](images/er-diagram.png)

Composed of entity types and specifies relationships that can exist between instances of those entity types.
* Show relationships
* Business process
* Visual representation
* Show links (primary keys)

### Keys
* Primary Key    
A column (or set of columns) whose values uniquely identify every row in the table.

* Foreign Key  
One or more columns that can be used together to identify a single row in another table.

### Indexes
* Concurrent Indexing 
Creating an index can interfere with regular operation of a database. 
`CONCURRENTLY` option of `CREATE INDEX`.
* GIN
Best for static data, 3 times faster than GiST, takes 3 times longer to build than GiST

### Temporary Tables
```sql
CREATE TEMPORARY TABLE Actives AS
(
  SELECT *
  FROM properties
  WHERE status = 'active'
)
```

### Comments
* Single Line
```sql
SELECT property_id
--,type_of_dwelling
,full_address
FROM listings 
```
* Section
```sql
SELECT property_id
/*,type_of_dwelling
,full_address
*/
FROM listings
```

### Filtering
* Specifies the data you want to retrieve
* Reduces the number of records you retrieve
* Increases query performance
* Reduces strain on client application
* Governance limitations

```sql
SELECT column_name
FROM table_name
WHERE column_name operator value;
```

| Operator | Description                |
|----------|----------------------------|
| =        | Equal                      |
| <>       | Not equal                  |
| >        | Greater than               |
| <        | Less than                  |
| >=       | Greater than or equal      |
| <=       | Less than or equal         |
| BETWEEN  | Between an inclusive range |
| IS NULL  | Is a null value            |

### Operators
* Explain
  ```sql
  EXPLAIN(ANALYZE, COSTS, VERBOSE, BUFFERS)
  ```
* In  
  Specifies a range of conditions with comma delimited list of values. Faster than `OR`. Order does not matter. Can contain another `SELECT`.  
  ```sql
  WHERE property_id IN (1, 2, 3);
  ```
* Or  
  Second condition won't be evaluated if first condition is met.  
  ```sql
  WHERE property_id = 1 OR 2;
  ```  
* Between
  ```sql
  BETWEEN
  ```
* Coalesce
  ```sql
  COALESCE
  ```
* Union: combines the result sets of two queries.
  ```sql
  UNION
  ```
* Not
  ```sql
  WHERE NOT city = 'Vancouver'
  ```  
* Not equal to
  ```sql
  WHERE listings.type_of_dwelling <> 'Single Family Dwelling'
  ```    

### Matchers
`ILIKE` allows matching of strings based on comparison with a pattern (case-insensitive)


## Postgres
### Operators
* Contains
  ```sql
  @>
  ```
* jsonb
  ```postgres
  -->
  -> 
  ```

### PostGIS
Create the extension  
```sql
CREATE EXTENSION postgis;
```