**Query #1**

    -- 1
    SELECT employee_id, employee_name, salary,
    ROW_NUMBER() OVER (ORDER BY salary DESC) AS row_num
    FROM employees;

| employee_id | employee_name | salary  | row_num |
| ----------- | ------------- | ------- | ------- |
| 4           | Diana Prince  | 95000.0 | 1       |
| 3           | Charlie Brown | 90000.0 | 2       |
| 7           | George Miller | 85000.0 | 3       |
| 8           | Hannah Lee    | 82000.0 | 4       |
| 1           | Alice Johnson | 70000.0 | 5       |
| 2           | Bob Smith     | 65000.0 | 6       |
| 5           | Ethan Hunt    | 60000.0 | 7       |
| 6           | Fiona Green   | 58000.0 | 8       |

---
**Query #2**

    -- 2
    SELECT employee_id, employee_name, salary,
    RANK() OVER (ORDER BY salary DESC) AS rank_num
    FROM employees;

| employee_id | employee_name | salary  | rank_num |
| ----------- | ------------- | ------- | -------- |
| 4           | Diana Prince  | 95000.0 | 1        |
| 3           | Charlie Brown | 90000.0 | 2        |
| 7           | George Miller | 85000.0 | 3        |
| 8           | Hannah Lee    | 82000.0 | 4        |
| 1           | Alice Johnson | 70000.0 | 5        |
| 2           | Bob Smith     | 65000.0 | 6        |
| 5           | Ethan Hunt    | 60000.0 | 7        |
| 6           | Fiona Green   | 58000.0 | 8        |

---
**Query #3**

    -- 3
    SELECT employee_id, employee_name, salary,
    DENSE_RANK() OVER (ORDER BY salary DESC) AS rank_by_salary
    FROM employees;

| employee_id | employee_name | salary  | rank_by_salary |
| ----------- | ------------- | ------- | -------------- |
| 4           | Diana Prince  | 95000.0 | 1              |
| 3           | Charlie Brown | 90000.0 | 2              |
| 7           | George Miller | 85000.0 | 3              |
| 8           | Hannah Lee    | 82000.0 | 4              |
| 1           | Alice Johnson | 70000.0 | 5              |
| 2           | Bob Smith     | 65000.0 | 6              |
| 5           | Ethan Hunt    | 60000.0 | 7              |
| 6           | Fiona Green   | 58000.0 | 8              |

---
**Query #4**

    -- 4
    SELECT *
    FROM (
        SELECT employee_id, employee_name, salary,
        ROW_NUMBER() OVER (ORDER BY salary DESC) AS top3_highest_paid
        FROM employees
    ) t
    WHERE top3_highest_paid <= 3;

| employee_id | employee_name | salary  | top3_highest_paid |
| ----------- | ------------- | ------- | ----------------- |
| 4           | Diana Prince  | 95000.0 | 1                 |
| 3           | Charlie Brown | 90000.0 | 2                 |
| 7           | George Miller | 85000.0 | 3                 |

---
**Query #5**

    -- 5
    SELECT employee_id, employee_name, department, salary,
    RANK() OVER (PARTITION BY department ORDER BY salary DESC) AS ranking
    FROM employees;

| employee_id | employee_name | department | salary  | ranking |
| ----------- | ------------- | ---------- | ------- | ------- |
| 7           | George Miller | Finance    | 85000.0 | 1       |
| 8           | Hannah Lee    | Finance    | 82000.0 | 2       |
| 5           | Ethan Hunt    | HR         | 60000.0 | 1       |
| 6           | Fiona Green   | HR         | 58000.0 | 2       |
| 4           | Diana Prince  | IT         | 95000.0 | 1       |
| 3           | Charlie Brown | IT         | 90000.0 | 2       |
| 1           | Alice Johnson | Sales      | 70000.0 | 1       |
| 2           | Bob Smith     | Sales      | 65000.0 | 2       |

---
**Query #6**

    -- 6
    SELECT *
    FROM (
        SELECT department, salary,
        RANK() OVER (PARTITION BY department ORDER BY salary DESC) AS ranking
        FROM employees
    ) t
    WHERE ranking = 1;

| department | salary  | ranking |
| ---------- | ------- | ------- |
| Finance    | 85000.0 | 1       |
| HR         | 60000.0 | 1       |
| IT         | 95000.0 | 1       |
| Sales      | 70000.0 | 1       |

---
**Query #7**

    -- 7
    SELECT order_id, order_date, total_amount,
    SUM(total_amount) OVER (ORDER BY order_id, order_date) AS running_total
    FROM orders;

| order_id | order_date | total_amount | running_total |
| -------- | ---------- | ------------ | ------------- |
| 101      | 2024-01-10 | 500.0        | 500.0         |
| 102      | 2024-01-11 | 700.0        | 1200.0        |
| 103      | 2024-01-15 | 1200.0       | 2400.0        |
| 104      | 2024-01-18 | 300.0        | 2700.0        |
| 105      | 2024-01-20 | 900.0        | 3600.0        |
| 106      | 2024-01-25 | 1500.0       | 5100.0        |
| 107      | 2024-02-01 | 650.0        | 5750.0        |
| 108      | 2024-02-05 | 1100.0       | 6850.0        |
| 109      | 2024-02-10 | 400.0        | 7250.0        |
| 110      | 2024-02-15 | 950.0        | 8200.0        |
| 111      | 2024-02-20 | 2000.0       | 10200.0       |
| 112      | 2024-02-25 | 750.0        | 10950.0       |

---
**Query #8**

    -- 8
    SELECT o.employee_id, e.employee_name, o.order_id, o.total_amount,
    SUM(o.total_amount) OVER (
        PARTITION BY o.employee_id 
        ORDER BY o.order_id, o.order_date
    ) AS cumulative_sales
    FROM orders o
    JOIN employees e 
    ON o.employee_id = e.employee_id;

| employee_id | employee_name | order_id | total_amount | cumulative_sales |
| ----------- | ------------- | -------- | ------------ | ---------------- |
| 1           | Alice Johnson | 101      | 500.0        | 500.0            |
| 1           | Alice Johnson | 103      | 1200.0       | 1700.0           |
| 1           | Alice Johnson | 107      | 650.0        | 2350.0           |
| 1           | Alice Johnson | 111      | 2000.0       | 4350.0           |
| 2           | Bob Smith     | 102      | 700.0        | 700.0            |
| 2           | Bob Smith     | 106      | 1500.0       | 2200.0           |
| 2           | Bob Smith     | 110      | 950.0        | 3150.0           |
| 3           | Charlie Brown | 104      | 300.0        | 300.0            |
| 3           | Charlie Brown | 108      | 1100.0       | 1400.0           |
| 4           | Diana Prince  | 105      | 900.0        | 900.0            |
| 4           | Diana Prince  | 109      | 400.0        | 1300.0           |
| 4           | Diana Prince  | 112      | 750.0        | 2050.0           |

---
**Query #9**

    -- 9
    SELECT o.customer_id, c.customer_name, o.order_id,
    SUM(o.total_amount) OVER (
        PARTITION BY o.customer_id 
        ORDER BY o.order_date, o.order_id
    ) AS total_amount_so_far,
    LAG(o.total_amount) OVER (
        PARTITION BY o.customer_id 
        ORDER BY o.order_date, o.order_id
    ) AS previous_order_amount
    FROM orders o
    JOIN customers c 
    ON o.customer_id = c.customer_id;

| customer_id | customer_name   | order_id | total_amount_so_far | previous_order_amount |
| ----------- | --------------- | -------- | ------------------- | --------------------- |
| 1           | Acme Corp       | 101      | 500.0               |                       |
| 1           | Acme Corp       | 103      | 1700.0              | 500.0                 |
| 1           | Acme Corp       | 108      | 2800.0              | 1200.0                |
| 1           | Acme Corp       | 112      | 3550.0              | 1100.0                |
| 2           | Tech Solutions  | 102      | 700.0               |                       |
| 2           | Tech Solutions  | 107      | 1350.0              | 700.0                 |
| 3           | Global Retail   | 104      | 300.0               |                       |
| 3           | Global Retail   | 109      | 700.0               | 300.0                 |
| 4           | Blue Sky Ltd    | 105      | 900.0               |                       |
| 4           | Blue Sky Ltd    | 110      | 1850.0              | 900.0                 |
| 5           | NextGen Systems | 106      | 1500.0              |                       |
| 5           | NextGen Systems | 111      | 3500.0              | 1500.0                |

---
**Query #10**

    -- 10
    SELECT o.customer_id, c.customer_name, o.order_id,
    SUM(o.total_amount) OVER (
        PARTITION BY o.customer_id 
        ORDER BY o.order_date, o.order_id
    ) AS total_amount_so_far,
    LEAD(o.total_amount) OVER (
        PARTITION BY o.customer_id 
        ORDER BY o.order_date, o.order_id
    ) AS next_order_amount
    FROM orders o
    JOIN customers c 
    ON o.customer_id = c.customer_id;

| customer_id | customer_name   | order_id | total_amount_so_far | next_order_amount |
| ----------- | --------------- | -------- | ------------------- | ----------------- |
| 1           | Acme Corp       | 101      | 500.0               | 1200.0            |
| 1           | Acme Corp       | 103      | 1700.0              | 1100.0            |
| 1           | Acme Corp       | 108      | 2800.0              | 750.0             |
| 1           | Acme Corp       | 112      | 3550.0              |                   |
| 2           | Tech Solutions  | 102      | 700.0               | 650.0             |
| 2           | Tech Solutions  | 107      | 1350.0              |                   |
| 3           | Global Retail   | 104      | 300.0               | 400.0             |
| 3           | Global Retail   | 109      | 700.0               |                   |
| 4           | Blue Sky Ltd    | 105      | 900.0               | 950.0             |
| 4           | Blue Sky Ltd    | 110      | 1850.0              |                   |
| 5           | NextGen Systems | 106      | 1500.0              | 2000.0            |
| 5           | NextGen Systems | 111      | 3500.0              |                   |

---

[View on DB Fiddle](https://www.db-fiddle.com/)
