---
Title: DBS101 Flipped Class 3
categories: [DBS101, Flipped_Class3]
tags: [DBS101]
---

## Null values in SQL
NULL represents the non-existent values in SQL but it is not the same as empty space in string data types and zero in int data type. Null values can be inserted into a column if it allows null values. Null values must be handled carefully as it affects the query results.  

IS NULL operator is used to test for null values and IS NOT NULL operator is used to test for non-null values.

How NULL values affects the behavior of aggregate function in SQL

Count():
Count() function ignores null values if it is not specified.
Count(*) function will count all the rows, regardless of whether they contain null values.

Sum():
Sum() calculates the total of values in the column and null values are typically ignored in the sum calculation. 
If there are no non-null values, the output will be NULL.

Avg():
It calculates the average of values in the column and it also ignores null values.
If there are no non-null values, the result will be NULL.

Min() and Max():
Min() and Max() functions also ignore the null values.

## SQL Set Operators

It allows you to combine two or more selected statements.

UNION : It is used to combine two or more selected statements into single results, it also removes all the duplicate rows by default and output is sorted. Number of data types and columns should be the same.

        Syntax 
        SELECT column1, column2 FROM table1
        UNION
        SELECT column1, column2 FROM table2;


UNION ALL : it functions similar to UNION but it retains all the rows in the combined statement output including duplicates and is not sorted.

        Syntax 
        SELECT column1, column2 FROM table1
        UNION ALL
        SELECT column1, column2 FROM table2;

INTERSECT : It returns the output of common rows that appears in the selected statements. Nmber of data types and columns should be the same.Output does not have duplicates and is sorted in ascending order by default.

        Syntex
        SELECT column1, column2 FROM table1
        INTERSECT
        SELECT column1, column2 FROM table2;

MINUS : this operator returns all the distinct rows from the first selected statement that are not present in the second one.
             : output does not contain duplicates and is sorted in ascending order by default.

        Syntax
        SELECT column1, column2 FROM table1
        MINUS
        SELECT column1, column2 FROM table2;



## During Flipped class.

It was the third flipped class and we had to discuss SQL set operators, NULL values and how aggregate function works on NULL values. Reading materials were provided in the vle so, we had to read through it and discuss in the home group and lateral on discuss with expert group. 
Since it was the third time for us, flipped class was more effective. 

 




