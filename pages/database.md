# Database

## Table of Contents
1. [SQL](#sql)
    1. [Entity Relationship](#entity-relationship-model)
    1. [Keys](#keys)
    1. [Indexes](#indexes)
    1. [Temporary Tables](#temporary-tables)
    1. [Comments](#comments)
    1. [Filtering](#filtering)
    1. [Operators](#operators)
    1. [Wildcards](#wildcards)
    1. [Sorting](#sorting)
    1. [Math Operations](#math-operations)
1. [Postgres](#postgres)
    1. [Operators](#operators)
    1. [PostGIS](#postgis)


## SQL
### Entity Relationship Model
![ER Diagram](/images/er-diagram.png)

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
  WHERE status = 'active';
)
```

### Comments
* Single Line
```sql
SELECT property_id
--,type_of_dwelling
,full_address
FROM listings ;
```
* Section
```sql
SELECT property_id
/*,type_of_dwelling
,full_address
*/
FROM listings;
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
  WHERE NOT city = 'Vancouver';
  ```  
* Not equal to
  ```sql
  WHERE listings.type_of_dwelling <> 'Single Family Dwelling';
  ```    

### Wildcards
* Takes longer to run if used at the end of search patterns. Placement of wildcards is important.

| Wildcard        | Action                                                    |
|-----------------|-----------------------------------------------------------|
| '%House'        | Retrieves anything ending with the word house             |
| 'House%'        | Retrieves anything after the word house                   |
| '%House%'       | Retrieves anything before and after the word house        |
| 'A%M'           | Retrieves anything that starts with "A" and ends with "M" |
| 'a%@gmail.com%' | Retrieves gmail addresses that start with "a"             |

* Underscore
  ```sql
  WHERE type_of_dwelling LIKE '_house';
  --Output: townhouse, rowhouse
  ```
* `ILIKE`  
Allows matching of strings based on comparison with a pattern (case-insensitive)

### Sorting
* Sequence of retrieved data cannot be assumed if order is not specified.
* Must always be the last clause in `SELECT` statement.
  ```sql
  SELECT *
  FROM properties
  ORDER BY pid;
  ```
* Direction  
  - Only applies to the column names it directly precedes.
  ```sql
  DESC --descending
  ASC --ascending
  ```

### Math Operations
| Operator | Description    |
|----------|----------------|
| +        | Addition       |
| -        | Subtraction    |
| *        | Multiplication |
| /        | Division       |

* Multiplication
  ```sql
  SELECT 
  address_id,
  floor_area_grand_total * sold_price_per_sqft AS soldPrice  
  FROM listings
  ORDER BY pid;
  ```
* Combining operations
  > PEDMAS
  ```sql
  SELECT 
  (total_value - land_value) / sold_price AS ppsf  
  FROM listings
  ORDER BY pid;
  ```  

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
Create the extension:  
```sql
CREATE EXTENSION postgis;
```