# Exercise 6.6
**Author:** *Gilberto Diaz*

**Profesor:** *Dr. Jordon Shaw*

**Course:** *MSSE 5123*
<br>

Repeat Exercise 6.5, but use the AIRLINE database schema of Figure 5.8.

*Question 6.5*
> Consider the database shown in Figure 1.2, whose schema is shown in Figure 2.1. What are the referential integrity constraints that should hold on the schema? Write appropriate SQL DDL statements to define the database.

```sql

CREATE DATABASE IF NOT EXISTS airline;
USE airline;

/*---------- AIRLINE DB ---------*/
 
CREATE TABLE AIRPORT (
	Airport_code INTEGER(11) PRIMARY KEY AUTO_INCREMENT,
	Name VARCHAR(64),
	City VARCHAR(32),
	State VARCHAR(2)
);

CREATE TABLE FLIGHT (
	Flight_number INTEGER(11) PRIMARY KEY AUTO_INCREMENT,
	Airline VARCHAR(128),
	Weekdays VARCHAR(1)
);

CREATE TABLE FLIGHT_LEG (
	Leg_number INTEGER(11) PRIMARY KEY AUTO_INCREMENT,
	Departure_airport_code VARCHAR(32),
	Schedule_departure_time DATETIME,
	Arrival_airport_code VARCHAR(32),
	Schedule_arrival_time DATETIME,
	Flight_number INTEGER(11),
	FOREIGN KEY (Flight_number)
		REFERENCES FLIGHT (Flight_number)
);

CREATE TABLE AIRPLANE (
	Airplane_id INTEGER(11) PRIMARY KEY AUTO_INCREMENT,
	Total_number_of_seats INTEGER,
	Airplane_type VARCHAR(16)
);

CREATE TABLE LEG_INSTANCE (
	Flight_number INTEGER(11),
	Leg_number INTEGER(11),
	Leg_instance_date DATETIME,
	Number_of_available_seats INTEGER(3),
	Airplane_id INTEGER(11),
	Departure_time DATETIME,
	Arrival_time DATETIME,
	PRIMARY KEY (Flight_number, Leg_number),
	FOREIGN KEY (Flight_number)
		REFERENCES FLIGHT (Flight_number),
	FOREIGN KEY (Leg_number)
		REFERENCES FLIGHT_LEG (Leg_number),
	FOREIGN KEY (Airplane_id)
		REFERENCES AIRPLANE (Airplane_id)
);

CREATE TABLE FARE (
	Fare_code INTEGER(11) PRIMARY KEY AUTO_INCREMENT,
	Flight_number INTEGER(11),
	Amount DECIMAL(15, 2),
	Restrictions VARCHAR(128)
);

CREATE TABLE AIRPLANE_TYPE (
	Airplane_type_name_number INTEGER(11) PRIMARY KEY AUTO_INCREMENT,
	Airplane_type_name VARCHAR(64),
	Max_seats INTEGER(32),
	Company VARCHAR(64)
);

CREATE TABLE CAN_LAND (
	Airplane_type_name_number INTEGER(11),
	Airport_code INTEGER(11),
	PRIMARY KEY (Airplane_type_name_number, Airport_code),
	FOREIGN KEY (Airplane_type_name_number)
		REFERENCES AIRPLANE_TYPE (Airplane_type_name_number),
	FOREIGN KEY (Airport_code)
		REFERENCES AIRPORT (Airport_code)
);

CREATE TABLE SEAT_RESERVATION (
	Flight_number INTEGER(11),
	Leg_number INTEGER(11),
	Reservation_date DATETIME,
	Seat_number VARCHAR(5),
	Customer_name VARCHAR(64),
	Customer_phone VARCHAR(15),
	PRIMARY KEY (Flight_number, Leg_number),
	FOREIGN KEY (Flight_number)
		REFERENCES FLIGHT (Flight_number),
	FOREIGN KEY (Leg_number)
		REFERENCES FLIGHT_LEG (Leg_number)
);


```
