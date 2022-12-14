## Case Study Question

Consider P1(a,b) and P2(c,d) to be two points on a 2D plane.
- a happens to equal the minimum value in Northern Latitude (LAT_N in STATION).
- b happens to equal the minimum value in Western Longitude (LONG_W in STATION).
- c happens to equal the maximum value in Northern Latitude (LAT_N in STATION).
- d happens to equal the maximum value in Western Longitude (LONG_W in STATION).

- Manhattan distance P1(a,b) and P2(c,d) = (a-c) + (b-d)
- P1(Min.LAT_N, Min.LONG_W) a,b
- P2(Max.LAT_N, Max.LONG_W) c,d

Query the Manhattan Distance between points P1 and P2 and round it to a scale of  decimal places.

```sql
SELECT ROUND(ABS((MIN(LAT_N) - MAX(LAT_N)) + (MIN(LONG_W) - MAX(LONG_W))),4)
FROM STATION;
```
