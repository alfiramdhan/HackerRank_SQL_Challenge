## Case Study Question

Given the CITY and COUNTRY tables, query the names of all cities where the CONTINENT is 'Africa'.
Note: CITY.CountryCode and COUNTRY.Code are matching key columns.

```sql
SELECT c.Name
FROM CITY c, COUNTRY ct
WHERE c.CountryCode = ct.Code
    AND CONTINENT = 'Africa'
```
