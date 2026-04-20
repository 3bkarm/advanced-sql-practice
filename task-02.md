## Task description

> Given a table: `sales(id, product_id, sale_date, amount)`, You need for each product to get the latest sale and the previous sale amount, Output: `product_id | latest_sale_date | latest_amount | previous_amount`, You must use window functions.

```sql
SELECT DISTINCT ON (product_id)
    product_id,
    sale_date AS latest_sale_date,
    amount AS latest_amount,
    LAG(amount) OVER (
        PARTITION BY product_id 
        ORDER BY sale_date ASC
    ) AS previous_amount
FROM sales
ORDER BY product_id, sale_date DESC;
```
