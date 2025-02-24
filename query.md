# 1. Find the Nth Highest Salary
Problem:
- Write an SQL query to find the N-th highest salary from the Employee table.
- Solution (Using LIMIT & OFFSET in PostgreSQL/MySQL):
```
SELECT DISTINCT salary FROM Employee
ORDER BY salary DESC
LIMIT 1 OFFSET (N-1);
```
Alternative (Using Subquery for Top N Filtering):
```
SELECT salary FROM Employee e1
WHERE N-1 = (SELECT COUNT(DISTINCT salary) FROM Employee e2 WHERE e2.salary > e1.salary);
```
# 2. Detect Duplicate Records
Problem:
- Find employees who have the same name and salary.

Solution:
```
SELECT name, salary, COUNT(*)
FROM Employee
GROUP BY name, salary
HAVING COUNT(*) > 1;
```

# 3. Find Customers Who Have Ordered Products But Never Paid
Problem:
- Identify customers who placed orders but never made payments.
- Solution (Using LEFT JOIN and NULL Check):
```
SELECT c.customer_id, c.name 
FROM Customers c
LEFT JOIN Orders o ON c.customer_id = o.customer_id
LEFT JOIN Payments p ON o.order_id = p.order_id
WHERE p.payment_id IS NULL;

```

# 4. Optimize a Slow Query
Problem:
- Given a slow query, how would you optimize it?

Solution:
- Check Indexes: Ensure columns in WHERE and JOIN clauses have indexes.
- Use EXPLAIN PLAN: Analyze query execution.
- Partition Large Tables: If working with billions of rows.
- Use Caching: Store frequent results in Redis.
- **Avoid SELECT *: Fetch only required columns.
