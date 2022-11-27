## Case Study Question

Write a query to print the hacker_id, name, and the total number of challenges created by each student.
Sort your results by the total number of challenges in descending order. If more than one student created the same number of challenges, then sort the result by hacker_id.
If more than one student created the same number of challenges and the count is less than the maximum number of challenges created,
then exclude those students from the result.

1. Use HAVING instead of WHERE since we have to filter on groups
2. Split the total number of counts into 2 pieces
3. First piece will be the largest number 
4. Second piece will be the number which doesn't repeat (Unique) or is available once
5. SELECT statement pada subquery HAVING should contains 1 column

```sql
SELECT h.hacker_id, h.name, count(ch.challenge_id) as number_challenge
FROM hackers h
JOIN challenges ch ON h.hacker_id = ch.hacker_id
GROUP BY h.hacker_id, h.name
HAVING number_challenge = (
                            SELECT COUNT(temp1.challenge_id)as max_number
                                   FROM challenges temp1
                                    GROUP BY temp1.hacker_id
                                    ORDER BY max_number DESC
                                    LIMIT 1)
    OR number_challenge IN (
                        SELECT DISTINCT total_unique
                        FROM (SELECT h1.hacker_id, h1.name, count(ch1.challenge_id) total_unique
                                FROM hackers h1
                                JOIN challenges ch1 ON h1.hacker_id = ch1.hacker_id
                                GROUP BY h1.hacker_id, h1.name)temp2
                        GROUP BY total_unique
                        HAVING count(total_unique) =1 )
ORDER BY number_challenge DESC, h.hacker_id;
```
