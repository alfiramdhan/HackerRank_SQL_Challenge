## Case Study Question

A median is defined as a number separating the higher half of a data set from the lower half.
Query the median of the Northern Latitudes (LAT_N) from STATION and round your answer to 4 decimal places.

```sql
SELECT ROUND(LAT_N,4)
FROM STATION st
WHERE (SELECT COUNT(LAT_N)
        FROM STATION s1
        WHERE s1.LAT_N < st.LAN_T) = (SELECT COUNT(LAT_N)
                                      FROM STATION s2
                                      WHERE s2.LAT_N > st.LAN_T);
```
