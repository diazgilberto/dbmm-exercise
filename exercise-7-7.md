# Exercise 7.7

**Author:** *Gilberto Diaz*

**Professor:** *Dr. Jordon Shaw*

**Course:** *MSSE 5123*

In `SQL`, specify the following queries on the database in Figure 5.5 using the concept of nested queries and other concepts described in this chapter.

1. Retrieve the names of all employees who work in the department that has the employee with the highest salary among all employees.

```sql
SELECT Fname, Lname FROM EMPLOYEE
    WHERE E.Dno = (
        SELECT Dno FROM EMPLOYEE
            WHERE Salary = (
                SELECT MAX(Salary) FROM EMPLOYEE
            )
    )
```

2. Retrieve the names of all employees whose supervisor's supervisor has `'888665555'` for `Ssn`.

```sql
SELECT Lname FROM EMPLOYEE WHERE Super_ssn IN (
    SELECT Snn FROM EMPLOYEE WHERE Super_snn = '888665555'
)
```

3. Retrieve the names of employees who make at least $10,000 more than the employee who is paid the least in the company.

```sql
SELECT Lname FROM EMPLOYEE WHERE Salary > 10000 + (
    SELECT MIN(Salary) FROM EMPLOYEE
)
```
