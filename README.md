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
