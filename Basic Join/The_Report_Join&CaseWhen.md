## Case Study Question

You are given two tables: Students and Grades. Students contains three columns ID, Name and Marks.
1. a report containing three columns: Name, Grade and Mark.
2. The report must be in descending order by grade -- i.e. higher grades are entered first
3. If there is more than one student with the same grade (8-10) assigned to them, order those particular students by their name alphabetically
4. if the grade is lower than 8, use "NULL" as their name and list them by their grades in descending order
5. If there is more than one student with the same grade (1-7) assigned to them, order those particular students by their marks in ascending order.

```sql
SELECT 
    CASE WHEN g.grade >= 8 THEN name
         WHEN g.grade < 8 THEN 'NULL'
    END as names,
        g.grade,
        s.marks
FROM students s, grades g
WHERE s.marks between g.min_mark and g.max_mark
ORDER BY g.grade DESC, names ASC
```
