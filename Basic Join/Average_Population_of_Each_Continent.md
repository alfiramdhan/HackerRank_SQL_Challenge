## Case Study Question

Given the CITY and COUNTRY tables, query the names of all the continents (COUNTRY.Continent) and their respective average city populations (CITY.Population) rounded down to the nearest integer.
Note: CITY.CountryCode and COUNTRY.Code are matching key columns.

```sql
SELECT ct.continent,
        FLOOR(AVG(population))
FROM city c, country ct
WHERE c.CountryCode = ct.Code
```
