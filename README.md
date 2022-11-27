# sql-challenge


 ​
#### Data Modeling

![employees_ERD](https://user-images.githubusercontent.com/113717031/204115450-a980613b-8f64-4da8-8bf6-e82bd2cee3c3.png)

 #### Data Analysis
 ​
 Once you have a complete database, perform these steps:
 ​
 1. List the following details of each employee: employee number, last name, first name, sex, and salary.

Select * from employees;

Select employees.emp_no, employees.last_name, employees.first_name, employees.sex, salaries.salary
from employees
inner join salaries on salaries.emp_no=employees.emp_no
limit (10);

![employees_q1](https://user-images.githubusercontent.com/113717031/204115522-aa876f13-8d3c-4962-a285-d46e0aa13e15.png)

2. List first name, last name, and hire date for employees who were hired in 1986.
select * from employees;

Select employees.first_name, employees.last_name, employees.hire_date
from employees
where employees.hire_date >= '1986-1-1'::date
and employees.hire_date < '1987-1-1'::date
limit(10);

![employees_q2](https://user-images.githubusercontent.com/113717031/204115525-46f34790-416d-4e02-aa40-7dce5e399d77.png)

 3. List the manager of each department with the following information: department number, department name, the manager's employee number, last name, first name.

Select * from departments;
Select * from dept_manager;
Select * from employees;

Select departments.dept_no, departments.dept_name, dept_manager.emp_no, employees.last_name, employees.first_name
from departments
inner join dept_manager on dept_manager.dept_no= departments.dept_no 
inner join employees on employees.emp_no=dept_manager.emp_no
limit (50); 

![employees_q3](https://user-images.githubusercontent.com/113717031/204115530-5ce6ec0c-b857-4a6d-b8a8-b272ce79ad33.png)

 4. List the department of each employee with the following information: employee number, last name, first name, and department name.

Select * from employees;

Select employees.emp_no,employees.last_name,employees.first_name, departments.dept_name
from employees
inner join dept_emp on dept_emp.emp_no= employees.emp_no 
inner join departments on departments.dept_no=dept_emp.dept_no
limit (10); 

![employees_q4](https://user-images.githubusercontent.com/113717031/204115534-0c939411-4c5a-4c99-97af-305473db7b22.png)

 5. List first name, last name, and sex for employees whose first name is "Hercules" and last names begin with "B."

Select * from employees;

Select employees.first_name, employees.last_name, employees.sex
from employees
where first_name='Hercules' and last_name similar to 'B%'
 --where first_name='Hercules' and last_name='B%'
limit(10);

![employees_q5](https://user-images.githubusercontent.com/113717031/204115540-e2c701c1-0e9d-47b5-82a9-8477c1f2eaf1.png)

 6. List all employees in the Sales department, including their employee number, last name, first name, and department name.

Select * from employees;
select * from departments;


Select employees.emp_no,employees.last_name,employees.first_name, departments.dept_name
from employees
inner join dept_emp on dept_emp.emp_no= employees.emp_no 
inner join departments on departments.dept_no=dept_emp.dept_no
where dept_name= 'Sales'
limit (10); 

![employees_q6](https://user-images.githubusercontent.com/113717031/204115546-f36068ef-e243-4339-88fa-40ed1170612b.png)

 7. List all employees in the Sales and Development departments, including their employee number, last name, first name, and department name.

Select employees.emp_no,employees.last_name,employees.first_name, departments.dept_name
from employees
inner join dept_emp on dept_emp.emp_no= employees.emp_no 
inner join departments on departments.dept_no=dept_emp.dept_no
where dept_name= 'Sales'
or dept_name='Development'
limit (10); 

![employees_q7](https://user-images.githubusercontent.com/113717031/204115550-193ff820-0fe9-4c0b-b456-b3ce12c28be0.png)

 8. List the frequency count of employee last names (i.e., how many employees share each last name) in descending order.

Select count(*) from employees.last_name

SELECT employees.last_name,COUNT(*) 
FROM employees 
GROUP BY employees.last_name 
ORDER BY COUNT(*) DESC;

![employees_q8](https://user-images.githubusercontent.com/113717031/204115557-f0faee12-c883-4311-8bf1-f74be5ea576b.png)


