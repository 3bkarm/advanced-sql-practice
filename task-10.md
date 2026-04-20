## Task description

> Given table: `transactions(id, user_id, amount)` and a query: `SELECT * FROM transactions WHERE user_id IN (SELECT user_id FROM transactions GROUP BY user_id HAVING SUM(amount) > 1000);`, Rewrite it in a better way and suggest indexes.

```sql
CREATE INDEX my_index ON transactions(user_id, amount);

WITH filtered AS (
    SELECT user_id
    FROM transactions
    GROUP BY user_id
    HAVING SUM(amount) > 1000
)
SELECT t.*
FROM transactions AS t
JOIN filtered AS f 
  ON t.user_id = f.user_id;
```
