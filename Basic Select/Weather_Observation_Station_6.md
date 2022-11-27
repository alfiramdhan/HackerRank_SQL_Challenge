## Case Study Question

Query the list of CITY names starting with vowels (i.e., a, e, i, o, or u) from STATION. Your result cannot contain duplicates.

```sql
-- using mySQL :

SELECT DISTINCT CITY
FROM STATION
WHERE upper(city) LIKE 'a%'
    OR upper(city) LIKE 'i%'
     OR upper(city) LIKE 'u%'
     OR upper(city) LIKE 'e%'
     OR upper(city) LIKE 'o%'
```     
or shortcut     

```sql
-- using MS SQL Server :

SELECT CITY
FROM STATION
WHERE CITY LIKE '[aiueo]%'
```
