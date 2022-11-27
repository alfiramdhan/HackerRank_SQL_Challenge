## Case Study Question

Write a query to output the names of those students whose best friends got offered a higher salary than them.
Names must be ordered by the salary amount offered to the best friends.
It is guaranteed that no two students got same salary offer.

```sql
SELECT s.name
FROM students s
JOIN friends f ON s.ID = f.ID
JOIN packages p ON f.ID = p.ID
JOIN packages fs ON f.friend_ID = fs.ID
WHERE p.salary < fs.salary
ORDER BY fs.salary;
 ```
