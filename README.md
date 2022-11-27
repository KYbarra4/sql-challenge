# sql-challenge


 ​
#### Data Modeling

![employees_ERD](https://user-images.githubusercontent.com/113717031/204115450-a980613b-8f64-4da8-8bf6-e82bd2cee3c3.png)


 ​
 #### Data Engineering
 ​

 ​
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



2. List first name, last name, and hire date for employees who were hired in 1986.
select * from employees;

Select employees.first_name, employees.last_name, employees.hire_date
from employees
where employees.hire_date >= '1986-1-1'::date
and employees.hire_date < '1987-1-1'::date
limit(10);

 3. List the manager of each department with the following information: department number, department name, the manager's employee number, last name, first name.

Select * from departments;
Select * from dept_manager;
Select * from employees;

Select departments.dept_no, departments.dept_name, dept_manager.emp_no, employees.last_name, employees.first_name
from departments
inner join dept_manager on dept_manager.dept_no= departments.dept_no 
inner join employees on employees.emp_no=dept_manager.emp_no
limit (50); 

 4. List the department of each employee with the following information: employee number, last name, first name, and department name.

Select * from employees;

Select employees.emp_no,employees.last_name,employees.first_name, departments.dept_name
from employees
inner join dept_emp on dept_emp.emp_no= employees.emp_no 
inner join departments on departments.dept_no=dept_emp.dept_no
limit (10); 


 5. List first name, last name, and sex for employees whose first name is "Hercules" and last names begin with "B."

Select * from employees;

Select employees.first_name, employees.last_name, employees.sex
from employees
where first_name='Hercules' and last_name similar to 'B%'
 --where first_name='Hercules' and last_name='B%'
limit(10);

 6. List all employees in the Sales department, including their employee number, last name, first name, and department name.

Select * from employees;
select * from departments;


Select employees.emp_no,employees.last_name,employees.first_name, departments.dept_name
from employees
inner join dept_emp on dept_emp.emp_no= employees.emp_no 
inner join departments on departments.dept_no=dept_emp.dept_no
where dept_name= 'Sales'
limit (10); 


 7. List all employees in the Sales and Development departments, including their employee number, last name, first name, and department name.

Select employees.emp_no,employees.last_name,employees.first_name, departments.dept_name
from employees
inner join dept_emp on dept_emp.emp_no= employees.emp_no 
inner join departments on departments.dept_no=dept_emp.dept_no
where dept_name= 'Sales'
or dept_name='Development'
limit (10); 

 8. List the frequency count of employee last names (i.e., how many employees share each last name) in descending order.

Select count(*) from employees.last_name

SELECT employees.last_name,COUNT(*) 
FROM employees 
GROUP BY employees.last_name 
ORDER BY COUNT(*) DESC;

 ## Bonus (Optional)

 As you examine the data, you begin to suspect that the dataset is fake. Maybe your boss gave you spurious data in order to test the data engineering skills of a new employee? To confirm your hunch, you decide to create a visualization of the data to present to your boss. Follow these steps: 

 1. Import the SQL database into Pandas. (Yes, you could read the CSVs directly in Pandas, but you are, after all, trying to prove your technical mettle.) This step may require some research. Feel free to use the following code to get started. Be sure to make any necessary modifications for your username, password, host, port, and database name:

    ```sql
    from sqlalchemy import create_engine
    engine = create_engine('postgresql://localhost:5432/<your_db_name>')
    connection = engine.connect()
    ```
 ​
     * Consult the [SQLAlchemy documentation](https://docs.sqlalchemy.org/en/latest/core/engines.html#postgresql) for more information.
 ​
     * If you’re using a password, do not upload your password to your GitHub repository. Review this [video](https://www.youtube.com/watch?v=2uaTPmNvH0I) and the [GitHub website](https://help.github.com/en/github/using-git/ignoring-files) for more information.
 ​
 2. Create a histogram to visualize the most common salary ranges for employees.
 ​
 3. Create a bar chart of average salary by title.
 ​
 ​
 ## Submission
 ​
 * Create an image file of your ERD.
 ​
 * Create a `.sql` file of your table schemata.
 ​
 * Create a `.sql` file of your queries.
 ​
 * (Optional) Create a Jupyter notebook of the bonus analysis.
 ​
 * Create and upload a repository with the above files to GitHub and post a link on BootCamp Spot.
 ​
 * Ensure your repository has regular commits and a thorough README.md file
 ​
 ## Rubric
 ​
 [Unit 9 Homework Rubric](https://docs.google.com/document/d/1OksnTYNCT0v0E-VkhIMJ9-iG0_oXNwCZAJlKV0aVMKQ/edit?usp=sharing)
 ​
 - - -
 ​
 ## References
 ​
 Mockaroo, LLC. (2021). Realistic Data Generator. [https://www.mockaroo.com/](https://www.mockaroo.com/)
 ​
 - - -
 ​
 © 2022 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.
