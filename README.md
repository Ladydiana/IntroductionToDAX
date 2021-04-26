# INTRODUCTION TO DAX


Based on SQLBI's Introducing DAX Video Course.


## The DAX Language 
DAX is a functional language, the execution flows with function calls.

- Language of: 
  - Power Pivot
  - Power BI
  - SSAS Tabular

- Important differences:
  - No concept of «row» and «column»
  - Different type system
- Many new functions
- Designed for data models and business calculations

**!** Code formatting is important in DAX, as it makes code debugging easy.
For automatically formatting DAX code one can use [daxformatter](www.daxformatter.com).

## Calculated Columns
- Columns computed using DAX.
- Always computed for the current row.

## Measures
- Written using DAX
- Do not work row by row
- Instead, use tables and aggregators
- Do not have the «current row» concept

## Naming Conventions
- Measures do not belong to a table => Avoid table name in referencing measures. 
This way it is easier to move to another table and identify as a measure.
- So:
  - Calculated columns -> Table[Column]
  - Measures -> [Measure]

## Measures vs Calculated Columns
- Use a column when: 
  - Needing to slice or filter on the value
- Use a measure when:
  - Calculating percentages or ratios
  - Needing complex aggregations
- Space and CPU usage: 
  - Columns consume memory
  - Measures consume CPU
  
## Aggregation Functions
- Work only on numeric columns.
- Aggregate only one column.
```
 SUM
 AVERAGE
 MIN
 MAX
```

## The «X» Aggregation Functions
- Iterators: useful to aggregate formulas
```
 SUMX
 AVERAGEX
 MINX
 MAXX
```
- Iterate over the table and evaluate the expression for
each row
- Always receive two parameters:
  1. Table to iterate
  2. Formula to evaluate for each row
- Example:
```
SUMX (
	Sales,
	Sales[Price] * Sales[Quantity]
)
```

## Using Variables
- Very useful to avoid repeating subexpressions in your code.
- Example: 
```
Quantity = 
VAR TotalQuantity = SUM ( Sales[Quantity] )
RETURN
	IF (
		TotalQuantity > 1000,
		TotalQuantity * 0.95,
		TotalQuantity * 1.25
	)
```

## Date Functions
```
DATE, DATEVALUE, DAY, EDATE,
EOMONTH, HOUR, MINUTE,
MONTH, NOW, SECOND, TIME,
TIMEVALUE, TODAY, WEEKDAY,
WEEKNUM, YEAR, YEARFRAC
```

## Table Functions
- Basic functions that work on full tables and return a table as a result
```
FILTER
ALL
VALUES
DISTINCT
RELATEDTABLE
```
- Their result is often used in other functions
- They can be combined together to form complex expressions