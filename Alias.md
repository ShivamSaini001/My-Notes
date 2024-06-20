## Alias 

An alias is a temporary name assigned to a table or a column in a query. Aliases can be useful for several reasons, including improving the readability of queries, shortening long table or column names, and specifying unique names for the result set of a query. \
MySQL aliases can exist only for the duration of a query.\
It is useful when you use the function in the query.\
It can also allow us to combines two or more columns. \
Column aliases are used to temporarily rename a column or to give a name to the result of an expression or function in the output of a query. 

*Column Alias Syntax:*
```sql
    SELECT column_name AS alias_name
    FROM table_name;
```

Example:
```sql
    SELECT order_id AS ID, order_date AS Date
    FROM orders;
```

*Table Alias Syntax:*
```sql
    SELECT column_name(s)
    FROM table_name AS alias_name;
```

Example:
```sql
    SELECT o.order_id, c.customer_name
    FROM orders AS o
    JOIN customers AS c ON o.customer_id = c.customer_id;
```

| Parameter | Description |
|-----------|-------------|
| alias_name | It is the temporary name that we are going to assign for the column or table. If alias_name contains space, we need to specify alias_name within qoute either single or double. |
| AS | It is optional. If you have not specified it, there is no effect on the query execution. It is a programmer choice that they use it during the aliasing of the column name, but not aliasing in the table name. |

> [!NOTE]
> ### Alias without **AS** keyword
> Column Alias Syntax:
>  ```sql
>      SELECT column_name alias_name
>      FROM table_name;
>  ```
>  
>  Table Alias Syntax:
>  ```sql
>      SELECT column_name(s)
>      FROM table_name alias_name;  
>  ```

### Using Aliases with Aggregate Functions:

Aliases are commonly used with aggregate functions such as COUNT, SUM, AVG, etc., to give a name to the result of the aggregation.

Example:
```sql
    SELECT COUNT(*) AS total_orders
    FROM orders;
```