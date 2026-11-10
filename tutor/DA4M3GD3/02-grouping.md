## 02 - Grouping and Aggregation Exercise

- Trainer: Day 3 02_ExerciseGuide_Grouping_and_Aggregation.docx
- Learners: Day3/Day 3 02_ExerciseGuide_Grouping_and_Aggregation.pdf
- Solution: Solutions/Day 3 02_ExerciseGuide_Grouping_and_Aggregation_SOLUTIONS.pdf

- Three exercises on Northwind: basic aggregates on Orders, GROUP BY CustomerID, then SUM of Quantity * UnitPrice on [Order Details]
- Checks: 830 orders (4 Jul 1996 - 6 May 1998); Employee 1 has 123; 89 customers, SAVEA top with 31; product 38 top value 149984.20
- Ex 2 Task 2 is meant to fail before GROUP BY is added - let learners see the error
- Ex 3 Task 3: HAVING can't use the TotalValue alias - repeat the SUM expression
- Watch: Ex 3 Task 1 expects product 23 first, but there's no ORDER BY, so row order may differ
