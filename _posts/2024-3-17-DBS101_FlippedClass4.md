---
Title: DBS101 Flipped Class 4
categories: [DBS101, Flipped_Class4]
tags: [DBS101]
---
# Advanced Aggregation Functions

## 1.Ranking
This function returns the rank of the values in the group of values.The rank is equal to one plus the number of rows that come before it but are not on the same level as it.We can use the RANK() window functions along with aggregate functions to assign a rank to each row on the specified criteria.

RANK() does not have parameters as it does not need additional parameters to perform its operation.

The RANK() function aids analysis and drawing reports such as identifying top performers, detecting outliners and generating leaderboards.


## 2.Window 
It is also known as window function and analytic function, which plays vital feature role in SQL that calculates a value for each row on a defined window or subset of the data unlike aggregte function like SUM() and AVG(). The output is calculated for each row and included as an additional column in the result set.

Frequently used window function:
- ROLL_NUMBER(): assigns the roll number to each row within partition.
- DENSE_RANK(): functions similar to RANK() but it does without gaps in the ranking.

Window function offers lots of flexilibilty and power for the data analysis tasks.
## 3.Pivoting
Pivoting is a process of converting data from row-based format to column-based format or  from column-based to row-based formate.

Pivot clause is composed of three parts:
- the values that is being aggregated.
- IN, column that is being replaced.
- FOR, specified values from the column being replaced that will become new column.

PIVOT can't be used with WHERE, GROUP BY or HAVING after the pivot clause.

It also aids summarizing and analysing data in various ways.


## 4.Rollup and Cube
They are the extention to the `GROUP BY` clause. ROLLUP and CUBE are particularly useful for creating hierarchical or multi-dimentional summaries of data. They are useful to uncover trends and patterns in the data that might not be apparent from the single `GROUP BY ` query.


#### ROLL UP
- generates the subtotals for hierarchy of values within the specified columns to grand total.
- produce sum up reports with subtotal rows.

#### CUBE
- It is the mega version of the ROLL UP.
- It generates subtotals of the all the possible combination of the specified columns.
- plays the important role while creating multi-dimentional summaries or pivot tables.


Both ROLL UP and CUBE performs from left to right in the order of the specified columns in the `GROUP BY` clause.

### During Flipped class
During this flipped class , we were assigned to groups of four with students of six and had to discuss the given topics. After long discussion we had to present it to the class. We were provided with reading materials for the topics but we did further research for in depth learning. We also did demo sessions for each topic since practical usage lends a hand more compared to theory classes. Of all the flipped classes, I found this flipped class much more interesting because of the demo session.  