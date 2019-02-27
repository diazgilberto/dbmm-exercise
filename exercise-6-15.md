# Exercise 6.15

**Author:** *Gilberto Diaz*

**Professor:** *Dr. Jordon Shaw*

**Course:** *MSSE 5123*

Consider that the `EMPLOYEE` table's constraint `EMPSUPERFK` as specified in Figure 6.2 is changed to read as follows:

```sql
CONSTRAINT EMPSUPERFK
    FOREIGN KEY (Super_snn)
        REFERENCES EMPLOYEE (Ssn)
            ON DELETE CASCADE ON UPDATE CASCADE
```

Answer the following questions:
1. What happens when the following command is run on the database state shown in Figure 5.6?
```sql
DELETE EMPLOYEE WHERE Lname = 'Borg'
```
All 8 rows from the `EMPLOYEE` table got deleted.

2. Is it better to `CASCADE` or `SET NULL` in case of `EMPSUPERFK` constraint `ON DELETE`?
Yes, it is better to `SET NULL`, since an employee is not deleted when their supervisor is deleted.
