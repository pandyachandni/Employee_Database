# Employee_Database

Overview for Analysis: The purpose of this activity is to determine the number of retiring employees per title and to see how many new hires will be needed once the tsumani on retirements start. Once this number of retirees are found then it is needed to identify employees who are eligible to participate in a mentorship program to train the incoming new employees.

Results:
1. The list of retiring employees

This table includes employee number, first name, last name, title, from-date and to-date and the query returns 133,776 rows. In this table it also displays the list of employees who will retire in the next few years.
The query returns 133,776 rows.

In order to get this data we had to merge two tables which where the employees and title. This was done by using the inner join and filtered by birth date, that indicates who is about to retire in the next few years with the command WHERE (e.birth_date BETWEEN '1952-01-01' AND '1955-12-31'). This query did result in duplicates which implied that there were more retirees than actual.

2. The list of retiring employees without duplicates

This table includes employee number, first name, last name, title, from-date and to-date and the query returns 90,398 rows which shows the list of employees who will retire soon and this table only shows the listed person once.

To only keep unique values we used the same data, we typed the query above with distinct_on command so it will keep only unique values. In order to make sure recent values are shown, it was order by command by rt.emp_no, rt.to_date DESC to sort the data in descending order. 

3. The number of retiring employees grouped by title

This table includes employees’ titles and their sum which the query returned a table with 7 rows and from this table we can see how many employees from each title that will be leaving
The query returns a cohesive table with 7 rows.

To retrieve this table the GROUP BY ut.title command was used to organize the groupings by titles. The command COUNT was used to count the specific titles in the database.

4. The employees eligible for the mentorship program

This table contains employee number, first name, last name, birth date, from date, to date and title and this query returned 1,549 rows and the tables purpose is to show a list of employees who is eligible for the mentorship program.

To retrieve this data, three tables were merge together: employees, titles and dep_emp with the inner join. The query filters by birth date (that indicates who is eligible for the mentorship program) with the command WHERE (e.birth_date BETWEEN '1952-01-01' AND '1955-12-31') and to_date to include only current employees. Duplicates were removed by DISTINCT ON (e.emp_no) command. To ensure the most recent titles, the command used ORDER BY e.emp_no, ti.from_date DESC command.



Summary:
How many roles will need to be filled as the "silver tsunami" begins to make an impact? 72,458 employees are retiring so the same for hiring.
Are there enough qualified, retirement-ready employees in the departments to mentor the next generation of Pewlett Hackard employees? 1549 employees are qualified and no this is not enough to train the incoming amount of employees needed to fill the retiring workers.

