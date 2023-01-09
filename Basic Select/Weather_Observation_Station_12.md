## Case Study Questions

Query the list of CITY names from STATION that do not start with vowels and do not end with vowels. Your result cannot contain duplicates.

```sql
SELECT DISTINCT CITY
FROM STATION
WHERE (UPPER(CITY) NOT LIKE 'a%'
    AND UPPER(CITY) NOT LIKE 'i%'
    AND UPPER(CITY) NOT LIKE 'u%'
    AND UPPER(CITY) NOT LIKE 'e%'
    AND UPPER(CITY) NOT LIKE 'o%') AND (lower(CITY) NOT LIKE '%a'
                                        AND lower(CITY) NOT LIKE '%i'
                                        AND lower(CITY) NOT LIKE '%u'
                                        AND lower(CITY) NOT LIKE '%e'
                                        AND lower(CITY) NOT LIKE '%o');
```

using MS SQL Server
```sql
select distinct city
from station
where upper(city) not like '[aiueo]%'
    and lower(city) not like '%[aiueo]'
```
