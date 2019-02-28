# Exercise 7.5

**Author:** *Gilberto Diaz*

**Professor:** *Dr. Jordon Shaw*

**Course:** *MSSE 5123*

Specify the following queries on the database in Figure 5.5 in `SQL`. Show the query results if each query is applied to the database state in Figure 5.6.

1. For each department whose average employee salary is more than $30,000, retrieve the department name and the number of employees working for that department.

```sql
SELECT D.DName, COUNT(*) FROM DEPARTMENT D, EMPLOYEE E
    WHERE E.Dnumber = E.Dno
        HAVING AVG(E.Salary) > 30000
```

Dname|Dnumber|Count(*)
----|----|----
Research|5|4
Administration|4|3
Headquaters|1|1

2. Suppose that we want the number of male employees in each department making more than $30,000, rather than all employees (as in Exercise 7.5a). Can we specify this query in `SQL`? Why or why not?

Yes we can. Since the `EMPLOYEE` table has the field `Sex` we can add a condition for `Sex = 'M'`.
