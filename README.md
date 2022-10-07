# Employee_Database

Overview for Analysis: The purpose of this activity is to determine the number of retiring employees per title and to see how many new hires will be needed once the tsumani on retirements start. Once this number of retirees are found then it is needed to identify employees who are eligible to participate in a mentorship program to train the incoming new employees.

Results:
1. The list of retiring employees

This table includes employee number, first name, last name, title, from-date and to-date and the query returns 133,776 rows. In this table it also displays the list of employees who will retire in the next few years.
The query returns 133,776 rows.

In order to get this data we had to merge two tables which where the employees and title. This was done by using the inner join and filtered by birth date, that indicates who is about to retire in the next few years with the command WHERE (e.birth_date BETWEEN '1952-01-01' AND '1955-12-31'). This query did result in duplicates which implied that there were more retirees than actual.

2. The list of retiring employees without duplicates

This table includes employee number, first name, last name, title, from-date and to-date and the query returns 90,398 rows which shows the list of employees who will retire soon and this table only shows the listed person once.
The table displays a list of employees who are going to retire in the next few years.

To only keep unique values we used the same data
Query contains the same data as the query above with addition of distinct_on command that kept only unique values. To ensure that most recent values are kept, I used command ORDER BY rt.emp_no, rt.to_date DESC to sort the data by descending order on the to_date column. In this case the most recent title was listed first, and after running the query the duplicates listed after the first appearance of the same employees were removed.

3. The number of retiring employees grouped by title

The table includes employees’ titles and their sum.
The query returns a cohesive table with 7 rows.
From this table we can quickly see how many employees with certain title will retire in the next few years.


Figure 4: Table with the employee grouped by title

Overview of the code

In order to retrieve this table I used GROUP BY ut.title command, and it is responsible for grouping the rows by titles. Next, I used its corresponding command COUNT (ut.title) that counts how many times specific title appears in the database.

4. The employees eligible for the mentorship program

The table contains employee number, first name, last name, birth date, from date, to date and title.
The query returns 1,549 rows.
The table displays a list of employees who is eligible for the mentorship program.


Figure 5: Table with the employee grouped by title

Overview of the code

To retrieve this data, three tables were merge together: employees, titles and dep_emp with the inner join. The query filters by birth date (that indicates who is eligible for the mentorship program) with the command WHERE (e.birth_date BETWEEN '1952-01-01' AND '1955-12-31') and to_date to include only current employees. Duplicates were removed by DISTINCT ON (e.emp_no) command. To ensure I got the most recent titles, I used ORDER BY e.emp_no, ti.from_date DESC command.



Summary:
How many roles will need to be filled as the "silver tsunami" begins to make an impact? 72,458 employees are retiring so the same for hiring.
Are there enough qualified, retirement-ready employees in the departments to mentor the next generation of Pewlett Hackard employees? 1549 employees are qualified and no this is not enough to train the incoming amount of employees needed to fill the retiring workers.

