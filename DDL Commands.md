 > # DDL Commands in MySQL:

Data Definition Language (DDL) commands are used in SQL to define, modify, and manage the structure of database objects. 
DDL changes the structure of the table like creating a table, deleting a table, altering a table, etc.
All the command of DDL are auto-committed that means it permanently save all the changes in the database. <br>
- [x] Create
- [x] Drop
- [x] Truncate
- [x] Alter (ADD, DROP, MODIFY, CHANGE, CONSTRAINTS)
 - Other
   - Use
   - Show tables
   - Show databases
   - Desc or describe
   - Rename


## (A) Operations on database:

### 1. CREATE DATABASE Command: -
Syntax:
```sql
    CREATE DATABASE [database_name];
```
Example: -
```sql
    CREATE DATABASE Banking_system;
```

### 2. DROP DATABASE Command (delete existing database): -
Syntax:
```sql
    DROP DATABASE [database_name];
```
Example: -
```sql
    DROP DATABASE Banking_system;
```

### 3. SHOW DATABASES Command: -
Syntax:
```sql
    SHOW DATABASES;
```

### 4. USE Command: -
Syntax:
```sql
    USE [database_name];
```
Example: -
```sql
    USE Banking_system;
```

### 5. Rename database: -
Please note that the ability to rename a database might be restricted depending on the database management system you are using and the permissions you have.
Syntax:
```sql
    ALTER DATABASE [current_name] MODIFY NAME = [new_name];
```
Example: -
```sql
    ALTER DATABASE Banking_system MODIFY NAME = Banking;
```

<br>

## (B) *Operations on Tables:* 

### 1. CREATE TABLE Command:
This command is used to create new database objects such as tables, views, indexes, or databases themselves.

Syntax to create a new table: -
```sql
    CREATE TABLE [table_name] (
        [column1] [datatype] [constraints],
        [column2] [datatype] [constraints],
        [column3] [datatype] [constraints],
        ....
    );
```

Example: -
```sql
    CREATE TABLE Users (
        id INT AUTO_INCREMENT,
        username VARCHAR(50) NOT NULL,
        email VARCHAR(100) NOT NULL,
        phoneNo NUMERIC(10) NOT NULL,
        created_at TIMESTAMP CURRENT_TIMESTAMP,
        PRIMARY KEY(id)
    );
```

you can create a table if it does not already exist using the **CREATE TABLE IF NOT EXISTS** statement. This statement ensures that the table is created only if it doesn't already exist in the database schema.

Syntax: -
```sql
    CREATE TABLE IF NOT EXISTS [table_name] (
        [column1] [datatype] [constraints],
        [column2] [datatype] [constraints],
        [column3] [datatype] [constraints],
        ....
    );
```

Example: -
```sql
    CREATE TABLE IF NOT EXISTS Users (
        id INT AUTO_INCREMENT,
        username VARCHAR(50) NOT NULL,
        email VARCHAR(100) NOT NULL,
        phoneNo NUMERIC(10) NOT NULL,
        created_at TIMESTAMP CURRENT_TIMESTAMP,
        PRIMARY KEY(id)
    );
```


## 2. DROP TABLE Command:

The DROP TABLE command deletes a table from the database.

Syntax: -
```sql
    DROP TABLE [table_name];
```

Example: -
```sql 
    DROP TABLE Users; 
```

## 3. TRUNCATE TABLE Command:

The TRUNCATE TABLE command deletes the data inside a table, but not the table itself.

Syntax: -
```sql
    TRUNCATE TABLE [table_name];
```

Example: -
```sql 
    TRUNCATE TABLE Users; 
```


## 4. DESCRIBE/DESC/SHOW Command:
Syntax: -
```sql
    DESC [table_name];
        or
    DESCRIBE [table_name];
        or
    SHOW COLUMNS FROM [table_name];
```

Example: -
```sql
    DESC Users;
        or
    DESCRIBE Users;
        or
    SHOW COLUMNS FROM Users;
```

## 5. RENAME TABLE Command:
Syntax: -
```sql
    RENAME TABLE [old_table_name] TO [new_table_name];
```

Example: -
```sql
    RENAME TABLE Users TO MyUsers;
```

## 6. SHOW TABLES (Show all tables of Database):
Syntex: -
```sql
    SHOW TABLES;
```


## 7. ALTER TABLE Command:

ALTER command is used to modify the structure of existing database objects like tables. 
It can add, modify, or drop columns, constraints, etc.


- ### Add new Column:
    Syntax:- 
    ```sql
    ALTER TABLE [table_name] ADD [column_name] [datatype] [constraints];
        Or
    ALTER TABLE [table_name] ADD COLUMN [column_name] [datatype] [constraints];
    ```
    
    Example: -
    ```sql
        ALTER TABLE Users ADD age INT;
        Or
        ALTER TABLE Users ADD COLUMN age INT;
    ```

- ### Add new Column by Position:
  - ### LAST (by default)
    Example:
    ```sql
        ALTER TABLE Users ADD COLUMN age INT;
    ```
  - ### FIRST
    Example:
    ```sql
        ALTER TABLE Users ADD COLUMN age INT FIRST;
    ```
  - ### AFTER
    Example:
    ```sql
        ALTER TABLE Users ADD COLUMN age INT AFTER email;
    ```

- ### Drop/Delete existing Column:
    Syntax: -
    ```sql
        ALTER TABLE [table_name] DROP [column_name];
        Or
        ALTER TABLE [table_name] DROP COLUMN [column_name];
    ```
    
    Example: -
    ```sql
        ALTER TABLE Users DROP age;
        Or
        ALTER TABLE Users DROP COLUMN age;
    ```

- ### Modify a existing Column (Change datatype or constraints):

    Syntax: -
    ```sql
    ALTER TABLE [table_name] MODIFY [column_name] [new_datatype] [new_constraint];
    Or
    ALTER TABLE [table_name] MODIFY COLUMN [column_name] [new_datatype] [new_constraint];
    ```

    Example: -
    ```sql
    ALTER TABLE Users MODIFY age NUMERIC(3) NOT NULL;
    Or
    ALTER TABLE Users MODIFY COLUMN age NUMERIC(3) NOT NULL;
    ```

- ### Rename a Column:

    Syntax: -
    ```sql
    ALTER TABLE [table_name] CHANGE [old_column_name] [new_column_name] [datatype];
    <!-- Rename multiple columns -->
    ALTER TABLE [table_name] CHANGE [old_column_name] [new_column_name] [datatype],
                             CHANGE [old_column_name] [new_column_name] [datatype], ...;
    ```

    Example: -
    ```sql
    ALTER TABLE Users CHANGE age new_age int(11);
    ```

## 8. Apply constraints: 
Constraints are rules that specify what data can be stored in a table.
Constraints helps in validate of data being inserted or updated in a database against predefined rules for maintaining the integrity and consistency of the database.

> ### **AUTO_INCREMENT Attribute:**
> AUTO_INCREMENT is a feature used to automatically generate a unique numeric value for a column whenever a new row is inserted into a table. It's commonly used for primary key columns to ensure each row has a unique identifier.
> By default, the starting value for AUTO_INCREMENT is 1, and it will increment by 1 for each new record.
> 
> Example:
> ```sql
>       CREATE TABLE users (
>          user_id INT AUTO_INCREMENT PRIMARY KEY,
>          username VARCHAR(50),
>          email VARCHAR(100)
>       );
> ```
>
> To let the AUTO_INCREMENT sequence start with another value, use the following SQL statement:
> 
> Example:
> ```sql
>       CREATE TABLE users (
>          user_id INT AUTO_INCREMENT=100 PRIMARY KEY,
>          username VARCHAR(50),
>          email VARCHAR(100)
>       );
> ```

> Types of Constrants:

> - **NOT NULL-**  The NOT NULL constraint is used to ensure that a column does not contain any NULL values.  You can apply the **NOT NULL** constraint to multiple columns within a table. \
In some cases, you can define a **default** value for a column with a **NOT NULL** constraint. If a value is not provided during insertion, the default value will be used instead. \
NOT NULL constraint is typically applied at the column level to ensure that a column must always contain a value and cannot be NULL.\
 However, MySQL does not support applying the NOT NULL constraint at the table level directly. <br>\
you can apply the NOT NULL constraint on column level by two ways -- \
>   (i) Using **CREATE TABLE** Command: \
>   Syntax:
>   ```sql
>       CREATE TABLE [table_name] (
>           [column1] [datatype] NOT NULL,
>           [column2] [datatype] NOT NULL,
>           [column3] [datatype] NOT NULL,
>           ....
>       );
>   ```
>   Example: -
>   ```sql
>       CREATE TABLE Employee(
>           emp_id int NOT NULL,
>           emp_name varchar(100) NOT NULL,
>           emp_email varchar(200),
>           ....
>       );
>   ```
>   (ii) Using **ALTER TABLE** Command: \
>   Syntax:
>   ```sql
>       ALTER TABLE [table_name]
>       MODIFY COLUMN [column_name] [data_type] NOT NULL;
>   ```
>   Example: -
>   ```sql
>       ALTER TABLE Employee
>       MODIFY COLUMN emp_name varchar(150) NOT NULL;
>   ```
>
>      ## How to remove NOT NULL Constraint
>   Syntax: -
>   ```sql
>       ALTER TABLE [table_name]
>       MODIFY COLUMN [column_name] [datatype] NULL;
>   ```

> - **UNIQUE-** UNIQUE constraints ensure that the values within a column or a group of columns are unique. They ensure that two rows in the table does't have the same value(s) for the specified column(s). <br>
**NULL** value is considered as unique, so multiple NULL values are allowed. <br>
When a UNIQUE constraint is defined, the database system automatically checks for duplicates when new rows are inserted or existing rows are updated. If a duplicate value is detected, the database will raise an error, and the operation will fail. <br>\
Types of Unique Constraint -- \
>   (1) Single-column Unique Constraint: \
>   (2) Composite (multi-column) Unique Constraint: <br>
> 
>   **(1) Single-column Unique Constraint**: 
> This type of constraint ensures that each value in a specified column is unique across all rows in the table. 
> 
>   (a) Using **CREATE TABLE** Command: 
> 
>   Syntax: -
>   ```sql
>       CREATE TABLE [table_name] (
>           [column1] [datatype] UNIQUE,
>           [column2] [datatype],
>           [column2] [datatype] UNIQUE,
>           ...
>        );
>                   OR
>       CREATE TABLE [table_name] (
>           [column1] [datatype],
>           [column2] [datatype],
>           [column3] [datatype],
>           UNIQUE(column1),
>           UNIQUE(column2),
>           ...
>        );
>   ```
>   Example: -
>   ```sql
>       CREATE TABLE Employee(
>           emp_id int UNIQUE,
>           emp_name varchar(100),
>           emp_email varchar(200) UNIQUE,
>       );
>               OR
>       CREATE TABLE Employee(
>           emp_id int,
>           emp_name varchar(100),
>           emp_email varchar(200),
>           UNIQUE(emp_id),
>           UNIQUE(emp_email),
>       );
>   ```
>
>   (b) Using **ALTER TABLE** Command: \
>   Syntax: -
>   ```sql
>       ALTER TABLE [table_name]
>       ADD CONSTRAINT [constraint_name]
>       UNIQUE (column_name);
>           OR
>       ALTER TABLE [table_name]
>       MODIFY COLUMN [column_name] UNIQUE;
>           OR
>       ALTER TABLE [table_name]
>       MODIFY COLUMN [column_name] [data_type] UNIQUE;
>   ```
>   Example: -
>   ```sql
>       ALTER TABLE Employee
>       ADD CONSTRAINT unique_id
>       UNIQUE (emp_id);
> 
>   /* Note: This command adds a UNIQUE constraint named unique_id to the emp_id column in the Employees table. */
>   /* If you don't provide 'constraint_name', it will be generate an error. */
>   ``` 
> 
>   **(2) Composite (multi-column) Unique Constraint**: 
> This type of constraint ensures that  the combination of values across multiple columns is unique across all rows in the table. \
> you can create a composite unique constraint involving any number of columns.
> 
>   (a) Using **CREATE TABLE** Command: 
> 
>   Syntax: -
>   ```sql
>       CREATE TABLE [table_name] (
>           [column1] [datatype],
>           [column2] [datatype],
>           [column3] [datatype],
>           UNIQUE(column1, column2, ...),
>           ...
>        );
>   ```
>   Example: -
>   ```sql
>       CREATE TABLE students (
>           student_id INT PRIMARY KEY,
>           email VARCHAR(100),
>           student_code VARCHAR(20),
>           UNIQUE (email, student_code)
>       );
>
>   /* So, the combination of columns 'email' and 'student_code' must be unique in each row. you can provide any number of column.
>   */
>   ```
>
>   (b) Using **ALTER TABLE** Command: \
>   Syntax: -
>   ```sql
>       ALTER TABLE [table_name]
>       ADD CONSTRAINT [constraint_name]
>       UNIQUE (column1_name, column2_name, ...);
>            OR
>       ALTER TABLE [table_name] ADD CONSTRAINT
>       UNIQUE (column1_name, column2_name, ...);        
>   ```
>
>      ## How to remove UNIQUE Constraint
>   Syntax: -
>   ```sql
>      ALTER TABLE [table_name] DROP INDEX [index_name];
>   ```

> - **DEFAULT-**
> The DEFAULT constraint is used to specify a default value for a column when a new row is inserted into a table and no explicit value is provided for that column.
>
>   (a) Using **CREATE TABLE** Command: 
> 
>   Syntax: -
>   ```sql
>       CREATE TABLE [table_name] (
>          [column_name] [datatype] DEFAULT default_value,
>           ...
>        );
>   ```
>   Example: -
>   ```sql
>       CREATE TABLE students (
>           student_id INT PRIMARY KEY,
>           gender VARCHAR(100) DEFAULT "Male",
>           email VARCHAR(100),
>           admission_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
>       );
>
>   /* if user not provide value of gender column, its default value 'Male' will be set on column gender.
>   */
>   ```
>
>   (b) Using **ALTER TABLE** Command: \
>   Syntax: -
>   ```sql
>       ALTER TABLE [table_name]
>       ALTER COLUMN [column_name] SET DEFAULT [default_value];     
>           OR
>       ALTER TABLE [table_name]
>       MODIFY COLUMN [column_name] [data_type] 
>       DEFAULT default_value;    
>           OR
>       ALTER TABLE [table_name]
>       MODIFY COLUMN [column_name]
>       DEFAULT default_value;
>   ```
>
>   Example: -
>   ```sql
>       ALTER TABLE students
>       ALTER COLUMN admission_date SET DEFAULT [CURRENT_TIMESTAMP]; 
>   ```
>
>   ## How to remove DEFAULT constraint?
>   Syntax: -
>   ```sql
>      ALTER TABLE [table_name]
>      ALTER COLUMN [column_name] DROP DEFAULT;
>   ```
>
>   Example: -
>   ```sql
>      ALTER TABLE employees
>      ALTER COLUMN salary DROP DEFAULT;
>   ```
>
> - **Check-**
> A CHECK constraint is a type of constraint that allows you to specify a condition that each row must satisfy for it to be valid. \
> However, MySQL does not directly support CHECK constraints until version 8.0.16. 
>
>   (a) Using **CREATE TABLE** Command: 
> 
>   Syntax: -
>   ```sql
>       CREATE TABLE [table_name] (
>          [column_name] [datatype],
>          [column_name] [datatype],
>           ... ,
>          CHECK (condition)
>        );
>   ```
>   Example: -
>   ```sql
>        CREATE TABLE employees (
>            employee_id INT PRIMARY KEY,
>            name VARCHAR(100),
>            age INT,
>            CHECK (age >= 18)
>        );
>   /* If you attempt to insert a row with an age less than 18, MySQL will generate an error. *?
>   ```
>
>   (b) Using **ALTER TABLE** Command: 
> 
>   Syntax: -
>   ```sql
>       ALTER TABLE [table_name]
>       ADD CONSTRAINT [constraint_name] CHECK (condition);
>   ```
>
>   Example: -
>   ```sql
>       ALTER TABLE employees
>       ADD CONSTRAINT check_age_gender 
>       CHECK (
>            (gender = 'Male' AND age BETWEEN 18 AND 65) OR
>            (gender = 'Female' AND age BETWEEN 18 AND 60)
>       );
>   ```
>
>   ## How to remove Check constraint?
>   Syntax: -
>   ```sql
>       ALTER TABLE [table_name] 
>       MODIFY COLUMN [column_name] [data_type];
>   ```


> - **Primary key-** A Primary Key constraint is a column or a combination of columns that is used to uniquely identifies each row(record) in a table. It ensures that each value in the specified column(s) is unique and not NULL. \
> A PRIMARY KEY constraint can be applied to one or more columns at the table level. If multiple columns are specified, their combination must be unique across all rows. \
> A composite Primary Key involves multiple columns, creating a unique combination of values across those columns. <br> \
>**(1) Single-column PRIMARY KEY Constraint:** This type of constraint ensures that each value in a specified column is unique and NOT NULL across all rows in the table.
> 
>   (a) Using **CREATE TABLE** Command: 
> 
>   Syntax: -
>   ```sql
>       CREATE TABLE [table_name] (
>          [column_name] [datatype] PRIMARY KEY,
>          [column_name] [datatype],
>           ... 
>        );
>               OR
>       CREATE TABLE [table_name] (
>          [column_name] [datatype],
>          [column_name] [datatype],
>           ... ,
>           PRIMARY KEY(column_name)
>        );
>   ```
>   Example: -
>   ```sql
>        CREATE TABLE employees (
>            employee_id INT PRIMARY KEY,
>            name VARCHAR(100),
>            age INT
>        );
>               OR
>        CREATE TABLE employees (
>            employee_id INT,
>            name VARCHAR(100),
>            age INT,
>            PRIMARY KEY(employee_id)
>        );
>   ```
>
>   (b) Using **ALTER TABLE** Command: 
> 
>   Syntax: -
>   ```sql
>       ALTER TABLE [table_name]
>       ADD CONSTRAINT [pk_constraint_name] PRIMARY KEY (column_name);
>   ```
>
>   Example: -
>   ```sql
>       ALTER TABLE student
>       ADD CONSTRAINT pk_student_id PRIMARY KEY (student_id);
>   ```
>
>   **(2) Composite (multi-column) PRIMARY KEY Constraint**: 
> You can also create a composite PRIMARY KEY constraint by specifying multiple columns. This means that the combination of values across these columns must be unique. 
> 
>   (a) Using **CREATE TABLE** Command: 
> 
>   Syntax: -
>   ```sql
>       CREATE TABLE [table_name] (
>           [column1] [datatype],
>           [column2] [datatype],
>           [column3] [datatype],
>           PRIMARY KEY(column1, column2, ...),
>           ...
>        );
>   ```
>   Example: -
>   ```sql
>       CREATE TABLE students (
>           student_id INT,
>           phoneNo varchar(10),
>           email VARCHAR(100),
>           student_code VARCHAR(20),
>           PRIMARY KEY(student_id, phoneNo)
>       );
>   ```
>
>   (b) Using **ALTER TABLE** Command: \
>   Syntax: -
>   ```sql
>       ALTER TABLE [table_name]
>       ADD CONSTRAINT [primary_key_name]
>       PRIMARY KEY (column1_name, column2_name, ...);
>   ```
>
>   Example: -
>   ```sql
>       ALTER TABLE students
>       ADD CONSTRAINT pk_student_id_phone 
>       PRIMARY KEY (student_id, phoneNo);
>   ```
>   ## How to remove primary key? 
>   Syntax:
>   ```sql
>       ALTER TABLE [table_name]
>       DROP PRIMARY [Primary_key_name];
>           OR
>       ALTER TABLE table_name
>       DROP PRIMARY KEY;
>   ```
>   Example:
>   ```sql
>       ALTER TABLE student
>       DROP PRIMARY [pk_student_id_phone];
>   ```


> - **Foreign key-** A Foreign Key (FK) constraint is a column or a set of columns in one table that refers to the Primary Key (PK) or a Unique Key (UK) in another table. \
> It defines a relationship between the two tables, enforcing referential integrity. \
> A table can have multiple Foreign Key constraints, each referring to different referenced tables or even the same table. \
> Establishing one-to-many or many-to-many relationships between tables. \
> Implementing parent-child relationships, such as in hierarchical data models. \
> The table with the foreign key is called the child table, and the table with the primary key is called the referenced or parent table. \
> A foreign key is created in the CREATE TABLE or ALTER TABLE statement. The foreign key in a table should match the primary key in the referenced table for every row. This is called Referential Integrity. \
> The table in which a foreign key is defined is called a Foreign table/Child table/Referencing table. and the table that defines a primary key and is referenced by a foreign key is called a Primary table/Parent table /Referenced Table. 
>
>    <u>**Properties:**</u>
> 1. The child field may have duplicates and nulls.
> 2. Parent records can be deleted if no child exists.
> 3. The master (parent) table cannot be updated if a child exists.
> 4. Records cannot be inserted in the child table if a corresponding record in the master table does not exist.
> 5. Records of the master table cannot be deleted if corresponding records in the child table exist.
> 6. Single-column foreign keys accept null values.
>
>     **There are two ways to add a foreign key to the table--**
>> 1. Using **CREATE TABLE**.
>> 2. Using **ALTER TABLE**.
>
>
>> 1. Using **CREATE TABLE** Command: \
> Syntax:
> ```sql
>       CREATE TABLE [table_name] (
>           [column1_name] [data_type] REFERENCES [parent_table_name], 
>           [column2_name] [data_type]
>       );
>                OR
>       CREATE TABLE [table_name] (
>           [column1_name] [data_type] REFERENCES [parent_table_name]([pk_column_name]), 
>           [column2_name] [data_type]
>       );
>                OR
>       CREATE TABLE [table_name] (
>           [column1_name] [data_type], 
>           [column2_name] [data_type],
>           FOREIGN KEY(child_table_col_name) REFERENCES  [parent_table_name]
>       );
>                OR
>       CREATE TABLE [table_name] (
>           [column1_name] [data_type], 
>           [column2_name] [data_type],
>           FOREIGN KEY(child_table_col_name) REFERENCES  [parent_table_name]([pk_column_name])
>       );
>                OR
>       CREATE TABLE [table_name] (
>           [column1_name] [data_type], 
>           [column2_name] [data_type],
>           CONSTRAINT [constraint_name] FOREIGN KEY(child_table_col_name) 
>           REFERENCES  [parent_table_name]([pk_column_name])
>       );
> ```
> <hr>
> <h3>NOTE:</h3>
> If there is a single columnar Primary key in the table, the column name in syntax can be omitted. So both the above syntax works correctly. 
> <hr>
> <br>
> 
> Example:
> ```sql
>     CREATE TABLE customers (
>         customer_id INT PRIMARY KEY,
>         customer_name VARCHAR(100)
>     );
>     
>     CREATE TABLE orders (
>         order_id INT PRIMARY KEY,
>         order_date DATE,
>         customer_id INT,
>         FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
>     );
>           OR
>     CREATE TABLE orders (
>         order_id INT PRIMARY KEY,
>         order_date DATE,
>         customer_id INT,
>         CONSTRAINT fk_customer_id FOREIGN KEY (customer_id) 
>         REFERENCES customers(customer_id)
>     );
> ```
>
>
> 2. Using **ALTER TABLE** Command: \
> Syntax:
>    ```sql
>        ALTER TABLE [child_table_name]
>        ADD CONSTRAINT [constraint_name]
>        FOREIGN KEY (foreign_key_column_name)
>        REFERENCES [parent_table_name] (primary_key_column_name);
>
>           OR
>        ALTER TABLE [child_table_name]
>        ADD FOREIGN KEY (foreign_key_column_name)
>        REFERENCES [parent_table_name] (primary_key_column_name);
>    ```
>
>    Example:
>    ```sql
>        CREATE TABLE customers (
>            customer_id INT PRIMARY KEY,
>            customer_name VARCHAR(100)
>        );
>
>        CREATE TABLE orders (
>            order_id INT PRIMARY KEY,
>            order_date DATE,
>            customer_id INT
>        );
>
>        ALTER TABLE orders
>        ADD CONSTRAINT fk_customer_id
>        FOREIGN KEY (customer_id)
>        REFERENCES customers(customer_id);
>    ```
>
>    <h2>DROP a FOREIGN KEY Constraint</h2>
>   Syntax:
>    ```sql
>        ALTER TABLE [table_name]
>        DROP CONSTRAINT [constraint_name];
>    ```
>   Example:
>    ```sql
>        ALTER TABLE orders
>        DROP CONSTRAINT fk_customer_id;
>               OR
>        ALTER TABLE orders
>        DROP FOREIGN KEY fk_customer_id;
>    ```
>
>
> <h2>Actions on Update or Delete: </h2>
>  When you define a foreign key constraint between two tables, you often have the option to specify what should happen if the referenced row in the parent table is updated or deleted. <br>
> These actions help maintain data integrity and consistency within the database. 
>  
>  Syntax: Using **CREATE TABLE**
>   ```sql
>        CREATE TABLE [child_table_name] (
>            [column1] [datatype],
>            [column2] [datatype],
>            FOREIGN KEY (foreign_key_column_name)
>            REFERENCES [parent_table_name](primary_key_column_name)
>            ON UPDATE [action_on_update]
>        );
>           OR
>        CREATE TABLE [child_table_name] (
>            [column1] [datatype],
>            [column2] [datatype],
>            FOREIGN KEY (foreign_key_column_name)
>            REFERENCES [parent_table_name](primary_key_column_name)
>            ON DELETE [action_on_delete]
>        );
>           OR
>        CREATE TABLE [child_table_name] (
>            [column1] [datatype],
>            [column2] [datatype],
>            FOREIGN KEY (foreign_key_column_name)
>            REFERENCES [parent_table_name](primary_key_column_name)
>            ON UPDATE [action_on_update]
>            ON DELETE [action_on_delete]
>        );
>    ```

>
> Syntax: Using **ALTER TABLE**
>
>   ```sql
>        ALTER TABLE [child_table_name]
>        ADD CONSTRAINT [constraint_name]
>        FOREIGN KEY (foreign_key_column_name)
>        REFERENCES [parent_table_name] (primary_key_column_name)
>        ON UPDATE [action_on_update];
>               OR
>        ALTER TABLE [child_table_name]
>        ADD CONSTRAINT [constraint_name]
>        FOREIGN KEY (foreign_key_column_name)
>        REFERENCES [parent_table_name] (primary_key_column_name)
>        ON DELETE [action_on_delete];
>               OR
>        ALTER TABLE [child_table_name]
>        ADD CONSTRAINT [constraint_name]
>        FOREIGN KEY (foreign_key_column_name)
>        REFERENCES [parent_table_name] (primary_key_column_name)
>        ON UPDATE [action_on_update]
>        ON DELETE [action_on_delete];
>    ```


<table border=2px align=center>
    <legend align=center>On Update</legend>
  <tr>
    <th> Actions ON UPDATE </th> <th> Description </th>
  </tr>

  <tr>
    <td> CASCADE </td> 
    <td>  If a referenced row in the parent table is updated, all corresponding rows in the child table are automatically updated to reflect the changes. </td>
  </tr>

  <tr>
    <td> SET NULL </td> 
    <td> If a referenced row in the parent table is updated, the foreign key column(s) in the child table are set to NULL. This is useful when you want to allow the deletion of the parent row without deleting the corresponding rows in the child table </td>
  </tr>

  <tr>
    <td> SET DEFAULT </td> 
    <td> Similar to SET NULL, but instead of setting the foreign key column(s) to NULL, they are set to their default values specified during table creation. </td>
  </tr>

  <tr>
    <td> RESTRICT </td> 
    <td> This prevents the update operation on the parent table if there are dependent rows in the child table. </td>
  </tr>

  <tr>
    <td> NO ACTION </td> 
    <td>  This is similar to RESTRICT. It also prevents the update operation on the parent table if there are dependent rows in the child table.</td>
  </tr>

</table>

<table border=2px align=center>
    <legend align=center>On Delete</legend>
  <tr>
    <th> Actions ON DELETE </th> <th> Description </th>
  </tr>

  <tr>
    <td> CASCADE </td> 
    <td> If a referenced row in the parent table is deleted, all corresponding rows in the child table are automatically deleted.  </td>
  </tr>

  <tr>
    <td> SET NULL </td> 
    <td> If a referenced row in the parent table is deleted, the foreign key column(s) in the child table are set to NULL. This is useful when you want to allow the deletion of the parent row without deleting the corresponding rows in the child table.</td>
  </tr>

  <tr>
    <td> SET DEFAULT </td> 
    <td> Similar to SET NULL, but instead of setting the foreign key column(s) to NULL, they are set to their default values specified during table creation. </td>
  </tr>

  <tr>
    <td> RESTRICT </td> 
    <td> This prevents the delete operation on the parent table if there are dependent rows in the child table. </td>
  </tr>

  <tr>
    <td> NO ACTION </td> 
    <td> This is similar to RESTRICT. It also prevents the delete operation on the parent table if there are dependent rows in the child table. </td>
  </tr>

</table>






### Example apply all Constraints Using the CREATE TABLE command:
Syntax: -
```sql
CREATE TABLE departments (
        department_id INT,
        department_name VARCHAR(100) NOT NULL,
        PRIMARY KEY(department_id)
);

CREATE TABLE employees (
        emp_id INT PRIMARY KEY AUTO_INCREMENT,
        emp_name VARCHAR(100) NOT NULL,
        age INT CHECK (age >= 18),
        salary DECIMAL(10, 2) DEFAULT 50000.00,
        email VARCHAR(100) NOT NULL UNIQUE, -- You can apply multiple constrants
        department_id INT,
        FOREIGN KEY (department_id) REFERENCES departments(department_id)
        ON DELETE cascade
);   
```




