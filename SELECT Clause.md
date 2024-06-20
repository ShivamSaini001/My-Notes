> # DQL (SELECT) Command:

<!--
## Important topics:
 
SELECT Command
SELECT DISTINCT
SELECT INTO
alias
operators
Clause
    - FROM 
    - WHERE
    - ORDER BY
    - GROUP BY
    - HAVING
    - LIMIT 
    - OFFSET

-->






## 1. SELECT Clause: 
The SELECT statement in MySQL is used to retrieve data from one or more tables in a database. It is one of the most fundamental and powerful commands in SQL.

The data returned is stored in the result table, also called as result set.

> [!IMPORTANT]
>  The **SELECT** statement is primarily used to retrieve data from a database, but it can also be used to print text and perform simple mathematical operations in MySQL. 
>
> **For Example: -** \
>  and SELECT “HELLO WORLD”.
>
> | Operations | Example | Result |
> |------------|---------|--------|
> | + | SELECT 14+15 | 29 |
> | - | SELECT 20-15 | 5 |
> | / | SELECT 20/6 | 3.3333 |
> | * | SELECT 15*3 | 45 |
> | ^ | SELECT 2^3 | 8 |
> | && | Select true && true | 1 |
> | ! | Select !true | 0 |
> |  | SELECT 'Hello World' | Hello World |
> |  | SELECT CONCAT('Hello', ' ', 'World'); | Hello World |
> |  |  | etc... |
> 
> 
> The MySQL SELECT statement is used with various clauses like **WHERE, GROUP BY, ORDER BY**, etc. We can also use aggregate functions like **SUM, COUNT**, etc 

### SELECT Statement Syntax: 
**++++ Select specified field +++++**

Syntax: -
```sql
    SELECT field_name1, field_name 2,... field_nameN   
    FROM table_name1, table_name2...  
    [WHERE condition]  
    [GROUP BY field_name(s)]  
    [HAVING condition]   
    [ORDER BY field_name(s)]  
    [OFFSET M ][LIMIT N];  

   /* Note: WHERE, GROUP BY, HAVING, ORDER BY, OFFSET are Optional.*/
```

**++++ Select all fields ++++**

Syntax: -
```sql
    SELECT * FROM table_name1, table_name2...  
    [WHERE condition]  
    [GROUP BY field_name(s)]  
    [HAVING condition]   
    [ORDER BY field_name(s)]  
    [OFFSET M ][LIMIT N]; 
    
   /* Note: WHERE, GROUP BY, HAVING, ORDER BY, OFFSET are Optional.*/
```


> **Note:** WHERE, GROUP BY, HAVING, ORDER BY, OFFSET are Optional.

- ### Select specific Columns:
    Syntax: -
    ```sql
        SELECT column1, column2, ... FROM [table_name];
    ```

- ### Selecting All Columns:
    Syntax: -
    ```sql
        SELECT * FROM table_name;
    ```

- ### Select Columns through Specifying Conditions:
    Syntax: -
    ```sql
        SELECT column1, column2, ... FROM [table_name] WHERE [Condition];
    ```
    Example: -
    ```sql
        SELECT emp_name, salary FROM Employee WHERE emp_id=12;
    ```

- ### ORDER BY command in SELECT Command:
    Syntax: -
    ```sql
        SELECT column1, column2, ... FROM [table_name] WHERE [Condition];
    ```
    Example: -
    ```sql
        SELECT * FROM users ORDER BY last_name ASC;
        SELECT * FROM users ORDER BY last_name DESC;
    ```

> ### Example:- 
> <div  style="display: flex; justify-content: space-evenly; flex-wrap: wrap;">
> <center>employees
> 
> | Emp_Id | First_Name | Last_Name | Status    | Salary |
> |--------|------------|-----------|-----------|--------|
> |      1 | Mary       | Williams  | Full Time |  35000 |
> |      2 | Robert     | Brown     | Full Time |  32000 |
> |      3 | Elizabeth  | Wilson    | Part Time |  12000 |
> |      4 | Jennifer   | Moore     | Full Time |  41000 |
> |      5 | Charles    | Brown     | Full Time |  39000 |
> |      6 | Lisa       | Price     | Part Time |  14000 |
> |      7 | Daniel     | Wood      | Part Time |  13750 |
> |      8 | Doniel     | Coleman   | Part Time |  37500 |
> |      9 | George     | Perry     | Part Time |  12050 |
> |     10 | Donna      | Steele    | Full Time |  36750 |
> |     11 | Carol      | Schultz   | Full Time |  38050 |
> 
> </center>
> 
> <center>address
> 
> | id | city       | pin_code | Emp_Id |
> |----|------------|----------|--------|
> |  1 | Saharanpur | 247451   |      1 |
> |  2 | Delhi      | 247454   |      7 |
> |  3 | Gangoh     | 247452   |      3 |
> |  6 | abc        | 247450   |     26 |
> 
> </center>
>
> </div>
>
> ### - Select data from single table
> - Select specified columns --    
>    ```sql
>       select Emp_Id, First_Name, Salary from employees;
>    ```
> - Select all columns --    
>    ```sql
>       select * from employees;
>    ```
>  
> ### - Select data from Multiple tables
>  Select employee data from employees and address table that address exists into address table.
> - Select specified columns --    >
>    ```sql
>       select Emp_Id, First_Name, Status, city, pin_code 
>       from employees, address 
>       where employees.Emp_Id = address.Emp_Id;
>   /* Error:
>    If you don't specify table name with column name and same column presesnt in two or more tables, there will be occur an ambiguity error:  Column 'Emp_Id' in field list is ambiguous. for Exp.
>   */ 
>
>   /* Solution 1:
>    You need to specify table name with specified column name that column name exact same as two or more tables from which you want to get data. for exp
>   */
>       select employees.Emp_Id, First_Name, Status, city, pin_code 
>       from employees, address 
>       where employees.Emp_Id = address.Emp_Id;
> 
>   /* Solution 2 (Best way):
>    You need to specify table name with all column names to resolve ambiguity. for exp
>   */
>       select employees.Emp_Id, employees.First_Name, employees.Status, address.city, address.pin_code 
>       from employees, address 
>       where employees.Emp_Id = address.Emp_Id;
>    ```
> - Select all columns --    
>    ```sql
>       select * from employees, address 
>       where employees.Emp_Id = address.Emp_Id;
>    ```



## 2. SELECT DISTINCT Command:  

MySQL **SELECT DISTINCT** Statement is used to retrieve only distinct(different) data from a field/column. 
It is very used to remove duplicates from the results. \
Syntax: -
```sql
  SELECT DISTINCT column1, column2, ...
  FROM table_name;
```


## 3. SELECT INTO Command:

The **SELECT INTO** statement is used to select data from a table and store it into variables or a new table. \
It allows you to retrieve data from one or more tables and assign the result set to variables or create a new table to hold the selected data.

 It is to note that the constraints from the source table are not copied to the destination table.

Syntax: -

### (A) Selecting Into Variables:
```sql
    SELECT column1, column2, ...
    INTO variable1, variable2, ...
    FROM table_name
    WHERE condition;
```

### (B) Selecting Into a New Table:
```sql
    SELECT column1, column2, ...
    INTO new_table_name
    FROM table_name
    WHERE condition;
```

<!-- Employee table -->
<table>
    <tr> <th colspan=5> <center> employee </center></th> </tr>
    <tr> <th>name</th> <th>occupation</th> <th>working_date</th> <th>working_hours</th> <th>salary</th> </tr>
    <tr> <td>Jolly Evans</td> <td>HR</td> <td>2020-10-04</td> <td>9</td> <td>25000</td> </tr>
    <tr> <td>Brayden Simmons</td> <td>Engineer</td> <td>2020-10-04</td> <td>12</td> <td>65000</td> </tr>
    <tr> <td>Rose Huges</td> <td>Writer</td> <td>2020-10-04</td> <td>13</td> <td>35000</td> </tr>
    <tr> <td>Laura Paul</td> <td>Manager</td> <td>2020-10-04</td> <td>10</td> <td>45000</td> </tr>
    <tr> <td>Diego Simmons</td> <td>Teacher</td> <td>2020-10-04</td> <td>12</td> <td>30000</td> </tr>
    <tr> <td>Antonio Bennet</td> <td>Writer</td> <td>2020-10-04</td> <td>13</td> <td>35000</td> </tr>
</table>
<br>


- If we want to copy all records of the **employee table** into the **backup_employee** table, we need to use the **SELECT INTO** statement.

    ```sql
        SELECT * 
        INTO backup_employee 
        FROM employee;  
    ```

> [!NOTE]
> **backup_employee** table automatically created. when query is execute and we don't need to create table explicitly. \
> because, 
**SELECT INTO** statement cannot be used to insert data into an existing table. To insert data into an existing table, you should use the **INSERT INTO** statement.


- If we want to copy only some rows of the **employee** table into the **backup_employee** table, we need to use the **SELECT INTO** statement with **WHERE** clause.
    ```sql
        SELECT * 
        INTO backup_employee 
        FROM employee
        WHERE salary>30000;  
    ```

- If we want to copy only some columns of the **employee** table into the **backup_employee** table, we need to specify the desired column names in the **SELECT INTO** statement.
    ```sql
        SELECT name, occupation, salary 
        INTO backup_employee 
        FROM employee;  
    ```

- **SELECT INTO Insert Data from multiple tables:** \
MySQL enables us to use the **JOIN clause** with the **SELECT INTO** statement. It helps us retrieve records from more than one table and then insert them into the new table. 

    ```sql
        SELECT cust.name, cust.email, O.item, O.price, O.prchase_date  
        INTO customer_orders 
        FROM customer AS cust   
        Inner JOIN orders AS O 
        ON cust.id = O.order_id;  
    ```


### Ques. What are the difference between INSERT INTO and SELECT INTO statements? 
Ans. Both the statements can be used to move data from one table into another table.

| INSERT INTO                                                                                                                                     | SELECT INTO                                                                                                                                                                                                                                                                |
| ----------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| We can use the INSERT INTO statement only when the target table exists in the database before copying data from the source to the target table. | The SELECT INTO statement does not require a target table to exist in our database before copying data from the source table. It automatically creates a target table whenever executed.                                                                                   |
| In INSERT INTO statement we are create table manually.                                                                                          | The SELECT INTO statement created the table structure automatically, which will be the same structure as the source table. It may lead to a problem while inserting the data. Suppose When we try to insert data in the column more than their size, we will get an error. |