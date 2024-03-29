# Applying Filters to SQL Queries

## Project Description
After the detection of a potential security incident, where repeated login attempts were made after company hours. The organization’s security team was tasked with performing an analysis on the matter. This document shows the process used for using SQL queries and filtering to help investigate the issue, and then performing further security-related tasks.

## Retrieve After-hours Failed Login Attempts

![1](https://github.com/RafUrera/Applying-Filters-to-SQL-Queries/assets/161657613/dd806626-ed08-40c6-b9fe-68844b32463a)

The first part of the investigation is to look for all the failed login attempts after company hours. 
To make the search specific. In the `WHERE` clause,  `login_time > ‘18:00’`, is used to display results for login attempts after 6pm. The next part of the line: `AND success = 0`, makes results only display failed login attempts. 

## Retrieve Login Attempts on Specific Dates

![2](https://github.com/RafUrera/Applying-Filters-to-SQL-Queries/assets/161657613/f5f33af2-af05-4a36-b051-e60537e5a91b)

There were suspicious logins on the date of 2022-05-09, so a closer look is needed on that day and the day before.  To narrow down the logins for specific dates. The `WHERE` clause in this query would use the `=` and `OR` operation to only bring back results of only the two relevant dates for this part of the investigation. The filters used were `login_date = ‘2022-05-09’` and `login_date = ‘2022-05-08’`, which both only show results from the respective dates that are taken from the `log_in_attempts` table.

## Retrieve Login Attempts Outside of Mexico

![3](https://github.com/RafUrera/Applying-Filters-to-SQL-Queries/assets/161657613/d7bce437-146a-440a-93d8-6fe2cc92d3fd)

The security team has determined that the login attempts were made outside Mexico. The next step of the search would be to remove Mexico-based login attempts. To do this, the `NOT` and `LIKE` operators would be used. To properly filter this search query `WHERE NOT country LIKE ‘Mex%’` would be used.

![3](https://github.com/RafUrera/Applying-Filters-to-SQL-Queries/assets/161657613/d7bce437-146a-440a-93d8-6fe2cc92d3fd)

The `NOT` operator returns all results excluding the given parameters from the country column, `LIKE ‘Mex%’` searches for variations on the name for Mexico. This is possible because the `LIKE` operator allows for the % to act as a variable amount of characters in the search. This is necessary because the database has different entries representing ‘Mexico’ such as `‘Mex’` or `‘Mexico’`.

## Retrieve Employees in Marketing

The security team requires security updates to be performed on devices in the Marketing department. The task comes down to finding which devices and in which building need to be maintained. To do this, the following query was used. 

![4](https://github.com/RafUrera/Applying-Filters-to-SQL-Queries/assets/161657613/7c3ad7f5-5b85-4a7d-8cec-c6b4cff908fb)

The first filter, `department = ‘Marketing’` reduces the search to a specific department from the column, and `office = LIKE ‘East%’` returns results only from the relevant East office building where the devices are located. 

## Retrieve Employees in Finance or Sales

A separate security task requires a security update for employees in the Finance and Sales departments. So to search for the machines belonging to employees in that department, the following query was used.

![5](https://github.com/RafUrera/Applying-Filters-to-SQL-Queries/assets/161657613/52679004-c752-4a22-8d58-166614ccec14)

There are two filters in this query that simply bring back results from the finance and sales departments.  The `OR` operator allows the results to have just one of the two conditions be true instead of both at the same time.

## Retrieve All Employees Not in IT

The final task involves a final security update to employee machines. The employees in the Information Technology department have already updated their machines. So this update is to be done for all other employees. 

![6](https://github.com/RafUrera/Applying-Filters-to-SQL-Queries/assets/161657613/e185aff4-d6a2-454b-8b7e-8b6a97621358)

The query done here is to simply exclude the IT department from the search results. By using the `NOT` operator the following `department = ‘Information Technology’` filter is excluded in the returning results. 

## Summary

Multiple tasks were completed using SQL queries, such as investigating a login-related security incident and knowing which machines needed security updates. These SQL queries used various filters and operators such as `OR`, `NOT`, and `LIKE`, in order to refine results to only necessary information.
