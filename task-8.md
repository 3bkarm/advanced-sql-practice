## Task description

> Given table `transactions(id, user_id, amount, created_at)`, Find for each user the first transaction where cumulative sum exceeds 500 (You may ignore those who didn't exceed the 500 limit).

```sql
WITH t AS (
    SELECT user_id, id, created_at,
    	SUM(amount) OVER(PARTITION BY user_id ORDER BY created_at) AS sm
    FROM transactions
), targ AS (
    SELECT *,
        ROW_NUMBER() OVER(PARTITION BY user_id ORDER BY created_at) AS rnk
    FROM t
    WHERE sm > 500
)
SELECT user_id, id
FROM targ
WHERE rnk = 1;
```
