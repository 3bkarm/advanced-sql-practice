## Task description

> Given table: `transactions(id, user_id, amount)`, And query: `SELECT user_id, SUM(amount) FROM transactions GROUP BY user_id ORDER BY SUM(amount) DESC LIMIT 10;`, Can we optimize this query using indexes, and is there is another way if we can't?

```sql
-- No indexes can't help because you need to scan all the records anyway
-- We can create a new table like user_totals(user_id, total_amount) and keep update the data and then we can achieve our query like this:
SELECT *
FROM user_totals
ORDER BY total_amount DESC
LIMIT 10;
```
