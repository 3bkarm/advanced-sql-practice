## Task description

> Table: `logs(id, level, message, created_at)` and a query: `SELECT * FROM logs WHERE level = 'ERROR' AND created_at >= NOW() - INTERVAL '1 day' ORDER BY created_at DESC LIMIT 20;`, Suggest the best index to optimize this query.

```sql
CREATE INDEX my_index ON logs(created_at DESC) WHERE level = 'ERROR';
```
