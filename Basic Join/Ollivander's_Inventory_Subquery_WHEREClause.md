## Case Study Question

Harry Potter and his friends are at Ollivander's with Ron, finally replacing Charlie's old broken wand.
Hermione decides the best way to choose is by determining the minimum number of gold galleons needed to buy each non-evil wand of high power and age.
Write a query to print the id, age, coins_needed, and power of the wands that Ron's interested in, sorted in order of descending power.
If more than one wand has same power, sort the result in order of descending age.

```sql
SELECT w.id,
        wp.age,
        w.coins_needed,
        w.power
FROM wands w
JOIN wands_property wp ON w.code = wp.code
WHERE is_evil = 0
    AND w.coins_needed IN (SELECT MIN(w1.coins_needed)
                            FROM wands w1
                            JOIN wands_property wp1 ON w1.code = wp1.code
                            
                            -- this filter based on minimum number of gold galleons needed to buy each non-evil wand of high power and age --
                            WHERE w.power = w1.power
                                AND wp.age = wp1.age)
ORDER BY w.power DESC, wp.age DESC ;   
```
