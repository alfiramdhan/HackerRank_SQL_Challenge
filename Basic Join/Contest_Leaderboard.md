## Case Study Question

The total score of a hacker is the sum of their maximum scores for all of the challenges.
Write a query to print the hacker_id, name, and total score of the hackers ordered by the descending score.
If more than one hacker achieved the same total score, then sort the result by ascending hacker_id.
Exclude all hackers with a total score of  from your result.

```sql
SELECT h.hacker_id,
        h.name,
        SUM(t1.max_score) as total_score
FROM hackers h
JOIN (SELECT s.hacker_id,
            MAX(s.score)as max_score
        FROM submissions s
        GROUP BY s.challenge_id, s.hacker_id
        HAVING max_score > 0)as t1
        ON h.hacker_id = t1.hacker_id
GROUP BY h.hacker_id, h.name
ORDER BY total_score DESC, h.hacker_id ASC;
```
