# Exercise 6.7

**Author:** *Gilberto Diaz*

**Professor:** *Dr. Jordon Shaw*

**Course:** *MSSE 5123*

Consider the LIBRARY relational database schema shown in *Figure 6.6*. Choose the appropriate action (reject, cascade, set to `NULL`, set to default) for each referential integrity constraint, both for the *deletion* of the referenced tuple and for the *update* of a primary key attribute value in a referenced tuple. Justify your choice.

Table|Field|Action|Reason
----|----|----|---
`PUBLISHER`|`NAME`|`ON UPDATE CASCADE`|I want to update the publisher name in the `BOOK` table every time it changes.
`PUBLISHER`|`NAME`|`ON DELETE SET NULL`|I want to set to `NULL` the publisher name and wait until a new publisher name is asigned.

For the rest of the `FK` I will do `ON UPDATE CASCADE` and `ON DELETE NO ACTION` since the rest of `FK` are `AUTO_INCREMENT` `PK`s in another table.

