# Exercise 7.6

**Author:** *Gilberto Diaz*

**Professor:** *Dr. Jordon Shaw*

**Course:** *MSSE 5123*

Specify the following queries in `SQL` on the database schema in Figure 1.2.

1. Retrieve the names and major departments of all straight A's students. (students who hae a grade of A in all their courses)

```sql
SELECT S.Name, S.Major FROM STUDENT S
    WHERE NOT EXISTS(
        SELECT * FROM GRADE_REPORT G
            WHERE G.Student_number = S.Student_number AND NOT G.GRADE = 'A')
```

It should return zero results.

2. Retrieve the names and major departments of all students who do not have a grade of A in any of their courses.

```sql
SELECT S.Name, S.Major FROM STUDENT S
    WHERE NOT EXISTS(
        SELECT * FROM GRADE_REPORT G
            WHERE G.Student_number = S.Student_number AND G.GRADE = 'A')
```

Name|Major
----|----
Smith|CS
