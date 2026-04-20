## Task description

> Given a table: `transactions(id, user_id, amount, created_at)`, and a bad query: `SELECT * FROM transactions WHERE DATE(created_at) = '2024-01-01';`, Rewrite this query to be more efficient.

```sql
SELECT * FROM transactions 
WHERE created_at >= '2024-01-01' AND created_at < '2024-01-02';
```
