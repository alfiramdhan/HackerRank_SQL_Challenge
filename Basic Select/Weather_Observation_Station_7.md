## Case Study Question

Query the list of CITY names ending with vowels (a, e, i, o, u) from STATION. Your result cannot contain duplicates.

```sql
SELECT DISTINCT CITY
FROM STATION
WHERE lower(CITY) LIKE '%a'
 OR lower(CITY) LIKE '%i'
 OR lower(CITY) LIKE '%u'
 OR lower(CITY) LIKE '%e'
 OR lower(CITY) LIKE '%o'
```

using MS SQL Server
```sql
select distinct city
from station
where lower(city) like '%[aiueo]'
```
