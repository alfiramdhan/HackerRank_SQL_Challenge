## Case Study Question

Given the CITY and COUNTRY tables, query the sum of the populations of all cities where the CONTINENT is 'Asia'.
Note: CITY.CountryCode and COUNTRY.Code are matching key columns.

```sql
SELECT SUM(C.POPULATION)
FROM CITY C, COUNTRY CT
WHERE C.CountryCode = CT.Code
 AND CT.CONTINENT = 'Asia'
```
