5.63 - Filtering data



Basic Queries

SELECT <column_name>  FROM <tablename> WHERE <condition>

E.g

SELECT birth_date FROM employees WHERE gender = 'F' LIMIT 5;
Or
SELECT * FROM employees WHERE gender = 'F' LIMIT 5;

Adding multiple conditions 



The AND Keyword

SELECT <columnname> FROM table  WHERE <condition> AND <othercondition> (you can keep chaining these ands)
E.g 
SELECT first_name, hire_date FROM employees WHERE gender = 'F' AND last_name = 'Facello';

The OR Keyword

SELECT <columnname> FROM table  WHERE <condition> AND <othercondition> OR <certaincondition>
E.g 
SELECT first_name, hire_date FROM employees WHERE gender = 'F' AND last_name = 'Facello' OR first_name = 'Georgi';
SELECT first_name, hire_date FROM employees WHERE gender = 'F' AND last_name = 'Facello' OR first_name = 'Georgi' AND last_name = 'Simmel';



Excluding data

The NOT keyword

SELECT <columnname> FROM <tablename> WHERE NOT <certaincondition>
E.g 
SELECT first_name FROM employees WHERE NOT gender = 'F';
SELECT first_name FROM employees WHERE NOT hire_date > '1986-06-26' ;
SELECT COUNT(age) FROM customers WHERE NOT age = 55;

Filtering Ranges

Comparison Operators

>

< =

<

> =

! =





SELECT <columnname> FROM <tablename> WHERE NOT <certaincondition>
SELECT first_name, last_name FROM customers WHERE age > 44 AND income > = 100000;
SELECT first_name, last_name FROM customers WHERE age > = 44 OR age < = 50 AND income < = 50000;

another way of checking ranges

SELECT <columname> FROM <tablename> WHERE <columnnamecriteria> BETWEEN X and Y 
SELECT firstname FROM customers WHERE age BETWEEN 55 AND 60



Operator Precedence

With multiple operators there's a priority in applying them 

If the operators have equal precedence then the operators are evaluated directionally from left to right or right to left

Where there are () this clause is applied first

Checking for Empty values

NULL - empty/missing it is not zero or a space

It's worth thinking about what you allow to be nullable.

NULL = NULL is NULL not TRUE or FALSE



The IS Keyword - How do we use null? 

Is the data optional or required. Say you dont need it for sign up but you might need it later.

Always check for nulls when necessary

Whatever operation you run on NULL it will be null

e.g if you NOT ! = NULL you'll get this is where is keyword is helpful

SELECT name, lastname from customers where lastname IS NOT NULL;
SELECT name, lastname from customers where lastname = '' IS TRUE;

Replace NULL values

Use coalesce() 

it returns the first null value in the list



SELECT coalesce(<columnname>(you can check against multiple columns), "defaultvalueyouwanttouse") AS column_alias FROM <tablename>

The  IN keyword

Can be used to return ranges of data or check if there's data in a specific list check example 2

SELECT firstname,lastname FROM customers WHERE age IN (55, 65) LIMIT 5;
SELECT * FROM employees WHERE emp_no IN (100001, 100006, 110008);



Date/TimeZones

Check the setting for the current postgres session.

show timezone;
or
SELECT current_setting('TIMEZONE')

2. Temporarily set the timezone for the session

set timezone 'utc'

3. Permanently set a time zone

ALTER USER <nameofsudouser> SET timezone='UTC'

MANIPULATING DATES

Use ISO-8601 standard

YYYY-MM-DDTHH:MM:SS

2017-08-17T12:47:16+02:00 - the timezone is optional



Timestamps 





