## Case Study Question

Write a query to print the contest_id, hacker_id, name, and the sums of total_submissions, total_accepted_submissions, total_views, and total_unique_views for each contest sorted by contest_id. Exclude the contest from the result if all four sums are .
Note: A specific contest can be used to screen candidates at more than one college, but each college only holds  screening contest.

```sql
SELECT ct.contest_id,
        ct.hacker_id,
        ct.name,
        SUM(ss.total_submissions),
        SUM(ss.total_accepted_submissions),
        SUM(vs.total_views),
        SUM(vs.total_unique_views)
FROM contests ct
JOIN colleges cl ON ct.contest_id = cl.contest_id
JOIN challenges ch ON cl.college_id = ch.college_id

-- subquery to get total sums for the Submission stats.
-- these subqueries use left joins, so that the unrelated/empty information is not joined.
-- join table challenge with submissions

LEFT JOIN (SELECT s.challenge_id,
                    SUM(s.total_submissions)as total_submissions,
                    SUM(s.total_accepted_submissions)as total_accepted_submissions
          FROM submission_stats s
          GROUP BY s.challenge_id)ss ON ch.challenge_id = ss.challenge_id
          
-- another subquery to get total sums for Views stats    
-- join table challenge with view_stats

LEFT JOIN (SELECT v.challenge_id,
                   SUM(v.total_views)as total_views,
                    SUM(v.total_unique_views)as total_unique_views
           FROM view_stats v
           GROUP BY v.challenge_id)vs ON ch.challenge_id = vs.challenge_id    
GROUP BY ct.contest_id,ct.hacker_id,ct.name   

-- HAVING works like WHERE, except over aggregations, which is what we want here.
HAVING SUM(ss.total_submissions)+
        SUM(ss.total_accepted_submissions)+
        SUM(vs.total_views)+
        SUM(vs.total_unique_views) > 0
ORDER BY ct.contest_id;
```
