 > # DML Commands in MySQL:

 DML Stands for Data Manipulation Language. 
 The command of DML is not auto-committed that means it can't permanently save all the changes in the database. They can be rollback.


## (A) INSERT Command: 
The INSERT statement is used to add new rows of data into a table. It allows you to specify the columns you want to insert data into and provide the corresponding values for those columns.

It is used to insert a single or a multiple records in a table.

There are two ways to insert data in a table --
1. By SQL INSERT INTO statement  
    (A) By specifying column names \
    (B) Without specifying column names
2. By SQL INSERT INTO SELECT statement

### **1. By SQL INSERT INTO statement**

Syntax:-
```sql
    --  By specifying column names
    INSERT INTO table_name (column1, column2, column3, ...)
    VALUES (value1, value2, value3, ...);
        Or
    -- Without specifying column names
    INSERT INTO table_name
    VALUES (value1, value2, value3, ...);
```
Example:-
```sql
    INSERT INTO users (name, age, email)
    VALUES ('John Doe', 30, 'john@example.com');
```

*Insert multiple rows at a time into the table.*

Example:-
```sql
    INSERT INTO users (name, age, email) VALUES 
    ('John Doe', 30, 'john@example.com'),
    ('Jessica', 35, 'Jessica@example.com'),
    ('Mary', 20, 'Mary@example.com');
``` 

### **2. By SQL INSERT INTO SELECT statement**


In MySQL, the INSERT INTO SELECT statement is used to insert data into a table from the result of a SELECT query. \
This statement allows you to copy data from one table and insert it into another table.

Syntax:
```sql
    INSERT INTO [target_table] (column1, column2, ...)
    SELECT expression1, expression2, ...
    FROM [source_table]
    WHERE condition;
```

Example:
```sql
    INSERT INTO new_employees (name, salary)
    SELECT name, salary
    FROM employees
    WHERE join_date > '2023-01-01';
```

**Note:** when you add a new row, you should make sure that data type of the value and the column should be matched.

<hr>

> [!IMPORTANT]
>
> ### Ques. How to copy data of one table into another table using INSERT INTO command?
> **Ans.** To copy data from one table to another existing table in MySQL using the **INSERT INTO** command, you can execute a query that selects data from one table and inserts it into another.
> Syntax: -
> ```sql
>     INSERT INTO target_table_name (column1, column2, ...)
>     SELECT column1, column2, ...
>     FROM source_table_name
>     WHERE condition;
> ```
> 
> - The column names and data types in the target table must match those in the result set of the SELECT query. 
> - If the target table already contains data, the INSERT INTO command will append the new rows to the existing data.

<hr>

## (B) DELETE Command: 

The DELETE command is used to remove rows from a table based on specified condition. It's commonly used when you need to delete specific records or all records from a table rather than dropping the entire table itself. 

Syntax:-
```sql
    -- Delete specific Record
    DELETE FROM [table_name] WHERE condition;
        OR
    -- Delete all Records
    DELETE FROM [table_name];
        OR
    -- Invalid query
    DELETE * FROM [table_name];
```

Example:-
```sql
    DELETE FROM employees WHERE employment_status = 'left';
```

**Note:** If you don't specify any condition, it will be remove(erase) all data from table.

Syntax:-
```sql
    DELETE FROM [table_name];
```

Example:-
```sql
    DELETE FROM user;
```


## (C) UPDATE Command: 
The UPDATE command is used to modify existing records in a table. It allows you to change the values of one or more columns in one or more rows based on specified conditions. 

Syntax:-
```sql
    UPDATE [table_name]
    SET column1 = value1, column2 = value2, ...
    WHERE condition;
```

**Note:** If you don't specify any condition, it will be update(change) data of specified all columns from table.

Syntax:-
```sql
    UPDATE [table_name]
    SET column1 = value1, column2 = value2, ...;
```

