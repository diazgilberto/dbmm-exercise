# Exercise 6.12

**Author:** *Gilberto Diaz*

**Professor:** *Dr. Jordon Shaw*

**Course:** *MSSE 5123*

Specify the following queries in `SQL` on the database schema of Figure 1.2.

1. Retrieve the names of all senior students majoring in `CS`.

```sql
SELECT Name FROM STUDENT 
    WHERE Major = 'CS'
    AND Class = '4';
```

1. Retrieve the names of all courses taught by Professor King in 2007 and 2008.

```sql
SELECT Course_name FROM COURSE C, SECTION S
    WHERE C.Course_number = S.Course_number
        AND Instructor = 'King'
        AND (Year = '07' or Year = '08') 
```

1. For each section taught by Professor King, retrieve the course number, semester, year, and number of students who took the section.

```sql
SELECT Course_number, Semester, Year, COUNT(G.Student_number) FROM SECTION S, GRADE_REPORT G
    WHERE S.Instructor = 'King' AND S.Section_identifier = G.Section_identifier
        GROUP BY Course_number, Semester, Year;
```

1. Retrieve the name and transcript of each senior student (Class = 4) majoring in `CS`. A transcript includes course name, course number, credit hours, semester, year, and grade for each course completed by the student.

```sql
SELECT S.Name, C.Course_name, C.Course_number, C.Credit_hours, S.Semester, S.Year, G.Grade FROM
    STUDENT S, COURSE C, SECTION S, GRADE_REPORT G
        WHERE Class = '4' AND Major = 'CS'
            AND S.Student_number = G.Student_number AND G.Section_identifier = S.Section_identifier
            AND S.Course_number = C.Course_number
```
