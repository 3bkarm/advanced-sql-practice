## Task description

> Given table: `orders(id, user_id, amount, created_at)`, Find for each user their top 2 highest orders (by amount) but only include users whose total order amount > 1000.

```sql
WITH t AS (
    SELECT user_id
    FROM orders
    GROUP BY user_id
    HAVING SUM(amount) > 1000
), targ AS (
    SELECT t.user_id, ord.id AS order_id,
        ROW_NUMBER() OVER(PARTITION BY t.user_id ORDER BY ord.amount DESC) AS rnk
    FROM t JOIN orders AS ord
        ON t.user_id = ord.user_id
)
SELECT user_id, order_id
FROM targ
WHERE rnk <= 2;
```
