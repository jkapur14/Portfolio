Airline Reservation Database
Overview

This is a SQL-based Airline Reservation Database that simulates airline operations, including managing passengers, staff, flights, reservations, payments, and airports. It demonstrates relational database design, constraints, and advanced SQL queries for reporting and analysis.

Features

Relational database with 9 tables: Person, Staff, Passenger, Airport, Aircraft, Flight, Reservation, Payment, Flight_Staff.

Maintains data integrity using primary keys, foreign keys, and constraints.

Sample data included for testing.

Example queries for:

Total revenue per flight

Passenger spending rankings

Staff assignments and staffing status

Searching passengers by last name, flight number, and seat

Database Schema

Person – Base table for all people

Staff – Employees linked to Person

Passenger – Passengers linked to Person

Airport – Airport details

Aircraft – Aircraft information

Flight – Flight schedules linked to airports and aircraft

Reservation – Booking information

Payment – Payment details linked to reservations

Flight_Staff – Staff assignments for flights

Setup

Clone the repository.

Open your SQL environment (Oracle SQL Developer, SQL*Plus, etc.).

Run ddl.sql to create tables.

Run data.sql to insert sample data.

Run queries.sql to test example queries.

Sample Queries

Total Revenue by Flight

SELECT f.FlightNUM, COUNT(r.ReservationID) AS Total_Passengers,
       SUM(NVL(r.Price,0)) AS Total_Revenue
FROM Reservation r
JOIN Flight f ON f.FlightID = r.FlightID
WHERE r.Status = 'Confirmed'
GROUP BY f.FlightNUM
ORDER BY Total_Revenue DESC;

Passenger Spending Rankings

SELECT p.FirstName || ' ' || p.LastName AS Passenger_Name,
       SUM(NVL(r.Price,0)) AS Total_Spent,
       RANK() OVER (ORDER BY SUM(NVL(r.Price,0)) DESC) AS Spend_Rank
FROM Reservation r
JOIN Passenger pa ON pa.PersonID = r.PassengerID
JOIN Person p ON p.PersonID = pa.PersonID
WHERE r.Status = 'Confirmed'
GROUP BY p.FirstName, p.LastName
ORDER BY Total_Spent DESC;

Staff Assigned to Each Flight

SELECT f.FlightNUM, a1.Code AS Origin, a2.Code AS Destination,
       LISTAGG(s.Role || ' (' || fs.Duty || ')', ', ') WITHIN GROUP (ORDER BY s.Role) AS Staff_Assigned,
       COUNT(fs.StaffID) AS Total_Staff,
       CASE WHEN COUNT(fs.StaffID) < 3 THEN 'Understaffed' ELSE 'Adequately Staffed' END AS Staffing_Status
FROM Flight f
JOIN Airport a1 ON a1.AirportID = f.OriginAirportID
JOIN Airport a2 ON a2.AirportID = f.DestinationAirportID
JOIN Flight_Staff fs ON fs.FlightID = f.FlightID
JOIN Staff s ON s.PersonID = fs.StaffID
GROUP BY f.FlightNUM, a1.Code, a2.Code
ORDER BY f.FlightNUM;

Author
Jatin Kapur
