# Project Description

## Investigation and Update of Employee Login Activities and Departmental Records

In this project, I will use SQL queries to conduct a detailed analysis of employee login activities and departmental records. The goal is to identify and address specific issues related to security and system updates. The scope of the project includes the following tasks:

### 1. Investigation of Failed Login Attempts
- Analyze failed login attempts that occurred after business hours.
- Retrieve and examine login activity records to identify all unsuccessful attempts made after 18:00.

### 2. Review of Suspicious Events
- Investigate a suspicious event that took place on `2022-05-09`.
- Retrieve all login attempts that occurred on the day of the event and the previous day (`2022-05-08`).

### 3. Analysis of Non-Mexico Logins
- Examine login activities that did not originate in Mexico.
- Focus on records where the country field is listed as `'MEX'` or `'MEXICO'` to understand potential unauthorized access.

### 4. Department and Office Information Retrieval
- Retrieve information from the department and office columns within the employee table.
- Write a SQL query to view the necessary columns and values to assist in the project analysis.

### 5. Update of Employee Machines in the Marketing Department
- Gather information on employees in the `'Marketing'` department located in offices within the East building (e.g., `'East-170'` or `'East-320'`).
- Write a SQL query to filter the records accordingly.

### 6. Preparation for Updates in the Finance and Sales Departments
- Identify employees within the `'Finance'` and `'Sales'` departments to prepare for a targeted system update.
- Write a SQL query to retrieve these relevant records.

### 7. Identification of Non-IT Department Employees
- Focus on employees who are not part of the Information Technology department.
- Use the `NOT` operator to write a SQL query that excludes records for employees in the IT department.

•	Retrieve after hours failed login attempts
SELECT *
FROM employees 
WHERE log_in_attempts > ’18:00’;

( I used SELECT *  to query all records from employees table,  where log_in_attempts occur after 18:00, using  (> operator))

•	Retrieve login attempts on specific dates
SELECT *
FROM employees 
WHERE log_in_attempts = ‘2024-08-11’ OR log_in_attempts = ‘2024-08-10’;

( I used  SELECT * to query all records from employees table with WHERE command for returning  log_in_attempts match for  either '2024-08-11' or '2024-08-10'. I accomplished this with  (= and OR operators).

-	Retrieve login attempts outside of ``Mexico``
```sql
SELECT *
FROM employees 
WHERE NOT country LIKE "MEX%"; 
```
- Retrieve employees in `Marketing`
```sql
SELECT *
FROM employees 
WHERE department = "Marketing";
```
- Retrieve employees in `Finance or Sales`
```sql 
SELECT *
FROM employees 
WHERE department = 'Finance' OR department = 'Sales';
```
- Retrieve all employees not in `IT`
```sql
SELECT *
FROM employees
WHERE NOT department = 'Information Technology';
```
##	Summary
I was able to effectively  utilized SQL operators such as ( >, =, OR, LIKE, and NOT)  to investigate and update employee login activities and departmental records, conducting a detailed analysis to identify and resolve specific security and system update issues.



•	Retrieve login attempts outside of Mexico: Use SELECT * with WHERE NOT to exclude records where the country field starts with 'MEX' (LIKE and NOT operators).
•	Retrieve employees in Marketing: Use SELECT * to query records where the department is 'Marketing' (= operator).
•	Retrieve employees in Finance or Sales: Use SELECT * to query records where the department is either 'Finance' or 'Sales' (OR operator).
•	Retrieve all employees not in IT: Use SELECT * with WHERE NOT to exclude records where the department is 'Information Technology' (NOT operator).
