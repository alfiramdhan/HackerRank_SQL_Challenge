## Case Study Question

Given the table schemas below, write a query to print :
  1. the company_code,
  2. founder name,
  3. total number of lead managers,
  4. total number of senior managers,
  5. total number of managers,
  6. and total number of employees.

Order your output by ascending company_code.

- Note:
1. The tables may contain duplicate records.
2. The company_code is string, so the sorting should not be numeric.
3. For example, if the company_codes are C_1, C_2, and C_10, then the ascending company_codes will be C_1, C_10, and C_2.

```sql
SELECT c.company_code,
        c.founder,
        COUNT(DISTINCT lm.lead_manager_code),
        COUNT(DISTINCT sm.senior_manager_code),
        COUNT(DISTINCT m.manager_code),
        COUNT(DISTINCT e.employee_code)
FROM company c, lead_manager lm, senior_manager sm, manager m, employee e
WHERE c.company_code = lm.company_code
    AND lm.lead_manager_code = sm.lead_manager_code
    AND sm.senior_manager_code = m.senior_manager_code
    AND m.manager_code = e.manager_code
GROUP BY c.company_code, c.founder   
ORDER BY c.company_code ASC;
```
