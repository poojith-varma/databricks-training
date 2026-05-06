Results

**Query #1**

    -- Question 1
    -- Select all columns from the Employee table
    
    SELECT *
    FROM Employee;

| emp_id | name        | age | salary  | department_id | hire_date  |
| ------ | ----------- | --- | ------- | ------------- | ---------- |
| 1      | John Doe    | 28  | 50000.0 | 1             | 2020-01-15 |
| 2      | Jane Smith  | 34  | 60000.0 | 2             | 2019-07-23 |
| 3      | Bob Brown   | 45  | 80000.0 | 1             | 2018-02-12 |
| 4      | Alice Blue  | 25  | 45000.0 | 3             | 2021-03-22 |
| 5      | Charlie P.  | 29  | 50000.0 | 2             | 2019-12-01 |
| 6      | David Green | 38  | 70000.0 | 4             | 2022-05-18 |
| 7      | Eve Black   | 40  | 55000.0 | 3             | 2021-08-30 |
| 8      | Frank White | 32  | 48000.0 |               | 2021-07-10 |
| 9      | Grace Kelly | 27  | 65000.0 | 1             | 2018-11-13 |
| 10     | Hannah Lee  | 30  | 53000.0 | 4             | 2020-02-25 |

---
**Query #2**

    -- Question 2
    -- Select only the name and salary columns from the Employee table
    
    SELECT name, salary
    FROM Employee;

| name        | salary  |
| ----------- | ------- |
| John Doe    | 50000.0 |
| Jane Smith  | 60000.0 |
| Bob Brown   | 80000.0 |
| Alice Blue  | 45000.0 |
| Charlie P.  | 50000.0 |
| David Green | 70000.0 |
| Eve Black   | 55000.0 |
| Frank White | 48000.0 |
| Grace Kelly | 65000.0 |
| Hannah Lee  | 53000.0 |

---
**Query #3**

    -- Question 3
    -- Select employees who are older than 30
    
    SELECT *
    FROM Employee
    WHERE age > 30;

| emp_id | name        | age | salary  | department_id | hire_date  |
| ------ | ----------- | --- | ------- | ------------- | ---------- |
| 2      | Jane Smith  | 34  | 60000.0 | 2             | 2019-07-23 |
| 3      | Bob Brown   | 45  | 80000.0 | 1             | 2018-02-12 |
| 6      | David Green | 38  | 70000.0 | 4             | 2022-05-18 |
| 7      | Eve Black   | 40  | 55000.0 | 3             | 2021-08-30 |
| 8      | Frank White | 32  | 48000.0 |               | 2021-07-10 |

---
**Query #4**

    -- Question 4
    -- Select the names of all departments
    
    SELECT name
    FROM Department;

| name      |
| --------- |
| IT        |
| HR        |
| Finance   |
| Marketing |

---
**Query #5**

    -- Question 5
    -- Select employees who work in the IT department
    
    SELECT e.*
    FROM Employee e
    JOIN Department d
    ON e.department_id = d.department_id
    WHERE d.name = 'IT';

| emp_id | name        | age | salary  | department_id | hire_date  |
| ------ | ----------- | --- | ------- | ------------- | ---------- |
| 1      | John Doe    | 28  | 50000.0 | 1             | 2020-01-15 |
| 3      | Bob Brown   | 45  | 80000.0 | 1             | 2018-02-12 |
| 9      | Grace Kelly | 27  | 65000.0 | 1             | 2018-11-13 |

---
**Query #6**

    -- Question 6
    -- Select employees whose names start with 'J'
    
    SELECT *
    FROM Employee
    WHERE name LIKE 'J%';

| emp_id | name       | age | salary  | department_id | hire_date  |
| ------ | ---------- | --- | ------- | ------------- | ---------- |
| 1      | John Doe   | 28  | 50000.0 | 1             | 2020-01-15 |
| 2      | Jane Smith | 34  | 60000.0 | 2             | 2019-07-23 |

---
**Query #7**

    -- Question 7
    -- Select employees whose names end with 'e'
    
    SELECT *
    FROM Employee
    WHERE name LIKE '%e';

| emp_id | name        | age | salary  | department_id | hire_date  |
| ------ | ----------- | --- | ------- | ------------- | ---------- |
| 1      | John Doe    | 28  | 50000.0 | 1             | 2020-01-15 |
| 4      | Alice Blue  | 25  | 45000.0 | 3             | 2021-03-22 |
| 8      | Frank White | 32  | 48000.0 |               | 2021-07-10 |
| 10     | Hannah Lee  | 30  | 53000.0 | 4             | 2020-02-25 |

---
**Query #8**

    -- Question 8
    -- Select employees whose names contain 'a'
    
    SELECT *
    FROM Employee
    WHERE name LIKE '%a%';

| emp_id | name        | age | salary  | department_id | hire_date  |
| ------ | ----------- | --- | ------- | ------------- | ---------- |
| 2      | Jane Smith  | 34  | 60000.0 | 2             | 2019-07-23 |
| 4      | Alice Blue  | 25  | 45000.0 | 3             | 2021-03-22 |
| 5      | Charlie P.  | 29  | 50000.0 | 2             | 2019-12-01 |
| 6      | David Green | 38  | 70000.0 | 4             | 2022-05-18 |
| 7      | Eve Black   | 40  | 55000.0 | 3             | 2021-08-30 |
| 8      | Frank White | 32  | 48000.0 |               | 2021-07-10 |
| 9      | Grace Kelly | 27  | 65000.0 | 1             | 2018-11-13 |
| 10     | Hannah Lee  | 30  | 53000.0 | 4             | 2020-02-25 |

---
**Query #9**

    -- Question 9
    -- Select employees whose names are exactly 9 characters long
    
    SELECT *
    FROM Employee
    WHERE LENGTH(name) = 9;

| emp_id | name      | age | salary  | department_id | hire_date  |
| ------ | --------- | --- | ------- | ------------- | ---------- |
| 3      | Bob Brown | 45  | 80000.0 | 1             | 2018-02-12 |
| 7      | Eve Black | 40  | 55000.0 | 3             | 2021-08-30 |

---
**Query #10**

    -- Question 10
    -- Select employees whose names have 'o' as the second character
    
    SELECT *
    FROM Employee
    WHERE name LIKE '_o%';

| emp_id | name      | age | salary  | department_id | hire_date  |
| ------ | --------- | --- | ------- | ------------- | ---------- |
| 1      | John Doe  | 28  | 50000.0 | 1             | 2020-01-15 |
| 3      | Bob Brown | 45  | 80000.0 | 1             | 2018-02-12 |


    -- Question 11
    -- Select employees hired after January 1, 2020
    
    SELECT *
    FROM Employee
    WHERE hire_date > '2020-01-01';

| emp_id | name        | age | salary  | department_id | hire_date  |
| ------ | ----------- | --- | ------- | ------------- | ---------- |
| 1      | John Doe    | 28  | 50000.0 | 1             | 2020-01-15 |
| 4      | Alice Blue  | 25  | 45000.0 | 3             | 2021-03-22 |
| 6      | David Green | 38  | 70000.0 | 4             | 2022-05-18 |
| 7      | Eve Black   | 40  | 55000.0 | 3             | 2021-08-30 |
| 8      | Frank White | 32  | 48000.0 |               | 2021-07-10 |
| 10     | Hannah Lee  | 30  | 53000.0 | 4             | 2020-02-25 |

---
**Query #2**

    -- Question 12
    -- Select employees hired before January 1, 2020
    
    SELECT *
    FROM Employee
    WHERE hire_date < '2020-01-01';

| emp_id | name        | age | salary  | department_id | hire_date  |
| ------ | ----------- | --- | ------- | ------------- | ---------- |
| 2      | Jane Smith  | 34  | 60000.0 | 2             | 2019-07-23 |
| 3      | Bob Brown   | 45  | 80000.0 | 1             | 2018-02-12 |
| 5      | Charlie P.  | 29  | 50000.0 | 2             | 2019-12-01 |
| 9      | Grace Kelly | 27  | 65000.0 | 1             | 2018-11-13 |

---
**Query #3**

    -- Question 13
    -- Select employees hired in the year 2021
    
    SELECT *
    FROM Employee
    WHERE YEAR(hire_date) = 2021;

| emp_id | name        | age | salary  | department_id | hire_date  |
| ------ | ----------- | --- | ------- | ------------- | ---------- |
| 4      | Alice Blue  | 25  | 45000.0 | 3             | 2021-03-22 |
| 7      | Eve Black   | 40  | 55000.0 | 3             | 2021-08-30 |
| 8      | Frank White | 32  | 48000.0 |               | 2021-07-10 |

---
**Query #4**

    -- Question 14
    -- Select employees hired in the month of July
    
    SELECT *
    FROM Employee
    WHERE MONTH(hire_date) = 7;

| emp_id | name        | age | salary  | department_id | hire_date  |
| ------ | ----------- | --- | ------- | ------------- | ---------- |
| 2      | Jane Smith  | 34  | 60000.0 | 2             | 2019-07-23 |
| 8      | Frank White | 32  | 48000.0 |               | 2021-07-10 |

---
**Query #5**

    -- Question 15
    -- Display employee names along with year of hiring
    
    SELECT name, YEAR(hire_date) AS hire_year
    FROM Employee;

| name        | hire_year |
| ----------- | --------- |
| John Doe    | 2020      |
| Jane Smith  | 2019      |
| Bob Brown   | 2018      |
| Alice Blue  | 2021      |
| Charlie P.  | 2019      |
| David Green | 2022      |
| Eve Black   | 2021      |
| Frank White | 2021      |
| Grace Kelly | 2018      |
| Hannah Lee  | 2020      |
    
    -- Question 16
    -- Find the average salary of all employees
    
    SELECT AVG(salary) AS average_salary
    FROM Employee;

| average_salary |
| -------------- |
| 57600.0        |

---
**Query #7**

    -- Question 17
    -- Find the maximum salary in the Employee table
    
    SELECT MAX(salary) AS maximum_salary
    FROM Employee;

| maximum_salary |
| -------------- |
| 80000.0        |

---
**Query #8**

    -- Question 18
    -- Find the minimum salary in the Employee table
    
    SELECT MIN(salary) AS minimum_salary
    FROM Employee;

| minimum_salary |
| -------------- |
| 45000.0        |

---
**Query #9**

    -- Question 19
    -- Count the total number of employees
    
    SELECT COUNT(*) AS total_employees
    FROM Employee;

| total_employees |
| --------------- |
| 10              |

---
**Query #20**

    -- Question 20
    -- Find the total salary paid to all employees
    
    SELECT SUM(salary) AS total_salary
    FROM Employee;

| total_salary |
| ------------ |
| 576000.0     |

 
    -- Question 21
    -- Find the average salary department-wise
    
    SELECT department_id, AVG(salary) AS average_salary
    FROM Employee
    GROUP BY department_id;

| department_id | average_salary |
| ------------- | -------------- |
|               | 48000.0        |
| 1             | 65000.0        |
| 2             | 55000.0        |
| 3             | 50000.0        |
| 4             | 61500.0        |

---

    -- Question 22
    -- Count employees in each department
    
    SELECT department_id, COUNT(*) AS employee_count
    FROM Employee
    GROUP BY department_id;

| department_id | employee_count |
| ------------- | -------------- |
|               | 1              |
| 1             | 3              |
| 2             | 2              |
| 3             | 2              |
| 4             | 2              |

---

    -- Question 23
    -- Find maximum salary in each department
    
    SELECT department_id, MAX(salary) AS max_salary
    FROM Employee
    GROUP BY department_id;

| department_id | max_salary |
| ------------- | ---------- |
|               | 48000.0    |
| 1             | 80000.0    |
| 2             | 60000.0    |
| 3             | 55000.0    |
| 4             | 70000.0    |

---

    -- Question 24
    -- Find minimum salary in each department
    
    SELECT department_id, MIN(salary) AS min_salary
    FROM Employee
    GROUP BY department_id;

| department_id | min_salary |
| ------------- | ---------- |
|               | 48000.0    |
| 1             | 50000.0    |
| 2             | 50000.0    |
| 3             | 45000.0    |
| 4             | 53000.0    |

---

    -- Question 25
    -- Find total salary department-wise
    
    SELECT department_id, SUM(salary) AS total_salary
    FROM Employee
    GROUP BY department_id;

| department_id | total_salary |
| ------------- | ------------ |
|               | 48000.0      |
| 1             | 195000.0     |
| 2             | 110000.0     |
| 3             | 100000.0     |
| 4             | 123000.0     |

---

    -- Question 26
    -- Departments having more than 2 employees
    
    SELECT department_id, COUNT(*) AS employee_count
    FROM Employee
    GROUP BY department_id
    HAVING COUNT(*) > 2;

| department_id | employee_count |
| ------------- | -------------- |
| 1             | 3              |

---

    -- Question 27
    -- Departments with average salary greater than 55000
    
    SELECT department_id, AVG(salary) AS average_salary
    FROM Employee
    GROUP BY department_id
    HAVING AVG(salary) > 55000;

| department_id | average_salary |
| ------------- | -------------- |
| 1             | 65000.0        |
| 4             | 61500.0        |

---

    -- Question 28
    -- Departments with total salary greater than 100000
    
    SELECT department_id, SUM(salary) AS total_salary
    FROM Employee
    GROUP BY department_id
    HAVING SUM(salary) > 100000;

| department_id | total_salary |
| ------------- | ------------ |
| 1             | 195000.0     |
| 2             | 110000.0     |
| 4             | 123000.0     |

---

    -- Question 29
    -- Departments having maximum salary above 70000
    
    SELECT department_id, MAX(salary) AS max_salary
    FROM Employee
    GROUP BY department_id
    HAVING MAX(salary) > 70000;

| department_id | max_salary |
| ------------- | ---------- |
| 1             | 80000.0    |

---

    -- Question 30
    -- Departments having less than 3 employees
    
    SELECT department_id, COUNT(*) AS employee_count
    FROM Employee
    GROUP BY department_id
    HAVING COUNT(*) < 3;

| department_id | employee_count |
| ------------- | -------------- |
|               | 1              |
| 2             | 2              |
| 3             | 2              |
| 4             | 2              |

---

    -- Question 31
    -- Display employees ordered by salary ascending
    
    SELECT *
    FROM Employee
    ORDER BY salary ASC;

| emp_id | name        | age | salary  | department_id | hire_date  |
| ------ | ----------- | --- | ------- | ------------- | ---------- |
| 4      | Alice Blue  | 25  | 45000.0 | 3             | 2021-03-22 |
| 8      | Frank White | 32  | 48000.0 |               | 2021-07-10 |
| 1      | John Doe    | 28  | 50000.0 | 1             | 2020-01-15 |
| 5      | Charlie P.  | 29  | 50000.0 | 2             | 2019-12-01 |
| 10     | Hannah Lee  | 30  | 53000.0 | 4             | 2020-02-25 |
| 7      | Eve Black   | 40  | 55000.0 | 3             | 2021-08-30 |
| 2      | Jane Smith  | 34  | 60000.0 | 2             | 2019-07-23 |
| 9      | Grace Kelly | 27  | 65000.0 | 1             | 2018-11-13 |
| 6      | David Green | 38  | 70000.0 | 4             | 2022-05-18 |
| 3      | Bob Brown   | 45  | 80000.0 | 1             | 2018-02-12 |

---

    -- Question 32
    -- Display employees ordered by salary descending
    
    SELECT *
    FROM Employee
    ORDER BY salary DESC;

| emp_id | name        | age | salary  | department_id | hire_date  |
| ------ | ----------- | --- | ------- | ------------- | ---------- |
| 3      | Bob Brown   | 45  | 80000.0 | 1             | 2018-02-12 |
| 6      | David Green | 38  | 70000.0 | 4             | 2022-05-18 |
| 9      | Grace Kelly | 27  | 65000.0 | 1             | 2018-11-13 |
| 2      | Jane Smith  | 34  | 60000.0 | 2             | 2019-07-23 |
| 7      | Eve Black   | 40  | 55000.0 | 3             | 2021-08-30 |
| 10     | Hannah Lee  | 30  | 53000.0 | 4             | 2020-02-25 |
| 1      | John Doe    | 28  | 50000.0 | 1             | 2020-01-15 |
| 5      | Charlie P.  | 29  | 50000.0 | 2             | 2019-12-01 |
| 8      | Frank White | 32  | 48000.0 |               | 2021-07-10 |
| 4      | Alice Blue  | 25  | 45000.0 | 3             | 2021-03-22 |

---

    -- Question 33
    -- Display employees ordered by age
    
    SELECT *
    FROM Employee
    ORDER BY age;

| emp_id | name        | age | salary  | department_id | hire_date  |
| ------ | ----------- | --- | ------- | ------------- | ---------- |
| 4      | Alice Blue  | 25  | 45000.0 | 3             | 2021-03-22 |
| 9      | Grace Kelly | 27  | 65000.0 | 1             | 2018-11-13 |
| 1      | John Doe    | 28  | 50000.0 | 1             | 2020-01-15 |
| 5      | Charlie P.  | 29  | 50000.0 | 2             | 2019-12-01 |
| 10     | Hannah Lee  | 30  | 53000.0 | 4             | 2020-02-25 |
| 8      | Frank White | 32  | 48000.0 |               | 2021-07-10 |
| 2      | Jane Smith  | 34  | 60000.0 | 2             | 2019-07-23 |
| 6      | David Green | 38  | 70000.0 | 4             | 2022-05-18 |
| 7      | Eve Black   | 40  | 55000.0 | 3             | 2021-08-30 |
| 3      | Bob Brown   | 45  | 80000.0 | 1             | 2018-02-12 |

---

    -- Question 34
    -- Display employees ordered by hire date descending
    
    SELECT *
    FROM Employee
    ORDER BY hire_date DESC;

| emp_id | name        | age | salary  | department_id | hire_date  |
| ------ | ----------- | --- | ------- | ------------- | ---------- |
| 6      | David Green | 38  | 70000.0 | 4             | 2022-05-18 |
| 7      | Eve Black   | 40  | 55000.0 | 3             | 2021-08-30 |
| 8      | Frank White | 32  | 48000.0 |               | 2021-07-10 |
| 4      | Alice Blue  | 25  | 45000.0 | 3             | 2021-03-22 |
| 10     | Hannah Lee  | 30  | 53000.0 | 4             | 2020-02-25 |
| 1      | John Doe    | 28  | 50000.0 | 1             | 2020-01-15 |
| 5      | Charlie P.  | 29  | 50000.0 | 2             | 2019-12-01 |
| 2      | Jane Smith  | 34  | 60000.0 | 2             | 2019-07-23 |
| 9      | Grace Kelly | 27  | 65000.0 | 1             | 2018-11-13 |
| 3      | Bob Brown   | 45  | 80000.0 | 1             | 2018-02-12 |

---

    -- Question 35
    -- Display employees ordered by department and salary
    
    SELECT *
    FROM Employee
    ORDER BY department_id, salary DESC;

| emp_id | name        | age | salary  | department_id | hire_date  |
| ------ | ----------- | --- | ------- | ------------- | ---------- |
| 8      | Frank White | 32  | 48000.0 |               | 2021-07-10 |
| 3      | Bob Brown   | 45  | 80000.0 | 1             | 2018-02-12 |
| 9      | Grace Kelly | 27  | 65000.0 | 1             | 2018-11-13 |
| 1      | John Doe    | 28  | 50000.0 | 1             | 2020-01-15 |
| 2      | Jane Smith  | 34  | 60000.0 | 2             | 2019-07-23 |
| 5      | Charlie P.  | 29  | 50000.0 | 2             | 2019-12-01 |
| 7      | Eve Black   | 40  | 55000.0 | 3             | 2021-08-30 |
| 4      | Alice Blue  | 25  | 45000.0 | 3             | 2021-03-22 |
| 6      | David Green | 38  | 70000.0 | 4             | 2022-05-18 |
| 10     | Hannah Lee  | 30  | 53000.0 | 4             | 2020-02-25 |

---

    -- Question 36
    -- Display employee names with department names
    
    SELECT e.name AS employee_name,
           d.name AS department_name
    FROM Employee e
    JOIN Department d
    ON e.department_id = d.department_id;

| employee_name | department_name |
| ------------- | --------------- |
| John Doe      | IT              |
| Bob Brown     | IT              |
| Grace Kelly   | IT              |
| Jane Smith    | HR              |
| Charlie P.    | HR              |
| Alice Blue    | Finance         |
| Eve Black     | Finance         |
| David Green   | Marketing       |
| Hannah Lee    | Marketing       |

---

    -- Question 37
    -- Display all employees with their projects
    
    SELECT e.name AS employee_name,
           p.name AS project_name
    FROM Employee e
    JOIN Project p
    ON e.department_id = p.department_id;

| employee_name | project_name    |
| ------------- | --------------- |
| John Doe      | Project Alpha   |
| Bob Brown     | Project Alpha   |
| Grace Kelly   | Project Alpha   |
| Jane Smith    | Project Beta    |
| Charlie P.    | Project Beta    |
| John Doe      | Project Gamma   |
| Bob Brown     | Project Gamma   |
| Grace Kelly   | Project Gamma   |
| Alice Blue    | Project Delta   |
| Eve Black     | Project Delta   |
| David Green   | Project Epsilon |
| Hannah Lee    | Project Epsilon |
| David Green   | Project Zeta    |
| Hannah Lee    | Project Zeta    |
| Alice Blue    | Project Eta     |
| Eve Black     | Project Eta     |
| John Doe      | Project Theta   |
| Bob Brown     | Project Theta   |
| Grace Kelly   | Project Theta   |

---

    -- Question 38
    -- Display all departments and their employees
    
    SELECT d.name AS department_name,
           e.name AS employee_name
    FROM Department d
    LEFT JOIN Employee e
    ON d.department_id = e.department_id;

| department_name | employee_name |
| --------------- | ------------- |
| IT              | John Doe      |
| IT              | Bob Brown     |
| IT              | Grace Kelly   |
| HR              | Jane Smith    |
| HR              | Charlie P.    |
| Finance         | Alice Blue    |
| Finance         | Eve Black     |
| Marketing       | David Green   |
| Marketing       | Hannah Lee    |

---

    -- Question 39
    -- Display all departments and their projects
    
    SELECT d.name AS department_name,
           p.name AS project_name
    FROM Department d
    LEFT JOIN Project p
    ON d.department_id = p.department_id;

| department_name | project_name    |
| --------------- | --------------- |
| IT              | Project Alpha   |
| IT              | Project Gamma   |
| IT              | Project Theta   |
| HR              | Project Beta    |
| Finance         | Project Delta   |
| Finance         | Project Eta     |
| Marketing       | Project Epsilon |
| Marketing       | Project Zeta    |

---

    -- Question 40
    -- Display employees without departments
    
    SELECT *
    FROM Employee
    WHERE department_id IS NULL;

| emp_id | name        | age | salary  | department_id | hire_date  |
| ------ | ----------- | --- | ------- | ------------- | ---------- |
| 8      | Frank White | 32  | 48000.0 |               | 2021-07-10 |

---

    -- Question 41
    -- Display projects without departments
    
    SELECT *
    FROM Project
    WHERE department_id IS NULL;

| project_id | name         | department_id |
| ---------- | ------------ | ------------- |
| 9          | Project Iota |               |

---

    -- Question 42
    -- Display employees and departments using INNER JOIN
    
    SELECT e.name,
           d.name
    FROM Employee e
    INNER JOIN Department d
    ON e.department_id = d.department_id;

| name        | name      |
| ----------- | --------- |
| John Doe    | IT        |
| Bob Brown   | IT        |
| Grace Kelly | IT        |
| Jane Smith  | HR        |
| Charlie P.  | HR        |
| Alice Blue  | Finance   |
| Eve Black   | Finance   |
| David Green | Marketing |
| Hannah Lee  | Marketing |

---

    -- Question 43
    -- Display all employees even if department is missing
    
    SELECT e.name,
           d.name
    FROM Employee e
    LEFT JOIN Department d
    ON e.department_id = d.department_id;

| name        | name      |
| ----------- | --------- |
| John Doe    | IT        |
| Jane Smith  | HR        |
| Bob Brown   | IT        |
| Alice Blue  | Finance   |
| Charlie P.  | HR        |
| David Green | Marketing |
| Eve Black   | Finance   |
| Frank White |           |
| Grace Kelly | IT        |
| Hannah Lee  | Marketing |

---

    -- Question 44
    -- Display all departments even if employees are absent
    
    SELECT d.name,
           e.name
    FROM Department d
    LEFT JOIN Employee e
    ON d.department_id = e.department_id;

| name      | name        |
| --------- | ----------- |
| IT        | John Doe    |
| IT        | Bob Brown   |
| IT        | Grace Kelly |
| HR        | Jane Smith  |
| HR        | Charlie P.  |
| Finance   | Alice Blue  |
| Finance   | Eve Black   |
| Marketing | David Green |
| Marketing | Hannah Lee  |

---

    -- Question 45
    -- Display employees working on projects in their department
    
    SELECT e.name AS employee_name,
           p.name AS project_name
    FROM Employee e
    JOIN Project p
    ON e.department_id = p.department_id;

| employee_name | project_name    |
| ------------- | --------------- |
| John Doe      | Project Alpha   |
| Bob Brown     | Project Alpha   |
| Grace Kelly   | Project Alpha   |
| Jane Smith    | Project Beta    |
| Charlie P.    | Project Beta    |
| John Doe      | Project Gamma   |
| Bob Brown     | Project Gamma   |
| Grace Kelly   | Project Gamma   |
| Alice Blue    | Project Delta   |
| Eve Black     | Project Delta   |
| David Green   | Project Epsilon |
| Hannah Lee    | Project Epsilon |
| David Green   | Project Zeta    |
| Hannah Lee    | Project Zeta    |
| Alice Blue    | Project Eta     |
| Eve Black     | Project Eta     |
| John Doe      | Project Theta   |
| Bob Brown     | Project Theta   |
| Grace Kelly   | Project Theta   |

---

    -- Question 46
    -- Employees earning above average salary
    
    SELECT *
    FROM Employee
    WHERE salary > (
        SELECT AVG(salary)
        FROM Employee
    );

| emp_id | name        | age | salary  | department_id | hire_date  |
| ------ | ----------- | --- | ------- | ------------- | ---------- |
| 2      | Jane Smith  | 34  | 60000.0 | 2             | 2019-07-23 |
| 3      | Bob Brown   | 45  | 80000.0 | 1             | 2018-02-12 |
| 6      | David Green | 38  | 70000.0 | 4             | 2022-05-18 |
| 9      | Grace Kelly | 27  | 65000.0 | 1             | 2018-11-13 |

---

    -- Question 47
    -- Employees earning maximum salary
    
    SELECT *
    FROM Employee
    WHERE salary = (
        SELECT MAX(salary)
        FROM Employee
    );

| emp_id | name      | age | salary  | department_id | hire_date  |
| ------ | --------- | --- | ------- | ------------- | ---------- |
| 3      | Bob Brown | 45  | 80000.0 | 1             | 2018-02-12 |

---

    -- Question 48
    -- Employees earning minimum salary
    
    SELECT *
    FROM Employee
    WHERE salary = (
        SELECT MIN(salary)
        FROM Employee
    );

| emp_id | name       | age | salary  | department_id | hire_date  |
| ------ | ---------- | --- | ------- | ------------- | ---------- |
| 4      | Alice Blue | 25  | 45000.0 | 3             | 2021-03-22 |

---

    -- Question 49
    -- Employees working in IT department
    
    SELECT *
    FROM Employee
    WHERE department_id = (
        SELECT department_id
        FROM Department
        WHERE name = 'IT'
    );

| emp_id | name        | age | salary  | department_id | hire_date  |
| ------ | ----------- | --- | ------- | ------------- | ---------- |
| 1      | John Doe    | 28  | 50000.0 | 1             | 2020-01-15 |
| 3      | Bob Brown   | 45  | 80000.0 | 1             | 2018-02-12 |
| 9      | Grace Kelly | 27  | 65000.0 | 1             | 2018-11-13 |

---

    -- Question 50
    -- Employees working in departments having projects
    
    SELECT *
    FROM Employee
    WHERE department_id IN (
        SELECT department_id
        FROM Project
    );

| emp_id | name        | age | salary  | department_id | hire_date  |
| ------ | ----------- | --- | ------- | ------------- | ---------- |
| 1      | John Doe    | 28  | 50000.0 | 1             | 2020-01-15 |
| 2      | Jane Smith  | 34  | 60000.0 | 2             | 2019-07-23 |
| 3      | Bob Brown   | 45  | 80000.0 | 1             | 2018-02-12 |
| 4      | Alice Blue  | 25  | 45000.0 | 3             | 2021-03-22 |
| 5      | Charlie P.  | 29  | 50000.0 | 2             | 2019-12-01 |
| 6      | David Green | 38  | 70000.0 | 4             | 2022-05-18 |
| 7      | Eve Black   | 40  | 55000.0 | 3             | 2021-08-30 |
| 9      | Grace Kelly | 27  | 65000.0 | 1             | 2018-11-13 |
| 10     | Hannah Lee  | 30  | 53000.0 | 4             | 2020-02-25 |

---

    -- Question 51
    -- Departments having employees with salary above 60000
    
    SELECT *
    FROM Department
    WHERE department_id IN (
        SELECT department_id
        FROM Employee
        WHERE salary > 60000
    );

| department_id | name      |
| ------------- | --------- |
| 1             | IT        |
| 4             | Marketing |

---

    -- Question 52
    -- Employees hired before the average hire date
    
    SELECT *
    FROM Employee
    WHERE hire_date < (
        SELECT AVG(hire_date)
        FROM Employee
    );

| emp_id | name        | age | salary  | department_id | hire_date  |
| ------ | ----------- | --- | ------- | ------------- | ---------- |
| 2      | Jane Smith  | 34  | 60000.0 | 2             | 2019-07-23 |
| 3      | Bob Brown   | 45  | 80000.0 | 1             | 2018-02-12 |
| 5      | Charlie P.  | 29  | 50000.0 | 2             | 2019-12-01 |
| 9      | Grace Kelly | 27  | 65000.0 | 1             | 2018-11-13 |

---

    -- Question 53
    -- Employees whose salary equals department-wise maximum salary
    
    SELECT *
    FROM Employee e1
    WHERE salary = (
        SELECT MAX(salary)
        FROM Employee e2
        WHERE e1.department_id = e2.department_id
    );

| emp_id | name        | age | salary  | department_id | hire_date  |
| ------ | ----------- | --- | ------- | ------------- | ---------- |
| 2      | Jane Smith  | 34  | 60000.0 | 2             | 2019-07-23 |
| 3      | Bob Brown   | 45  | 80000.0 | 1             | 2018-02-12 |
| 6      | David Green | 38  | 70000.0 | 4             | 2022-05-18 |
| 7      | Eve Black   | 40  | 55000.0 | 3             | 2021-08-30 |

---

    -- Question 54
    -- Employees whose age is greater than average age
    
    SELECT *
    FROM Employee
    WHERE age > (
        SELECT AVG(age)
        FROM Employee
    );

| emp_id | name        | age | salary  | department_id | hire_date  |
| ------ | ----------- | --- | ------- | ------------- | ---------- |
| 2      | Jane Smith  | 34  | 60000.0 | 2             | 2019-07-23 |
| 3      | Bob Brown   | 45  | 80000.0 | 1             | 2018-02-12 |
| 6      | David Green | 38  | 70000.0 | 4             | 2022-05-18 |
| 7      | Eve Black   | 40  | 55000.0 | 3             | 2021-08-30 |

---

    -- Question 55
    -- Employees not assigned to any department
    
    SELECT *
    FROM Employee
    WHERE department_id IS NULL;

| emp_id | name        | age | salary  | department_id | hire_date  |
| ------ | ----------- | --- | ------- | ------------- | ---------- |
| 8      | Frank White | 32  | 48000.0 |               | 2021-07-10 |

---

 
    -- Question 56
    -- Find department with highest average salary
    
    SELECT department_id,
           AVG(salary) AS avg_salary
    FROM Employee
    GROUP BY department_id
    ORDER BY avg_salary DESC
    LIMIT 1;

| department_id | avg_salary |
| ------------- | ---------- |
| 1             | 65000.0    |

---

    -- Question 57
    -- Find youngest employee
    
    SELECT *
    FROM Employee
    ORDER BY age ASC
    LIMIT 1;

| emp_id | name       | age | salary  | department_id | hire_date  |
| ------ | ---------- | --- | ------- | ------------- | ---------- |
| 4      | Alice Blue | 25  | 45000.0 | 3             | 2021-03-22 |

---

    -- Question 58
    -- Find oldest employee
    
    SELECT *
    FROM Employee
    ORDER BY age DESC
    LIMIT 1;

| emp_id | name      | age | salary  | department_id | hire_date  |
| ------ | --------- | --- | ------- | ------------- | ---------- |
| 3      | Bob Brown | 45  | 80000.0 | 1             | 2018-02-12 |

---

    -- Question 59
    -- Display employees and project count department-wise
    
    SELECT d.name,
           COUNT(p.project_id) AS project_count
    FROM Department d
    LEFT JOIN Project p
    ON d.department_id = p.department_id
    GROUP BY d.name;

| name      | project_count |
| --------- | ------------- |
| IT        | 3             |
| HR        | 1             |
| Finance   | 2             |
| Marketing | 2             |

---

    -- Question 60
    -- Display departments with no employees
    
    SELECT *
    FROM Department
    WHERE department_id NOT IN (
        SELECT DISTINCT department_id
        FROM Employee
        WHERE department_id IS NOT NULL
    );

There are no results to be displayed.

---

    -- Question 61
    -- Find second highest salary
    
    SELECT MAX(salary) AS second_highest_salary
    FROM Employee
    WHERE salary < (
        SELECT MAX(salary)
        FROM Employee
    );

| second_highest_salary |
| --------------------- |
| 70000.0               |

---

    -- Question 62
    -- Find employees whose names contain letter 'e'
    
    SELECT *
    FROM Employee
    WHERE name LIKE '%e%';

| emp_id | name        | age | salary  | department_id | hire_date  |
| ------ | ----------- | --- | ------- | ------------- | ---------- |
| 1      | John Doe    | 28  | 50000.0 | 1             | 2020-01-15 |
| 2      | Jane Smith  | 34  | 60000.0 | 2             | 2019-07-23 |
| 4      | Alice Blue  | 25  | 45000.0 | 3             | 2021-03-22 |
| 5      | Charlie P.  | 29  | 50000.0 | 2             | 2019-12-01 |
| 6      | David Green | 38  | 70000.0 | 4             | 2022-05-18 |
| 7      | Eve Black   | 40  | 55000.0 | 3             | 2021-08-30 |
| 8      | Frank White | 32  | 48000.0 |               | 2021-07-10 |
| 9      | Grace Kelly | 27  | 65000.0 | 1             | 2018-11-13 |
| 10     | Hannah Lee  | 30  | 53000.0 | 4             | 2020-02-25 |

---

    -- Question 63
    -- Find total employees hired after 2020
    
    SELECT COUNT(*) AS total_employees
    FROM Employee
    WHERE YEAR(hire_date) > 2020;

| total_employees |
| --------------- |
| 4               |

---

    -- Question 64
    -- Display department names with employee count
    
    SELECT d.name,
           COUNT(e.emp_id) AS employee_count
    FROM Department d
    LEFT JOIN Employee e
    ON d.department_id = e.department_id
    GROUP BY d.name;

| name      | employee_count |
| --------- | -------------- |
| IT        | 3              |
| HR        | 2              |
| Finance   | 2              |
| Marketing | 2              |

---

    -- Question 65
    -- Display all employee names and corresponding department names
    
    SELECT e.name AS employee_name,
           d.name AS department_name
    FROM Employee e
    LEFT JOIN Department d
    ON e.department_id = d.department_id;

| employee_name | department_name |
| ------------- | --------------- |
| John Doe      | IT              |
| Jane Smith    | HR              |
| Bob Brown     | IT              |
| Alice Blue    | Finance         |
| Charlie P.    | HR              |
| David Green   | Marketing       |
| Eve Black     | Finance         |
| Frank White   |                 |
| Grace Kelly   | IT              |
| Hannah Lee    | Marketing       |
