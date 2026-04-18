## Task description

> Given a table: `orders(id, user_id, status, created_at, amount)` and a query: `SELECT user_id, created_at FROM orders WHERE status = 'PAID' ORDER BY created_at DESC LIMIT 10;`, Suggest the best covering index to optimize the query.

```sql
CREATE INDEX my_index ON orders(status, created_at DESC) INCLUDE(user_id);
```
