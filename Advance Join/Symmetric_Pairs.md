## Case Study Question

You are given a table, Functions, containing two columns: X and Y.
Two pairs (X1, Y1) and (X2, Y2) are said to be symmetric pairs if X1 = Y2 and X2 = Y1.
Write a query to output all such symmetric pairs in ascending order by the value of X. List the rows such that X1 ≤ Y1.

- NOTE: 
Lets divide the output in 2 parts: 

a. X=Y  
for the (a) X=Y, We should check whether the entry (X,Y) WHERE X=Y is present in the table twice.
If it is present 2 times then we can say the symmetric pair is present and add it in the output. 

b. X<Y
for the (b) X<Y, We should check whether the entries are present in the table where X1=Y2 and X2=Y1. 


SOLUTION :
```sql
SELECT f1.X, f1.Y
FROM Functions f1, Functions f2
WHERE f1.X <= f1.Y
AND f1.X = f2.Y
AND f2.X = f1.Y
GROUP BY f1.X, f1.Y
HAVING count(CASE WHEN f1.X=f1.Y THEN f1.X END)>2
OR count(CASE WHEN f1.X<f1.Y THEN f1.X END)=1
ORDER BY f1.X, f1.Y;
```

We have checked the count for X=Y should be >2 (instead of =2), It's because, due to the usage of CROSS-JOIN there, if the count for a pair (X1,Y1) is 2 in the original table, after the CROSS-JOIN the count will become 4. original count = 3 will become 6 after CROSS-JOIN and so on... 
So, checking the count > 2, will be correct major to check if duplicate entry is present in the original table.
