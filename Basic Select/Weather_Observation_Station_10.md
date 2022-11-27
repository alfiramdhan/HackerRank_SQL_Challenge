## Case Study Questions

Query the list of CITY names from STATION that do not end with vowels. Your result cannot contain duplicates.

````sql
SELECT DISTINCT CITY
FROM STATION
WHERE lower(CITY) NOT LIKE '%a'
    AND lower(CITY) NOT LIKE '%i'
    AND lower(CITY) NOT LIKE '%u'
    AND lower(CITY) NOT LIKE '%e'
    AND lower(CITY) NOT LIKE '%o';
````
