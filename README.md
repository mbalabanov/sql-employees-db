# SQL Employees DB Admin

### 1. Report:
**How many rows do we have in each table in the employees database?**
```
SELECT DISTINCT COUNT(*) as "Number of Rows"
FROM `employees`;
```

### 2. Report:
**How many employees with the first name "Mark" do we have in our company?**
```
SELECT DISTINCT COUNT(*) as "First Name Mark"
FROM `employees`
WHERE first_name = 'Mark'
```

### 3. Report:
***How many employees with the first name "Eric" and the last name beginning with "A" do we have in our company?**
```
SELECT DISTINCT COUNT(*) as 'Eric, last name starts with A'
FROM `employees` WHERE first_name = 'Eric'
AND last_name LIKE 'A%'
```

### 4. Report:
**How many employees do we have that are working for us since 1985 and who are they?**
```
SELECT DISTINCT COUNT(*) 
FROM `employees`
WHERE hire_date > '19850000';

SELECT DISTINCT first_name, last_name 
FROM `employees`
WHERE hire_date > '19850000';
```

### 5. Report:
**How many employees got hired from 1990 until 1997 and who are they?**
```
SELECT DISTINCT COUNT(*)
FROM `employees`
WHERE hire_date > '19900000'
AND hire_date < '19970000';

SELECT DISTINCT first_name, last_name
FROM `employees`
WHERE hire_date > '19900000'
AND hire_date < '19970000';
```

## 6. Report:
**How many employees have salaries higher than EUR 70 000,00 and who are they?**
```
SELECT DISTINCT COUNT(*)
FROM employees
INNER JOIN salaries
ON salaries.emp_no = employees.emp_no
WHERE salary > 70000;

SELECT DISTINCT employees.emp_no, employees.first_name, employees.last_name, salaries.salary
FROM employees
INNER JOIN salaries
ON salaries.emp_no = employees.emp_no
WHERE salary > 70000
ORDER BY `salaries`
DESC;
```

## 7. Report:
**How many employees do we have in the Research Department, who are working for us since 1992 and who are they?**
```
SELECT DISTINCT COUNT(*)
FROM departments
AS res_dept
INNER JOIN dept_emp AS res_dept_emp
ON res_dept.dept_no = res_dept_emp.dept_no
INNER JOIN employees AS res_emp
ON res_emp.emp_no = res_dept_emp.emp_no
INNER JOIN salaries AS res_sal
ON res_sal.emp_no = res_emp.emp_no
WHERE res_emp.hire_date > '19920000'
AND res_dept.dept_name = 'Research'
AND res_sal.to_date = '9999-01-01';

SELECT DISTINCT res_emp.emp_no, res_emp.first_name, res_emp.last_name, res_dept.dept_name, res_dept_emp.dept_no
FROM departments
AS res_dept
INNER JOIN dept_emp AS res_dept_emp
ON res_dept.dept_no = res_dept_emp.dept_no
INNER JOIN employees AS res_emp
ON res_emp.emp_no = res_dept_emp.emp_no
WHERE res_emp.hire_date > '19920000'
AND res_dept.dept_name = 'Research'
AND res_sal.to_date = '9999-01-01';
```

## 8. Report:
**How many employees do we have in the Finance Department, who are working for us since 1985 until now and who have salaries higher than EUR 75 000,00 - who are they?**
```
SELECT DISTINCT COUNT(*)
FROM departments
AS res_dept
INNER JOIN dept_emp AS res_dept_emp
ON res_dept.dept_no = res_dept_emp.dept_no
INNER JOIN employees AS res_emp
ON res_emp.emp_no = res_dept_emp.emp_no
INNER JOIN salaries AS res_sal
ON res_sal.emp_no = res_emp.emp_no
WHERE res_emp.hire_date > '19850000'
AND res_dept.dept_name = 'Finance'
AND res_sal.salary > 75000
AND res_sal.to_date = '9999-01-01';

SELECT DISTINCT res_emp.emp_no, res_emp.first_name, res_emp.last_name, res_dept.dept_name, res_dept_emp.dept_no
FROM departments
AS res_dept
INNER JOIN dept_emp AS res_dept_emp
ON res_dept.dept_no = res_dept_emp.dept_no
INNER JOIN employees AS res_emp
ON res_emp.emp_no = res_dept_emp.emp_no
INNER JOIN salaries AS res_sal
ON res_sal.emp_no = res_emp.emp_no
WHERE res_emp.hire_date > '19850000'
AND res_dept.dept_name = 'Finance'
AND res_sal.salary > 75000;
```

## 9. Report:
**We need a table with employees, who are working for us at this moment: first and last name, date of birth, gender, hire_date, title and salary.**
```
SELECT DISTINCT emp.first_name, emp.last_name, emp.birth_date, emp.gender, emp.hire_date, tit.title, sal.salary
FROM employees AS emp
INNER JOIN salaries AS sal
ON sal.emp_no = emp.emp_no
INNER JOIN titles AS tit
ON tit.emp_no = emp.emp_no
WHERE sal.to_date = '9999-01-01'
```

## 10. Report:
**We need a table with managers, who are working for us at this moment: first and last name, date of birth, gender, hire_date, title, department name and salary.**
```

```

## Bonus query:
**Create a query that will join all tables and show all data from all tables.**
```

```
