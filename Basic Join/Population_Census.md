## Case Study Question

Given the CITY and COUNTRY tables, query the sum of the populations of all cities where the CONTINENT is 'Asia'.
Note: CITY.CountryCode and COUNTRY.Code are matching key columns.

```sql
SELECT SUM(POPULATION)
FROM CITY c, COUNTRY ct
WHERE c.CountryCode = ct.Code
    AND CONTINENT = 'Asia'
```
