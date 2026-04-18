## Task description

> Given tables: `users(id, name) orders(id, user_id) payments(id, order_id, amount)`, Write a query to get for each user: total number of orders and total amount paid.

```sql
WITH order_counts AS (
    SELECT user_id, COUNT(*) AS total_orders
    FROM orders
    GROUP BY user_id
), payment_sums AS (
    SELECT ord.user_id, SUM(pay.amount) AS total_amount
    FROM orders AS ord
    JOIN payments AS pay 
        ON ord.id = pay.order_id
    GROUP BY ord.user_id
)
SELECT u.id,
    COALESCE(o.total_orders, 0),
    COALESCE(p.total_amount, 0)
FROM users AS u
LEFT JOIN order_counts AS o ON u.id = o.user_id
LEFT JOIN payment_sums AS p ON u.id = p.user_id;
```
