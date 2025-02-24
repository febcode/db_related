# What are SQL Joins?
Answer:
- SQL Joins are used to combine data from multiple tables based on a related column.

|Join Type	|Description|
|------------|----------|
|INNER JOIN|	Returns matching rows from both tables|
|LEFT JOIN	|Returns all rows from the left table + matching rows from the right|
|RIGHT JOIN	|Returns all rows from the right table + matching rows from the left|
|FULL JOIN	|Returns all rows from both tables (matches where possible)|
Example Query:
```
SELECT employees.name, departments.dept_name
FROM employees
INNER JOIN departments ON employees.dept_id = departments.dept_id;
```
