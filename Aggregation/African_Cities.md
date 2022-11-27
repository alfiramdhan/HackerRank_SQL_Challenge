## Case Study Question

Given the CITY and COUNTRY tables, query the names of all cities where the CONTINENT is 'Africa'.
Note: CITY.CountryCode and COUNTRY.Code are matching key columns.

```sql
SELECT C.NAME
FROM CITY C, COUNTRY CT
WHERE C.CountryCode = CT.Code
    AND CT.CONTINENT = 'Africa'
```
