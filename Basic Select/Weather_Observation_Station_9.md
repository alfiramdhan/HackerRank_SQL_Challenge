## Case Study Question

Query the list of CITY names from STATION that do not start with vowels. Your result cannot contain duplicates.

```sql
SELECT DISTINCT CITY
FROM STATION
WHERE UPPER(CITY) NOT LIKE 'a%'
    AND UPPER(CITY) NOT LIKE 'i%'
    AND UPPER(CITY) NOT LIKE 'u%'
    AND UPPER(CITY) NOT LIKE 'e%'
    AND UPPER(CITY) NOT LIKE 'o%';
```
