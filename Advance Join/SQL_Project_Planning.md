## Case Study Question

Write a query to output the start and end dates of projects:
- listed by the number of days it took to complete the project in ascending order -> number_diff ASC
- the difference between the End_Date and the Start_Date is equal to 1 day for each row in the table -> number_diff and start_date < end_date
- If there is more than one project that have the same number of completion days, then order by the start date of the project -> start_date ASC

```sql
SELECT s.pro_start, MIN(e.pro_end)
FROM (SELECT start_date as pro_start FROM projects WHERE start_date NOT IN (SELECT end_date FROM projects))as s,
     (SELECT end_date as pro_end FROM projects WHERE end_date NOT IN (SELECT start_date FROM projects))as e
 WHERE s.pro_start < e.pro_end
GROUP BY s.pro_start
 ORDER BY DATEDIFF(MIN(e.pro_end), s.pro_start) ASC, s.pro_start ASC;
```
