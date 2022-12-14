## Case Study Question

Write a query to print the respective hacker_id and name of hackers who achieved full scores for more than one challenge.
Order your output in descending order by the total number of challenges in which the hacker earned a full score.
If more than one hacker received full scores in same number of challenges, then sort them by ascending hacker_id.

```sql
SELECT s.hacker_id,
       h.name
    FROM submissions s
        JOIN challenges ch ON s.challenge_id = ch.challenge_id
        JOIN difficulty d ON ch.difficulty_level = d.difficulty_level
        JOIN hackers h ON s.hacker_id = h.hacker_id
    WHERE s.score = d.score
    GROUP BY s.hacker_id, h.name
    HAVING COUNT(S.hacker_id) > 1
    ORDER BY COUNT(S.hacker_id) DESC, S.hacker_id ASC;
```
