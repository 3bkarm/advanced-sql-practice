## Task description

> Given table: `employees(id, name, department_id, salary)`, Write a query to return top 2 highest salaries per department and if many employees have the same salary include all of them, Output: `department_id | name | salary`, You must use a window function.

```sql
SELECT department_id, name, salary FROM ( 
    SELECT *, 
        DENSE_RANK() OVER(PARTITION BY department_id ORDER BY salary DESC) AS rnk
    FROM employees
)
WHERE rnk <= 2;
```
