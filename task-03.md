## Task description

> Given table: `users(id, name) logins(id, user_id, login_date)`, Find users who logged in at least 3 consecutive days, Output: `user_id`.

```sql
WITH t AS (
    SELECT user_id,
        login_date - INTERVAL '1 DAY' * 
        ROW_NUMBER() OVER (PARTITION BY user_id ORDER BY login_date) AS ky
    FROM logins
), grouped AS (
    SELECT user_id, ky, COUNT(*) AS cnt
    FROM t
    GROUP BY user_id, ky
)
SELECT DISTINCT user_id
FROM grouped
WHERE cnt >= 3;
```
