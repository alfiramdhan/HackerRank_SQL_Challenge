## Case Study Questions

Query the NAME field for all American cities in the CITY table with populations larger than 120000. The CountryCode for America is USA.

````sql
SELECT *
FROM CITY
WHERE POPULATION > 100000
    AND COUNTRYCODE = 'USA';
````
