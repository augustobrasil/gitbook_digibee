---
description: >-
  Learn more about Pagination and see examples of how to implement paginated
  queries in the pipeline.
---

# Paginations Example

## **Input Json Example**

```
{
    "page" : 1,
    "pageSize" : 50
}
```

## **Oracle** <a href="#h_2750facf09" id="h_2750facf09"></a>

```sql
SELECT COL_A, COL_B
  FROM (SELECT COL_A,
               COL_B,
               row_number() over (order by COL_A) rn
          FROM XPTO.MY_TABLE )
WHERE rn BETWEEN {{ TOLONG(SUM(SUBTRACT(MULTIPLY(message.page, message.pageSize), message.pageSize), 1)) }}
AND {{ TOLONG(MULTIPLY(message.page, message.pageSize)) }}
```

## **SQL Server** <a href="#h_913678e9a1" id="h_913678e9a1"></a>

```sql
SELECT col_a, col_b FROM myTabel 
ORDER BY col_a  
OFFSET {{ TOLONG(SUM(SUBTRACT(MULTIPLY(message.page, message.pageSize), message.pageSize), 1)) }} ROWS 
FETCH NEXT {{ message.pageSize}} ROWS ONLY 
```

## Data Bricks (managed Apache Spark) <a href="#h_518bdfce52" id="h_518bdfce52"></a>

```sparql
WITH CTEResults AS 
( 
SELECT *, ROW_NUMBER() OVER (ORDER BY query.col_1) AS RowNum FROM( 
select distinct 
col_1, 
col_2, 
col_3 
from mytable 
where << YOUR FILTERS HERE>> 
order by col_1) query 
) 
SELECT * 
FROM CTEResults 
where RowNum > {{ TOLONG(SUBTRACT(MULTIPLY(message.page, message.pageSize), message.pageSize)) }} 
 and RowNum <= {{ TOLONG(MULTIPLY(message.page, message.pageSize)) }}
```
