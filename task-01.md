## Task description

> Given table: `transactions(id, user_id, amount, status)` and a bad query: `SELECT * FROM transactions WHERE user_id IN ( SELECT user_id FROM transactions WHERE status = 'FAILED');`, Your tasks is to rewrite this query in a more efficient way.

```sql
SELECT *
FROM transactions AS t1
WHERE EXISTS (
    SELECT 1
    FROM transactions AS t2
    WHERE t2.user_id = t1.user_id
        AND t2.status = 'FAILED'
);
```
