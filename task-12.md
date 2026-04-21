## Task description

> Given table: `transactions(id, user_id, amount, status)` and two queries: `SELECT * FROM transactions WHERE status = 'FAILED';` and `SELECT * FROM transactions WHERE user_id IN (SELECT user_id FROM transactions WHERE status = 'FAILED')`, Are the outputs the same from the two queries or not?

```sql
-- no the first query gets only the failed transactions
-- but the second query get all transactions for users that have at least one failed transaction
```
