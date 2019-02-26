# Exercise 6.8
**Author:** *Gilberto Diaz*

**Profesor:** *Dr. Jordon Shaw*

**Course:** *MSSE 5123*

Write appropriate `SQL` statements for declaring the `LIBRARY` relational database schema of Figure 6.6. Specify the keys and referential triggered actions.
<br>

```sql
CREATE DATABASE IF NOT EXISTS library;
USE library;

/*---------- LIBRARY DB ---------*/
 
CREATE TABLE PUBLISHER (
	Publisher_id INTEGER(11) PRIMARY KEY AUTO_INCREMENT,
	Publisher_name VARCHAR(64),
	Phone VARCHAR(15)
);

CREATE TABLE BOOK (
	Book_id INTEGER(11) PRIMARY KEY AUTO_INCREMENT,
	Title VARCHAR(128),
	Publisher_id INTEGER(11),
	FOREIGN KEY (Publisher_id)
		REFERENCES PUBLISHER (Publisher_id)
);

CREATE TABLE BOOK_AUTHOR (
	Book_author_id INTEGER(11) PRIMARY KEY AUTO_INCREMENT,
	Book_id INTEGER(11),
	Author_name VARCHAR(32),
	FOREIGN KEY (Book_id)
		REFERENCES BOOK (Book_id)
);

CREATE TABLE LIBRARY_BRANCH (
	Branch_id INTEGER(11) PRIMARY KEY AUTO_INCREMENT,
	Branch_name VARCHAR(64),
	Address VARCHAR(128)
);

CREATE TABLE BOOK_COPIES (
	Book_copies_id INTEGER(11) PRIMARY KEY AUTO_INCREMENT,
	Book_id INTEGER(11),
	Branch_id INTEGER(11),
	No_of_copies INTEGER(11),
	FOREIGN KEY (Book_id)
		REFERENCES BOOK (Book_id),
	FOREIGN KEY (Branch_id)
		REFERENCES LIBRARY_BRANCH (Branch_id)
);

CREATE TABLE BORROWER (
	Borrower_id INTEGER(11) PRIMARY KEY AUTO_INCREMENT,
	Card_no INTEGER(11),
	Barrower_name VARCHAR(32),
	Address VARCHAR(128),
	Phone VARCHAR(15)
);

CREATE TABLE BOOK_LOANS (
	Book_loans_id INTEGER(11) PRIMARY KEY AUTO_INCREMENT,
	Book_id INTEGER(11),
 	Branch_id INTEGER(11),
  	Borrower_id INTEGER(11),
	Date_out DATETIME,
	Due_date DATETIME,
	FOREIGN KEY (Book_id)
		REFERENCES BOOK (Book_id),
 	FOREIGN KEY (Branch_id)
		REFERENCES LIBRARY_BRANCH (Branch_id),
	FOREIGN KEY (Borrower_id)
		REFERENCES BORROWER (Borrower_id)
);
```
