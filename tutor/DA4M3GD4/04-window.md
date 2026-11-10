## 04 - Window Functions (Stretch and Challenge)

- Trainer: Day 4 04_Window Functions.pptx (21 slides)
- Learners: Day4/Day 4 01_Window Functions.pdf (numbered 01 in the zip, 04 in the trainer file)

- Start from a problem GROUP BY can't solve: each employee next to their department's average salary
- OVER() for the whole table, then PARTITION BY for groups; ROWS BETWEEN for running and moving totals
- Ranking (RANK, DENSE_RANK, ROW_NUMBER, NTILE) and positional (LAG, LEAD, FIRST_VALUE) - run them from `Data files/Day 4 01_Window Functions_examples code.sql`
- Needs `Data files/DeptEmployees.csv` imported and `Data files/CreateRevenue.sql` run - demo rather than have everyone set up
- Watch: slides 7-8 write `Employee Name` with a space - it's EmployeeName
