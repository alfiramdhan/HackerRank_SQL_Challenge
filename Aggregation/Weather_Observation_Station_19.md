## Case Study Question

Consider P1(a,c) and P2(b,d) to be two points on a 2D plane where (a,b) are the respective minimum and maximum values of Northern Latitude (LAT_N)
and (c,d) are the respective minimum and maximum values of Western Longitude (LONG_W) in STATION.
Query the Euclidean Distance between points P1 and P2 and format your answer to display  decimal digits.

The Euclidean Distance : P1(a,c) and P2(b,d)={\sqrt {(a-c)^{2}+(b-d)^{2}}}.}

- P1(Min.LAT_N, Max.LAT_N) a,b
- P2(Min.LONG_W, Max.LONG_W) c,d

```sql
SELECT ROUND(SQRT(POWER(Min(LAT_N) - Max(LAT_N), 2) + POWER(Min(LONG_W)- Max(LONG_W), 2)),4)
FROM STATION
```
