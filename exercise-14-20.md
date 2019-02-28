# Exercise 14.20

**Author:** *Gilberto Diaz*

**Professor:** *Dr. Jordon Shaw*

**Course:** *MSSE 5123*

What update anomalies occur in the `EMP_PROJ` and `EMP_DEPT` relations of Figures 14.3 and 14.4?

In `EMP_DEPT`:

- Insertion Anomalies - If we try to inset a new employee and that employee doesn't work for a department just yet, we must set the `Dnumber`, `Dname` to `NULL`. The same happens with the manager.
- Deletion Anomalies - If one delete an employee the `EMP_PROJ` gets affected since `Ssn` is the `PRIMARY KEY` in the table.
- Modification Anomalies - Since the employee's name is in the `EMP_PROJ` as well their is a change to have inconsistency in the data. Updating the name has to be done in two table which make code to start been unmanageable.

In `EMP_PROJ`:

- Insertion Anomalies - We can't create a new project without an employee since `Ssn` is a `PRIMARY KEY` in the table. `EMP_PROJ` should have its own `PRIMARY KEY` and create a new table to link employees to a project.
- Deletion Anomalies - For deleting a project one has to find all the people that are assigned to that project and hoping that `Pnumber` are all the same.
- Modification Anomalies - Since employee's name is in two table, once again, the update has to be done twice. Updating the name in two tables increases the chance of data inconsistency 
