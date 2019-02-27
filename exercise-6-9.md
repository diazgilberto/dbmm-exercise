# Exercise 6.p
**Author:** *Gilberto Diaz*

**Professor:** *Dr. Jordon Shaw*

**Course:** *MSSE 5123*

- How can the key and foreign key constraints be enforced by the DBMS?
    - The DBMS default action for the key and foreign key constraint is to reject the update and delete operation that will cause a violation, which is known as RESTRICT. 
- Is the enforcement technique you suggest difficult to implement?
    - No, to the enforcement the technique one just has to defined PK and FK as needed.
- Can the constraint checks be executed efficiently when updates are applied to the database?
    - In some cases could hurt efficiency since the DBMS needs to check the constraint to avoid duplicate tuples in the table.
