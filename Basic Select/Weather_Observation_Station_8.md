## Case Study Question

Query the list of CITY names from STATION which have vowels (i.e., a, e, i, o, and u) as both their first and last characters.
Your result cannot contain duplicates.

```sql
SELECT DISTINCT CITY
FROM STATION
WHERE (UPPER(CITY) LIKE 'a%'
    OR UPPER(CITY) LIKE 'i%'
    OR UPPER(CITY) LIKE 'u%'
    OR UPPER(CITY) LIKE 'e%'
    OR UPPER(CITY) LIKE 'o%') AND (lower(CITY) LIKE '%a'
                                    OR lower(CITY) LIKE '%i'
                                    OR lower(CITY) LIKE '%u'
                                    OR lower(CITY) LIKE '%e'
                                    OR lower(CITY) LIKE '%o');
```

using MS SQL Server
```sql
select distinct city
from station
where upper(city) like '[aiueo]%'
    and lower(city) like '%[aiueo]'
