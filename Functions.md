## Functions in MySQL:
<h3>

1. <a href="#stringFunctions">String Functions</a>
2. <a href="#numericFunctions">Numeric Functions</a>
3. <a href="#dateTimeFunctions">Date and Time Functions</a>
4. <a href="#aggregateFunctions">Aggregate Functions</a>

</h3>

<!-- String function start -->
<h3 id="stringFunctions">1. String Functions:-</h3>

String functions in MySQL are a set of built-in functions that are designed to perform operations on string values.

<table>
<tbody>
<tr>
    <th>String Functions</th>
    <th>Description</th>
</tr>
<tr>
    <td><a href="#upperCaseFunction">UCASE( ) / UPPER()</a></td>
    <td>Converts all characters in a string to uppercase.</td>
</tr>
<tr>
    <td><a href="#lowerCaseFunction">LCASE( ) / LOWER()</a></td>
    <td>Converts all characters in a string to lowercase.</td>
</tr>
<tr>
    <td><a href="#lengthFunction">LENGTH( )</a></td>
    <td>Returns the length of a string.</td>
</tr>
<tr>
    <td><a href="#concatFunction">CONCAT( )</a></td>
    <td>Concatenates two or more strings together.</td>
</tr>
</tr>
<tr>
    <td><a href="#substrFunction">SUBSTRING( ) / SUBSTR( )</a></td>
    <td>Extracts a substring from a string.</td>
</tr>
<tr>
    <td><a href="#replaceFunction">REPLACE( )</a></td>
    <td>Replaces all occurrences of a substring within a string with another substring.</td>
</tr>
<tr>
    <td><a href="#trimFunction">TRIM( )</a></td>
    <td>Removes leading and/or trailing spaces (or specified characters) from a string.</td>
</tr>
<tr>
    <td><a href="#leftFunction">LEFT( )</a></td>
    <td>Returns the leftmost characters from a string.</td>
</tr>
<tr>
    <td><a href="#rightFunction">RIGHT( )</a></td>
    <td>Returns the rightmost characters from a string.</td>
</tr>
<tr>
    <td><a href="#repeatFunction">REPEAT( )</a></td>
    <td>Repeats a string a specified number of times.</td>
</tr>
<tr>
    <td><a href="#strcmpFunction">STRCMP( )</a></td>
    <td>Compares two strings.</td>
</tr>
<tr>
    <td><a href="#concatWSFunction">CONCAT_WS( )</a></td>
    <td>Concatenates multiple strings with a specified separator between them.</td>
</tr>
</tbody>
</table>

<!-- Function Explaination -- -->
<h3 id="upperCaseFunction">(A) UCASE( ) / UPPER() Function:</h3>

Both **UCASE()** and **UPPER()** functions are used to convert a string to uppercase. \
If the input string is **NULL**, both functions return **NULL**.

### Syntax:
```sql
    UCASE(column_name);  -- It convert String of entire column into Upper Case.
    UCASE(String);
        OR
    UPPER(column_name);
    UPPER(String);
```

### Example:
```sql
    SELECT UCASE("Hello World");    -- HELLO WORLD
    SELECT UCASE(first_name) AS Employee_name from Employee;
        OR
    SELECT UPPER("Hello World");    -- HELLO WORLD
    SELECT UPPER(first_name) AS Employee_name from Employee;
```



<h3 id="lowerCaseFunction">(B) LCASE( ) / LOWER() Function:</h3>

Both **LCASE()** and **LOWER()** functions are used to convert a string to lowercase. \
If the input string is **NULL**, both functions return **NULL**.

### Syntax:
```sql
    LCASE(column_name);   -- It convert String of entire column into Lower Case.
    LCASE(String);
        OR
    LOWER(column_name);
    LOWER(String);
```

### Example:
```sql
    SELECT LCASE("Hello World");    -- hello world
    SELECT LCASE(first_name) AS Employee_name from Employee;
        OR
    SELECT LOWER("Hello World");    -- hello world
    SELECT LOWER(first_name) AS Employee_name from Employee;
```


<h3 id="lengthFunction">(C) LENGTH( ) Function:</h3>

The **LENGTH()** function is used to return the length of a string. It counts the total number of characters in a given string, including spaces and special characters. \
It returns **NULL** if the input string is **NULL**.

### Syntax:
```sql
    LENGTH(column_name); 
    LENGTH(String);
```

### Example:
```sql
    SELECT LENGTH("Hello World");    -- 11
    SELECT LENGTH(first_name) AS Employee_name from Employee;
```


<h3 id="concatFunction">(D) CONCAT( ) Function:</h3>

The **CONCAT()** function in MySQL is used to concatenate two or more strings together. It takes multiple string arguments and returns a single string that is the concatenation of all the input strings.

### Syntax:
```sql
    CONCAT(string1, string2, ...); 
    CONCAT(column_name1, column_name2, ...);
```

### Example:
```sql
    SELECT CONCAT('Hello', ' ', 'World');   -- Hello World
        OR
    -- You can also concatenate column values from a table using the CONCAT() function.
    SELECT CONCAT(first_name, ' ', last_name) AS full_name
    FROM employees;
```

> [!NOTE]
> If any of the input strings is **NULL**, the **CONCAT()** function returns **NULL**. To handle **NULL** values.
> ### Example:
> ```sql
>     -- This query will return NULL because one of the input strings is NULL.
>     SELECT CONCAT('Hello', Null, 'World');   -- Null
> 
>     -- To handle NULL values and prevent the CONCAT() function from returning NULL, you can use IFNULL().
>     SELECT CONCAT(IFNULL('Hello', ''), ' ', IFNULL(NULL, ''), 'World'); -- Hello World, replacing the NULL value with an empty string.
> ```


<h3 id="substrFunction">(E) SUBSTRING( ) / SUBSTR( ) Function:</h3>

It allows you to retrieve a portion of a string based on a specified starting position and length. 

### Syntax:
```sql
    SUBSTRING(string, start_position, length); 
    SUBSTRING(column_name, start_position, length);
```
  - **string:** The string from which the substring will be extracted.
  - **start_position:** The position within the string where the extraction will begin. It is a numeric value representing the character position (1-based index) within the string. If the start_position is positive, the extraction starts from the beginning of the string. If negative, it starts from the end of the string.
  - **length (Optional):** The number of characters to be extracted from the string.

### Example:
```sql
    SELECT SUBSTRING('Hello World', 1, 5); -- Returns 'Hello'
    
    SELECT SUBSTRING('Hello World', -5); -- Returns 'World'

    SELECT SUBSTRING('Hello World', 7); -- Returns 'World'
```


<h3 id="replaceFunction">(F) REPLACE( ) Function:</h3>

It is commonly used to perform find and replace operations on text data stored in database tables. \
The **REPLACE()** function is used to replace all occurrences substring within a string with another substring. \
The **REPLACE()** function is **case-sensitive**. It will only replace exact matches of the search string. \
If the search string is not found in the original string, no replacement will occur, and the original string will be returned unchanged. \
If any of the parameters to the **REPLACE()** function are **NULL**, the function returns **NULL**.

### Syntax:
```sql
    REPLACE(original_string, search_string, replacement_string); 
    REPLACE(column_name, search_string, replacement_string);
```

### Example:
```sql
    SELECT REPLACE('Hello, old world!', 'old', 'new');  -- Hello, new world!
            OR
    -- You can update/modify data into database.
    UPDATE products
    SET description = REPLACE(description, 'old', 'new');
```


<h3 id="trimFunction">(G) TRIM( ) Function:</h3>

The **TRIM()** function in MySQL is used to remove spaces(default) or specified characters from leading(beginning) or trailing(end) or both(beginning and end) from a string. 

### Syntax:
```sql
    TRIM(string); -- remove space from both(beginning and end).
    TRIM( [removal_string] FROM [string] ); -- remove specified character from both(beginning and end).
    TRIM( [BOTH | LEADING | TRAILING] [removal_string] FROM [string] ); 
    TRIM( [BOTH | LEADING | TRAILING] [removal_string] FROM [column_name] ); 
```

  - **BOTH (default)(optional):** Removes characters from both(beginning and end) of the string.
  - **LEADING(optional):** Removes characters only from the beginning of the string.
  - **TRAILING(optional):** Removes characters only from the end of the string.
  - **removal_string(optional):** Optional. Specifies the characters (or character) to remove from the string. If not specified, TRIM() removes spaces.

### Example:
```sql
    SELECT TRIM('   Hello   ');  -- Hello
    SELECT TRIM('x' FROM 'xxHellox');  -- Hello, remove 'x' character from both(beginning and end) of the string 
    SELECT TRIM(LEADING '0' FROM '0001230'); -- 1230 , remove '0' character from start of the string 
    SELECT TRIM(TRAILING 'x' FROM 'Helloxx');  -- Hello , remove 'x' character from end of the string 
```


<h3 id="leftFunction">(H) LEFT( ) Function:</h3>

It is commonly used to retrieve a substring from the beginning of a string. \
When you specify a negative value for the length parameter in the **LEFT()** function, MySQL interprets(consider) it as 0 and returns an empty string.  \
If the input string is **NULL**, the **LEFT()** function returns **NULL**.

### Syntax:
```sql
    LEFT(string, length);
    LEFT(column_name, length);
```
  
  - **string:** The string from which you want to extract characters.
  - **length:** The number of characters to extract from the left side of the string.

### Example:
```sql
    SELECT LEFT('Hello World', 5);  -- Hello
    SELECT LEFT('Hello World', 0);  -- ''
    SELECT LEFT('Hello World', -3);  -- ''
```


<h3 id="rightFunction">(I) RIGHT( ) Function:</h3>

It is commonly used to retrieve a substring from the end of a string. \
When you specify a negative value for the length parameter in the **RIGHT()** function, MySQL interprets(consider) it as 0 and returns an empty string.  \
If the input string is **NULL**, the **RIGHT()** function returns **NULL**.

### Syntax:
```sql
    RIGHT(string, length);
    RIGHT(column_name, length);
```
  
  - **string:** The string from which you want to extract characters.
  - **length:** The number of characters to extract from the right side of the string.

### Example:
```sql
    SELECT RIGHT('Hello World', 5); -- World
    SELECT RIGHT('Hello World', 0);  -- ''
    SELECT RIGHT('Hello World', -3);  -- ''
```


<h3 id="repeatFunction">(J) REPEAT( ) Function:</h3>

The **REPEAT()** function in MySQL is used to repeat a string a specified number of times. \
If the count parameter is negative or zero, the **REPEAT()** function returns an empty string. \
If the input string is **NULL**, the **REPEAT()** function returns **NULL**.

### Syntax:
```sql
    REPEAT(string, count);
```
  
  - **string:** The string that you want to repeat.
  - **count:** The number of times you want to repeat the string.

### Example:
```sql
    SELECT REPEAT('Hello', 3); -- HelloHelloHello
    SELECT REPEAT('Hello', 0);  -- ''
    SELECT REPEAT('Hello', -3);  -- ''
```


<h3 id="strcmpFunction">(K) STRCMP( ) Function:</h3>

The **STRCMP()** function in MySQL is used to compare two strings. \
It returns 0 if the strings are equal, a negative value(-1) if the first string is less than the second string, and a positive value(1) if the first string is greater than the second string. \
It's particularly useful when you need to compare strings in a case-sensitive manner. \
If either string1 or string2 is NULL, the function returns NULL.

### Syntax:
```sql
    STRCMP(string1, string2);
    STRCMP(column_name1, column_name2);
```
  
### Example:
```sql
    SELECT STRCMP('Hello', 'Hello'); -- 0
    SELECT STRCMP('Hello', 'hello'); -- 0
    SELECT STRCMP('Hello', 'hello1'); -- -1
    SELECT STRCMP('Hello', 'Dear');  -- 1
```


<h3 id="concatWSFunction">(L) CONCAT_WS( ) Function:</h3>

The **CONCAT_WS()** function in MySQL is used to concatenate multiple strings into a single string with a specified separator between them. Unlike the regular **CONCAT()** function, which concatenates strings without any separator. \
If any of the input strings are **NULL**, **CONCAT_WS()** will skip them and not include them in the result. \
If all input strings are **NULL**, the function returns **NULL**.

### Syntax:
```sql
    CONCAT_WS(separator, string1, string2, ...);
    CONCAT_WS(separator, column_name1, column_name2, ...);
```
  
### Example:
```sql
    SELECT CONCAT_WS(', ', 'John', 'Doe', '123 Main St');  -- John, Doe, 123 Main St
    SELECT CONCAT_WS(', ', 'John', NULL, 'Doe', NULL, '123 Main St');  -- John, Doe, 123 Main St
    SELECT CONCAT_WS(', ',  NULL, NULL, NULL);  -- NULL
```


<!-- Numeric function start -->
<h3 id="numericFunctions">2. Numeric Functions:-</h3>


Numeric functions in MySQL are used to perform various operations on numeric data types such as integers, floating-point numbers, and decimal numbers. \
These functions can be used to perform mathematical calculations, manipulate numeric values, and format numeric output. 

<table>
<tbody>
<tr>
    <th>Numeric Functions</th>
    <th>Description</th>
</tr>
<tr>
    <td><a href="#absFunction">ABS( )</a></td>
    <td>Returns the absolute value of a number.</td>
</tr>
<tr>
    <td><a href="#ceilFunction">CEIL( ) / CEILING( )</a></td>
    <td>Rounds a number up to the nearest integer.</td>
</tr>
<tr>
    <td><a href="#floorFunction">FLOOR( )</a></td>
    <td>Rounds a number down to the nearest integer.</td>
</tr>
<tr>
    <td><a href="#roundFunction">ROUND( )</a></td>
    <td>Rounds a number to a specified number of decimal places.</td>
</tr>
<tr>
    <td><a href="#randFunction">RAND( )</a></td>
    <td>Returns a random floating-point value between 0 and 1.</td>
</tr>
<tr>
    <td><a href="#sqrtFunction">SQRT( )</a></td>
    <td>Returns the square root of a number.</td>
</tr>
<tr>
    <td><a href="#powerFunction">POWER()</a></td>
    <td>Raises a number to the power of another number.</td>
</tr>
<tr>
    <td><a href="#formatFunction">FORMAT( )</a></td>
    <td> Formats a number with a specific number of decimal places.</td>
</tr>
<tr>
    <td><a href="#piFunction">PI( )</a></td>
    <td>Return value of PI.</td>
</tr>
</tbody>
</table>


<!-- Function Explaination -- -->
<h3 id="absFunction">(A) ABS( ) Function:</h3>

The **ABS()** function in MySQL is used to return the absolute (non-negative) value of a numeric expression. \
If the input number is **NULL**, the **ABS()** function returns **NULL**. \
If the input number is already positive, the function returns the same number without any change.

### Syntax:
```sql
    ABS(number);
    ABS(column_name);
```
  
### Example:
```sql
    SELECT ABS(-10);  -- 10
    SELECT ABS(0);  -- 0
    SELECT ABS(10);  -- 10

    SELECT ABS(amount) AS absolute_amount
    FROM transactions;
```


<h3 id="ceilFunction">(B) CEIL( ) / CEILING( ) Function:</h3>

The CEIL() or CEILING() function in MySQL is used to round a numeric value up to the nearest integer that is greater than or equal to the input value. \
If the input value is already an integer, the **CEIL() / CEILING()** function returns the same value without rounding. \
For positive numbers, the result of **CEIL()** is always greater than or equal to the input value. \
For negative numbers, the result of **CEIL()** is always greater than or equal to the input value (moving towards zero). 

### Syntax:
```sql
    CEIL(number);
    CEIL(column_name);
```
  
### Example:
```sql
    SELECT CEIL(4.3);   -- Returns 5
    SELECT CEIL(-4.3);  -- Returns -4
    SELECT CEIL(5.7);   -- Returns 6

    SELECT CEIL(price) AS rounded_price
    FROM products;
```


<h3 id="floorFunction">(C) FLOOR( ) Function:</h3>

The **FLOOR()** function in MySQL is used to round a numeric value down to the nearest integer less than or equal to the input value. \
If the input value is **NULL**, the **FLOOR()** function returns **NULL**. 


### Syntax:
```sql
    FLOOR(number);
    FLOOR(column_name);
```
  
### Example:
```sql
    SELECT FLOOR(3.7);   -- Returns 3
    SELECT FLOOR(-2.5);  -- Returns -3
    SELECT FLOOR(5);   -- Returns 5

    SELECT price, FLOOR(price) AS rounded_down_price
    FROM product_prices;
```


<h3 id="roundFunction">(D) ROUND( ) Function:</h3>

The **ROUND()** function in MySQL is used to round a numeric value to a specified number of decimal places. It is commonly used to adjust precision when working with numerical data. \
If the number is **NULL**, the **ROUND()** function returns **NULL**.

### Syntax:
```sql
    ROUND(number);
    ROUND(number, decimals);
```
  
  - **number:** The numeric value to be rounded.
  - **decimals:** The number of decimal places to which the number should be rounded. default value is 0.

### Example:
```sql
    SELECT ROUND(3.14159, 2);   -- 3.14
    SELECT ROUND(3.14159, 0);   -- 3
    SELECT ROUND(3.14159);   -- 3
```

> If decimals is **negative**, the number is rounded to the **left** of the decimal point (e.g., rounding to the nearest ten, hundred, etc.).

  - -1 means rounding to the nearest ten(10).
  - -2 means rounding to the nearest hundred(100).
  - -3 means rounding to the nearest thousand(1000).
  - and so on.

**(i) Rounding to the nearest ten (-1 decimal place):**
```sql
    SELECT ROUND(123.456, -1);  -- 120
    SELECT ROUND(3.14159, -1);  -- 0
```

**(ii) Rounding to the nearest hundred (-2 decimal places):**
```sql
    SELECT ROUND(123.456, -2);  -- 100
```

**(iii) Rounding to the nearest thousand (-3 decimal places):**
```sql
    SELECT ROUND(123.456, -3);  -- 0
```


<h3 id="randFunction">(E) RAND( ) Function:</h3>

The **RAND()** function in MySQL is used to generate a random floating-point number between 0 and 1. It's commonly used to generate random numbers for various purposes, such as creating sample data or randomizing query results. 
### Syntax:
```sql
    RAND();
```

> [!NOTE]
> To generate random integers within a specific range, you can use the **FLOOR()** function along with **RAND()**. 
> ```sql
>     SELECT FLOOR(RAND() * 100) + 1;
> ```


<h3 id="sqrtFunction">(F) SQRT( ) Function:</h3>

The **SQRT()** function in MySQL is used to calculate the square root of a numeric value. It takes a single argument, which is the number for which you want to find the square root, and returns the square root of that number. \
If the input number is negative, the SQRT() function returns NULL. 

### Syntax:
```sql
    SQRT(number);
```

### Example:
```sql
    SELECT SQRT(25);  -- 5
```


<h3 id="powerFunction">(G) POWER() Function:</h3>

Both the base and exponent parameters can be positive or negative numbers.

### Syntax:
```sql
    POWER(base, exponent);
```

  - **base:** The base number to be raised to a power.
  - **exponent:** The exponent to which the base number is raised.

### Example:
```sql
    SELECT POWER(2, 3);  -- 8
```


<h3 id="formatFunction">(H) FORMAT( ) Function:</h3>

The **FORMAT()** function in MySQL is used to format a number with a specific number of decimal places, and to add thousands separators. It is particularly useful for presenting numeric data in a human-readable format, such as currency values or large numbers. \
If the number parameter is **NULL**, the **FORMAT()** function returns **NULL**. \
The formatted result is returned as a string, not as a numeric value.

### Syntax:
```sql
    FORMAT(number, decimals);
```

  - **number:** The numeric value to be formatted.
  - **decimals:** The number of decimal places to include in the formatted result. This parameter is required.

### Example:
```sql
    SELECT FORMAT(1234567.89123, 2);  -- 1,234,567.89
    SELECT FORMAT(1234567.89123, 0);  -- 1,234,568
    SELECT FORMAT(1234567.89123);  -- Error
```


<h3 id="piFunction">(I) PI( ) Function:</h3>

The **PI()** function in MySQL returns the value of the mathematical constant π (pi), which is approximately equal to 3.141592653589793. 

### Syntax:
```sql
    PI();
```

### Example:
```sql
    SELECT PI();  -- 3.141592653589793
```


<!-- Date time function start -->
<h3 id="dateTimeFunctions">3. Date and Time Functions:-</h3>

<table>
<tbody>
<tr>
    <th>Date/Time Functions</th>
    <th>Description</th>
</tr>
<tr>
    <td><a href="#nowFunction">NOW( )</a></td>
    <td>Returns the current date and time.</td>
</tr>
<tr>
    <td><a href="#curDateFunction">CURDATE( )</a></td>
    <td>Returns the current date.</td>
</tr>
<tr>
    <td><a href="#curTimeFunction">CURTIME( )</a></td>
    <td>Returns the current time.</td>
</tr>
<tr>
    <td><a href="#dateFunction">DATE( )</a></td>
    <td>Extracts the date part of a date or datetime expression.</td>
</tr>
<tr>
    <td><a href="#timeFunction">TIME( )</a></td>
    <td>Extracts the time part of a datetime expression.</td>
</tr>
<tr>
    <td><a href="#dateDifferFunction">DATEDIFF( )</a></td>
    <td>Calculates the difference between two dates.</td>
</tr>
<tr>
    <td><a href="#dateAddFunction">DATE_ADD( )</a></td>
    <td>Adds a specified time interval to a date.</td>
</tr>

<tr>
    <td><a href="#dateSubFunction">DATE_SUB( )</a></td>
    <td>Subtracts a specified time interval from a date.</td>
</tr>
<tr>
    <td><a href="#dateFormatFunction">DATE_FORMAT( )</a></td>
    <td>Formats a date or datetime value.</td>
</tr>
</tbody>
</table>

<!-- Function Explaination -- -->
<h3 id="nowFunction">(A) NOW( ) Function:</h3>

The **NOW()** function in MySQL is used to retrieve the current date and time from the server's system clock. It returns a value in the format **'YYYY-MM-DD HH:MM:SS'**, representing the current date and time in the server's time zone.

### Syntax:
```sql
    NOW();
```

### Example:
```sql
    SELECT NOW();  -- 2024-04-28 15:10:47
```


<h3 id="curDateFunction">(B) CURDATE( ) Function:</h3>

The **CURDATE()** function in MySQL is used to retrieve the current date from the system's clock. \
The **CURDATE()** function returns the current date in the format **'YYYY-MM-DD'**.

### Syntax:
```sql
    CURDATE();
```

### Example:
```sql
    SELECT CURDATE();  -- 2024-04-28
```


<h3 id="curTimeFunction">(C) CURTIME( ) Function:</h3>

The **CURTIME()** function in MySQL is used to retrieve the current time in the format **'HH:MM:SS'** or **'HH:MM:SS.SSSSSS'** (hours, minutes, seconds, and microseconds) based on the system time zone set on the MySQL server.

### Syntax:
```sql
    CURTIME();
```

### Example:
```sql
    SELECT CURTIME();  -- 15:19:08
```


<h3 id="dateFunction">(D) DATE( ) Function:</h3>

In MySQL, the **DATE()** function is used to extract the date part (year, month, day) from a given date or datetime expression. \
The returned date value has the same format as a standard date value in MySQL **(YYYY-MM-DD)**. \
If the input date_expression is **NULL**, the **DATE()** function returns **NULL**.

### Syntax:
```sql
    DATE(date_expression);
```

### Example:
```sql
    -- This query returns the date portion of the datetime value '2022-04-26 14:30:00', which is '2022-04-26'.
    SELECT DATE('2022-04-26 14:30:00');  -- 2022-04-26

    SELECT DATE(now());  -- 2024-04-28
```


<h3 id="timeFunction">(E) TIME( ) Function:</h3>

In MySQL, the **TIME()** function is used to extract the time portion of a date or datetime expression.  \
The time portion returned by the **TIME()** function is represented as a time value with the format **'HH:MM:SS' (hours, minutes, seconds)**. \
If the input datetime_expression is **NULL**, the **TIME()** function returns **NULL**. 

### Syntax:
```sql
    TIME(datetime_expression);
```

### Example:
```sql
    -- This query returns the time portion of the datetime value '2024-04-25 13:45:30', which is '13:45:30'.
    SELECT TIME('2024-04-25 13:45:30');  -- 13:45:30

    SELECT TIME(now());  -- 15:38:28
```


<h3 id="dateDifferFunction">(F) DATEDIFF( ) Function:</h3>

The **DATEDIFF()** function in MySQL is used to calculate the difference between two dates. It returns the number of days between two dates, allowing you to easily determine the interval between them. 

### Syntax:
```sql
    DATEDIFF(date1, date2);
```

### Example:
```sql
    SELECT DATEDIFF('2024-04-30', '2024-04-20');  -- Output: 10
```

**Note:** If **date1** is later than **date2**, the result will be positive. If **date1** is earlier than **date2**, the result will be negative. If both dates are the same, the result will be zero. 



<h3 id="dateAddFunction">(G) DATE_ADD( ) Function:</h3>

The **DATE_ADD()** function in MySQL is used to add a specified time interval to a date or datetime value. \
If the original date is a datetime value, the result will also be a datetime value. \
If the original date is a date value (without time), the result will also be a date value.

### Syntax:
```sql
    DATE_ADD(date, INTERVAL value unit);
    DATE_ADD(datetime, INTERVAL value unit);
```

  - **date:** The date or datetime value to which you want to add the interval.
  - **value:** The number of units to add to the date. It can be an integer or an expression that evaluates to an integer.
  - **unit:** The unit of time to add, such as 'YEAR', 'MONTH', 'DAY', 'HOUR', 'MINUTE', 'SECOND', etc.

### Example:
```sql
    -- This query adds 1 day to the date '2022-04-20' and returns the result, which is '2022-04-21'.
    SELECT DATE_ADD('2022-04-20', INTERVAL 1 DAY);

    -- This query subtracts 1 month from the datetime '2022-04-15 10:30:00' and returns '2022-03-15 10:30:00'.
    SELECT DATE_ADD('2022-04-15 10:30:00', INTERVAL -1 MONTH);

    -- This query adds 2 hours to the datetime '2022-04-20 08:00:00' and returns '2022-04-20 10:00:00'.
    SELECT DATE_ADD('2022-04-20 08:00:00', INTERVAL 2 HOUR);
```


<h3 id="dateSubFunction">(H) DATE_SUB( ) Function:</h3>

The **DATE_SUB()** function in MySQL is used to subtract a specified time interval from a given date or datetime expression. It allows you to calculate a new date or datetime value by subtracting a certain number of **years, months, days, hours, minutes,** or **seconds** from an existing date or datetime.

### Syntax:
```sql
    DATE_SUB(date, INTERVAL value unit);
    DATE_SUB(datetime, INTERVAL value unit);
```

  - **date:** The date or datetime value from which the time interval will be subtracted.
  - **value:** The number of units you want to subtract from the date or datetime. It can be an integer or an expression that evaluates to an integer.
  - **unit:** The unit of time to subtract, such as 'YEAR', 'MONTH', 'DAY', 'HOUR', 'MINUTE', 'SECOND', etc.

### Example:
```sql
    -- This query subtracts 7 days from the date '2022-04-25', resulting in the date '2022-04-18'.
    SELECT DATE_SUB('2022-04-25', INTERVAL 7 DAY);

    -- This query subtracts 3 hours from the datetime '2022-04-25 12:00:00', resulting in the datetime '2022-04-25 09:00:00'.
    SELECT DATE_SUB('2022-04-25 12:00:00', INTERVAL 3 HOUR);

    -- You can use negative values for 'value' to add time intervals instead of subtracting them.
    -- This query adds 2 hours to the datetime '2022-04-20 08:00:00' and returns '2022-04-20 10:00:00'.
    SELECT DATE_SUB('2022-04-20 08:00:00', INTERVAL -2 HOUR);
```


<h3 id="dateFormatFunction">(I) DATE_FORMAT( ) Function:</h3>

The **DATE_FORMAT()** function in MySQL is used to format a date or datetime value according to a specified format. It allows you to customize the appearance of date and time values when retrieving them from the database. \
The **DATE_FORMAT()** function returns a string representing the formatted date or datetime value based on the specified format string.

### Syntax:
```sql
    DATE_FORMAT(date, format);
    DATE_FORMAT(datetime, format);
```

  - **format:** The format string specifying how the date or datetime value should be formatted.

### *Format Specifiers:*



Format specifiers are placeholders representing different parts of the date or datetime value.

| Format Specifier | Description                               |
| ---------------- | ----------------------------------------- |
| %Y:              | Year (4 digits)                           |
| %y:              | Year (2 digits)                           |
| %m:              | Month (01-12)                             |
| %d:              | Day of the month (01-31)                  |
| %H:              | Hour (00-23)                              |
| %h:              | Hour (01-12)                              |
| %i:              | Minute (00-59)                            |
| %s:              | Second (00-59)                            |
| %p:              | AM or PM (for 12-hour clock)              |
| %W:              | Weekday name (e.g., Sunday, Monday)       |
| %M:              | Month name (e.g., January, February)      |
| %b:              | Abbreviated month name (e.g., Jan, Feb)   |
| %c:              | Month (1-12)                              |
| %a:              | Abbreviated weekday name (e.g., Sun, Mon) |

### Example:
```sql
    SELECT DATE_FORMAT('2022-04-25', '%d-%m-%y'); -- 25-04-22
    SELECT DATE_FORMAT('2022-04-25', '%d/%M/%Y'); -- 25/April/2022

    SELECT DATE_FORMAT(now(), '%d/%M/%Y'); -- 28/April/2024

    SELECT DATE_FORMAT('2024-04-28 16:38:50', '%d/%m/%Y %h/%i/%s'); -- 28/04/2024 04/38/50
    SELECT DATE_FORMAT('2024-04-28 16:38:50', '%d/%m/%Y %h/%i/%s %p'); -- 28/04/2024 04/38/50 PM
    SELECT DATE_FORMAT('2024-04-28 16:38:50', '%d/%m/%Y'); -- 28/04/2024
    SELECT DATE_FORMAT('2024-04-28 16:38:50', '%h/%i/%s %p'); -- 04/38/50 PM
```



<!-- Aggregate function start -->
<h3 id="aggregateFunctions">4. Aggregate Functions:-</h3>
MySQL's aggregate function is used to perform calculations on multiple values and return the result in a single value like the average of all values, the sum of all values, and maximum & minimum value among certain groups of values. 

### Syntax:
```sql
    SELECT aggregate_function(column_name)
    FROM table_name
    WHERE condition;
```


<table>
<tbody>
<tr>
    <th>Aggregate Functions</th>
    <th>Description</th>
</tr>
<tr>
    <td><a href="#countFunction">COUNT( )</a></td>
    <td>It returns the number of rows, including rows with NULL values in a group.</td>
</tr>
<tr>
    <td><a href="#sumFunction">SUM( )</a></td>
    <td>It returns the total summed values (Non-NULL) in a set.</td>
</tr>
<tr>
    <td><a href="#averageFunction">AVG( )</a></td>
    <td>It returns the average value of an expression.</td>
</tr>
<tr>
    <td><a href="#minFunction">MIN( )</a></td>
    <td>It returns the minimum (lowest) value in a set.</td>
</tr>
<tr>
    <td><a href="#maxFunction">MAX( )</a></td>
    <td>It returns the maximum (highest) value in a set.</td>
</tr>
<tr>
    <td><a href="#groupConcatFunction">GROUP_CONCAT( )</a></td>
    <td>It returns a concatenated string.</td>
</tr>
<tr>
    <td><a href="#firstFunction">FIRST()</a></td>
    <td>It returns the first value of an expression. but it support only within MS Access.</td>
</tr>
<tr>
    <td><a href="#lastFunction">LAST()</a></td>
    <td>It returns the last value of an expression. but it support only within MS Access.</td>
</tr>
</tbody>
</table>


<!-- Function Explaination -- -->
<h3 id="countFunction">(A) COUNT() Function:-</h3>

The **COUNT()** function is an aggregate function used to count the number of rows that match a specified condition within a table. 

This function produces all rows or only some rows of the table based on a specified condition, and its return type is BIGINT. It can work with both numeric and non-numeric data types.

If there are no matching rows, COUNT() returns 0. COUNT(NULL) returns 0.

### Basic Syntax:
```sql
    SELECT COUNT(column_name)
    FROM table_name
    WHERE condition;
```

- **Counting All Rows:**
 
    ```sql
        SELECT COUNT(*) FROM table_name;
    ```
    This will count all rows, regardless of whether any column contains **NULL** values.

- **Counting Rows with a Condition:**
 
    ```sql
        SELECT COUNT(*) FROM table_name WHERE condition;
    ```
    You can use **COUNT()** with a **WHERE** clause to count only the rows that meet specific criteria.

- **Counting Distinct Values:**
 
    ```sql
        SELECT COUNT(DISTINCT column_name) FROM table_name;
    ```
    This will count only the **unique** values in the specified column.

- **Using Aliases with COUNT():**
 
    ```sql
        SELECT COUNT(*) AS alias_name FROM table_name;
    ```

- **Handling NULL Values:** \
 By default, **COUNT(column_name)** counts all rows, including those with **NULL** values in the specified column. To exclude **NULL** values from the count, use **IS NOT NULL** in the WHERE clause.

    ```sql
        SELECT COUNT(column_name) FROM table_name WHERE column_name IS NOT NULL;
    ```

<h3 id="sumFunction">(B) SUM() Function:-</h3>

The **SUM()** function is an aggregate function used to calculate the sum of values in a column or expression. \
 It works with numeric data type only

### Syntax:
```sql
    SUM(column_name)
            OR
    SUM(expression)
            OR
    SELECT SUM(column_name)
    FROM table_name
    WHERE condition;
```

### Example:
```sql
    SELECT SUM(working_hours) AS "Total working hours" FROM employees;  
```

- **Handling NULL Values:** \
If the column contains **NULL** values, the **SUM()** function ignores them and calculates the sum of **non-NULL** values only. If all values in the column are **NULL**, the result of **SUM()** will be **NULL**.


- **Using SUM() with WHERE:** 
    ```sql
        SELECT SUM(column_name) AS alias_name
        FROM table_name
        WHERE condition;
    ```

- **Using SUM() with GROUP BY:** \
You can also use the SUM() function with the GROUP BY clause to calculate the sum of values for each group separately. 

    ```sql
        SELECT product, SUM(revenue) AS total_revenue
        FROM sales
        GROUP BY product;
    ```

<h3 id="averageFunction">(C) AVG() Function:-</h3>

The **AVG()** function in MySQL is used to calculate the average value of a set of numeric values. \
It takes a column name or expression as its argument and returns the average of all non-NULL values in that column. 

### Syntax:
```sql
    AVG(column_name)
            OR
    AVG(expression)
            OR
    SELECT AVG(column_name)
    FROM table_name
    WHERE condition;
```

### Example:
```sql
    SELECT AVG(score) AS average_score
    FROM grades;
```

- **Handling NULL Values:** \
The **AVG()** function ignores **NULL** values in the column when calculating the average. Only **non-NULL** values are considered in the calculation. \
If all values in the column are **NULL**, the **AVG()** function returns **NULL**.

    > [!NOTE]
    > If all values in a column are strings, the AVG() function in MySQL will attempt to convert those strings to numeric values before calculating the average. If the conversion is successful, it will proceed with the calculation.

- **Using AVG() with Grouping:** \
You can also use the **AVG()** function with the **GROUP BY** clause to calculate average values for each group separately. This is useful for calculating averages across different categories or groups in your data. e.g.,

    ```sql
        SELECT product_category, AVG(sales_amount) AS average_sales
        FROM sales
        GROUP BY product_category;
    ```

<h3 id="minFunction">(D) MIN() Function:-</h3>

The **MIN()** function returns the minimum value from a set of values. It is commonly used to find the smallest value in a specified column of a table or within a set of values returned by a query. 

### Syntax:
```sql
    MIN(column_name)
            OR
    MIN(expression)
            OR
    SELECT MIN(column_name)
    FROM table_name
    WHERE condition;
```

### Example:
```sql
    SELECT MIN(price) AS min_price
    FROM products;
```

- **Handling NULL Values:** \
If the specified column or expression contains **NULL** values, the **MIN()** function ignores them and returns the smallest **non-NULL** value. If all values are **NULL**, the function returns **NULL**.

- **MIN() Functions with GROUP BY:** \
You can combine the **MIN()** function with the **GROUP BY** clause to find the minimum value for each group of rows. e.g.,

    ```sql
        SELECT subject, MIN(score) AS min_score
        FROM student_scores
        GROUP BY subject;
    ```

<h3 id="maxFunction">(E) MAX() Function:-</h3>

The **MAX()** function in MySQL is used to find the maximum value in a set of values. It can be applied to various data types such as **numbers, dates, and strings**. When applied to numeric values, **MAX()** returns the largest value. When applied to date or time values, it returns the latest date or time. When applied to strings, it returns the string that comes last in alphabetical order.

### Syntax:
```sql
    MAX(column_name)
            OR
    MAX(expression)
            OR
    SELECT MAX(column_name)
    FROM table_name
    WHERE condition;
```

### Example:
```sql
    SELECT MAX(salary) AS max_salary
    FROM employees;
```

- **Finding the latest date:** 
    ```sql
        SELECT MAX(order_date) AS latest_order_date
        FROM orders;
    ```

- **Finding the last alphabetical string:** 
    ```sql
        SELECT MAX(product_name) AS last_product
        FROM products;
    ```

<h3 id="groupConcatFunction">(F) GROUP_CONCAT() Function:-</h3>

The **GROUP_CONCAT()** function concatenates values from multiple rows into a single string seperated by commas. It's particularly useful when you want to display or retrieve data in a comma-separated list format within groups. 

### Example:

| student_id | subject |
| ---------- | ------- |
| 1          | Math    |
| 1          | Science |
| 2          | English |
| 3          | Math    |
| 3          | History |

students table

```sql
    SELECT student_id, GROUP_CONCAT(subject) AS subjects
    FROM students
    GROUP BY student_id;
 ```

 | student_id | subjects      |
 | ---------- | ------------- |
 | 1          | Math, Science |
 | 2          | English       |
 | 3          | Math, History |

Result


<h3 id="firstFunction">(G) FIRST() Function:-</h3>

The **FIRST()** function is used to return the first value in a sorted group of values. This function is typically used with the **GROUP BY** clause to group rows based on one or more columns and then retrieve the first value within each group.

It's important to note that MySQL doesn't have a built-in FIRST() function, so it's typically emulated using other functions such as MIN() or MAX().

To get the first value of the column, we must have to use the **LIMIT** clause. It is because **FIRST()** function only supports in MS Access.

### Example:
```sql
    SELECT working_date FROM employee LIMIT 1;    
```

<h3 id="lastFunction">(H) LAST() Function:-</h3>

This function returns the last value of the specified column. To get the last value of the column, we must have to use the **ORDER BY** and **LIMIT** clause. It is because the **LAST()** function only supports in **MS Access**.

### Example:
```sql
    SELECT working_hours FROM employee ORDER BY name DESC LIMIT 1;    
```
