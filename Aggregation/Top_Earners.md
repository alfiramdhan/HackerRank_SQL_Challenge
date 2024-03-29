## Case Study Question

We define an employee's total earnings to be their monthly salary x months worked and the maximum total earnings to be the maximum total earnings for any employee in the Employee table.

Write a query to find the maximum total earnings for all employees as well as the total number of employees who have maximum total earnings.
Then print these values as 2 space-separated integers.

```sql
SELECT salary*months as max,
        count(*)as number
FROM employee
GROUP BY max
ORDER BY max desc
LIMIT 1;
```

So we got the maximum earnings value (108064) and a count of the number of employees who have earned 108064 (which is 7) as two space-separated values.
