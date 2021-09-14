---
sort: 1
---

# Basic knowledge
Good to know first.

### 1. [The order of execution](https://www.eversql.com/sql-order-of-operations-sql-query-order-of-execution/)
1. FROM, including JOINs
2. WHERE
3. GROUP BY
4. HAVING
5. WINDOW functions
6. SELECT
7. DISTINCT
8. UNION
9. ORDER BY
10. LIMIT and OFFSET

Knowing this, we can avoid some problems, for example: when you use a WINDOW function to get a new column, you can't
filter it by WHERE clause because it has been executed. 

```note
Modern databases are already challanaging that default order by applying some optimization tricks which might change the actual order of execution, though they must end up returning the same result as if they were running the query at the default execution order.

Why would they do that? Well, it can be silly if the database would first fetch all data mentioned in the FROM clause (including the JOINs), before looking into the WHERE clause and its indexes. Those tables can hold lots of data, so you can imagine what will happen if the database's optimizer would stick to the traditional order of operations of an SQL query.
```
