## 04 - Advanced Grouping Exercise

- Trainer: Day 3 04_ExerciseGuide_Advanced_Aggregation.docx
- Learners: Day3/Day 3 04_ExerciseGuide_Advanced_Aggregation.pdf
- Solution: Solutions/Day 3 04_ExerciseGuide_Advanced_Aggregation_SOLUTIONS.pdf

- New database: learners run `Data files/QATSQLPLUS Setup.sql` first - check everyone has it before starting
- Queries the VendorCourseDateDelegateCount view: SUM(NumberDelegates) by VendorName, CourseName, StartDate
- Checks: 9 rows grouped; 20 with ROLLUP; 52 with CUBE; 12 with GROUPING SETS
- Column order in GROUP BY matters for ROLLUP - wrong order is the usual reason for not getting 20
- Watch: the overview says Task 2 subtotals VendorName and CourseName, but Task 2 itself asks for Vendor only (12 rows) - follow the task
