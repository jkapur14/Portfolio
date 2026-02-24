-- AIRLINE RESERVATION DATABASE DDL

-- PERSON TABLE
CREATE TABLE Person (
    PersonID NUMBER PRIMARY KEY,
    FirstName VARCHAR2(100),
    LastName VARCHAR2(100),
    DOB DATE,
    Address VARCHAR2(150),
    Email VARCHAR2(100),
    PhoneNumber VARCHAR2(15)
);

-- STAFF TABLE
CREATE TABLE Staff (
    PersonID NUMBER PRIMARY KEY,
    Role VARCHAR2(50),
    Department VARCHAR2(50),
    HireDate DATE,
    Salary NUMBER(10,2),
    FOREIGN KEY (PersonID) REFERENCES Person(PersonID)
);

-- PASSENGER TABLE
CREATE TABLE Passenger (
    PersonID NUMBER PRIMARY KEY,
    FrequentFlyerNUM VARCHAR2(20),
    PassengerNUM VARCHAR2(20),
    FOREIGN KEY (PersonID) REFERENCES Person(PersonID)
);

-- AIRPORT TABLE
CREATE TABLE Airport (
    AirportID NUMBER PRIMARY KEY,
    Code VARCHAR2(10),
    Name VARCHAR2(100),
    City VARCHAR2(50),
    Country VARCHAR2(50)
);

-- AIRCRAFT TABLE
CREATE TABLE Aircraft (
    AircraftID NUMBER PRIMARY KEY,
    RegistrationNUM VARCHAR2(20),
    Model VARCHAR2(50),
    Capacity NUMBER
);

-- FLIGHT TABLE
CREATE TABLE Flight (
    FlightID NUMBER PRIMARY KEY,
    FlightNUM VARCHAR2(10),
    DestinationAirportID NUMBER,
    OriginAirportID NUMBER,
    AircraftID NUMBER,
    DepartureTime TIMESTAMP,
    ArrivalTime TIMESTAMP,
    Status VARCHAR2(20),
    FOREIGN KEY (DestinationAirportID) REFERENCES Airport(AirportID),
    FOREIGN KEY (OriginAirportID) REFERENCES Airport(AirportID),
    FOREIGN KEY (AircraftID) REFERENCES Aircraft(AircraftID)
);

-- RESERVATION TABLE
CREATE TABLE Reservation (
    ReservationID NUMBER PRIMARY KEY,
    PassengerID NUMBER,
    FlightID NUMBER,
    BookingDate DATE,
    Status VARCHAR2(20),
    SeatNumber VARCHAR2(5),
    TravelClass VARCHAR2(20),
    Price NUMBER(10,2),
    FOREIGN KEY (PassengerID) REFERENCES Passenger(PersonID),
    FOREIGN KEY (FlightID) REFERENCES Flight(FlightID)
);

-- PAYMENT TABLE
CREATE TABLE Payment (
    PaymentID NUMBER PRIMARY KEY,
    ReservationID NUMBER,
    Amount NUMBER(10,2),
    PaymentDate DATE,
    Method VARCHAR2(20),
    PaymentStatus VARCHAR2(20),
    FOREIGN KEY (ReservationID) REFERENCES Reservation(ReservationID)
);

-- FLIGHT_STAFF TABLE
CREATE TABLE Flight_Staff (
    StaffID NUMBER,
    FlightID NUMBER,
    Duty VARCHAR2(50),
    PRIMARY KEY (StaffID, FlightID),
    FOREIGN KEY (StaffID) REFERENCES Staff(PersonID),
    FOREIGN KEY (FlightID) REFERENCES Flight(FlightID)
);
-- PERSON DATA
INSERT INTO Person VALUES (1, 'John', 'Smith', DATE '1985-04-10', '123 Main St', 'john.smith@email.com', '555-1001');
INSERT INTO Person VALUES (2, 'Emily', 'Johnson', DATE '1990-07-22', '45 West Ave', 'emily.johnson@email.com', '555-1002');
INSERT INTO Person VALUES (3, 'Michael', 'Brown', DATE '1975-02-14', '980 Lake Rd', 'michael.brown@email.com', '555-1003');
INSERT INTO Person VALUES (4, 'Sarah', 'Lee', DATE '1992-12-05', '67 Oak St', 'sarah.lee@email.com', '555-1004');
INSERT INTO Person VALUES (5, 'James', 'Taylor', DATE '1988-06-30', '321 Pine Rd', 'james.taylor@email.com', '555-1005');

-- Staff
INSERT INTO Person VALUES (6, 'Anna', 'White', DATE '1980-01-15', '72 Elm St', 'anna.white@email.com', '555-2001');
INSERT INTO Person VALUES (7, 'David', 'Green', DATE '1978-03-25', '88 North St', 'david.green@email.com', '555-2002');
INSERT INTO Person VALUES (8, 'Linda', 'Hall', DATE '1983-09-12', '10 Brookside', 'linda.hall@email.com', '555-2003');
INSERT INTO Person VALUES (9, 'Robert', 'Adams', DATE '1970-11-11', '9 Park Ave', 'robert.adams@email.com', '555-2004');
INSERT INTO Person VALUES (10, 'Karen', 'Davis', DATE '1995-08-23', '59 River Rd', 'karen.davis@email.com', '555-2005');

INSERT INTO Staff VALUES (6, 'Pilot', 'Flight Ops', DATE '2010-05-20', 120000);
INSERT INTO Staff VALUES (7, 'Co-Pilot', 'Flight Ops', DATE '2012-03-10', 95000);
INSERT INTO Staff VALUES (8, 'Flight Attendant', 'Cabin Crew', DATE '2015-08-18', 55000);
INSERT INTO Staff VALUES (9, 'Flight Attendant', 'Cabin Crew', DATE '2017-01-08', 52000);
INSERT INTO Staff VALUES (10, 'Ground Staff', 'Operations', DATE '2019-06-30', 45000);

INSERT INTO Passenger VALUES (1, 'FF12345', 'PS001');
INSERT INTO Passenger VALUES (2, 'FF54321', 'PS002');
INSERT INTO Passenger VALUES (3, 'FF99887', 'PS003');
INSERT INTO Passenger VALUES (4, 'FF66554', 'PS004');
INSERT INTO Passenger VALUES (5, 'FF22119', 'PS005');

INSERT INTO Airport VALUES (1, 'JFK', 'John F. Kennedy Intl', 'New York', 'USA');
INSERT INTO Airport VALUES (2, 'LAX', 'Los Angeles Intl', 'Los Angeles', 'USA');
INSERT INTO Airport VALUES (3, 'ORD', 'O’Hare Intl', 'Chicago', 'USA');
INSERT INTO Airport VALUES (4, 'DFW', 'Dallas/Fort Worth Intl', 'Dallas', 'USA');
INSERT INTO Airport VALUES (5, 'ATL', 'Hartsfield–Jackson', 'Atlanta', 'USA');

INSERT INTO Aircraft VALUES (1, 'N123AA', 'Boeing 737', 160);
INSERT INTO Aircraft VALUES (2, 'N456BB', 'Airbus A320', 150);
INSERT INTO Aircraft VALUES (3, 'N789CC', 'Boeing 777', 300);

INSERT INTO Flight VALUES (1, 'AA101', 2, 1, 1, 
    TIMESTAMP '2025-03-12 08:00:00', TIMESTAMP '2025-03-12 11:15:00', 'On Time');

INSERT INTO Flight VALUES (2, 'AA202', 3, 1, 2, 
    TIMESTAMP '2025-03-13 09:30:00', TIMESTAMP '2025-03-13 12:00:00', 'Delayed');

INSERT INTO Flight VALUES (3, 'AA303', 1, 2, 3, 
    TIMESTAMP '2025-03-15 16:00:00', TIMESTAMP '2025-03-15 20:30:00', 'Cancelled');

INSERT INTO Reservation VALUES (1, 1, 1, DATE '2025-02-20', 'Confirmed', '12A', 'Economy', 350.00);
INSERT INTO Reservation VALUES (2, 2, 1, DATE '2025-02-22', 'Confirmed', '14C', 'Economy', 350.00);
INSERT INTO Reservation VALUES (3, 3, 2, DATE '2025-02-28', 'Pending', '10B', 'Business', 1200.00);
INSERT INTO Reservation VALUES (4, 4, 2, DATE '2025-03-01', 'Cancelled', '22D', 'Economy', 350.00);
INSERT INTO Reservation VALUES (5, 5, 3, DATE '2025-03-02', 'Confirmed', '02A', 'First', 2500.00);

INSERT INTO Payment VALUES (1, 1, 350.00, DATE '2025-02-20', 'Card', 'Completed');
INSERT INTO Payment VALUES (2, 2, 350.00, DATE '2025-02-22', 'Card', 'Completed');
INSERT INTO Payment VALUES (3, 3, 1200.00, DATE '2025-02-28', 'PayPal', 'Pending');
INSERT INTO Payment VALUES (4, 5, 2500.00, DATE '2025-03-02', 'Card', 'Completed');

INSERT INTO Flight_Staff VALUES (6, 1, 'Pilot');
INSERT INTO Flight_Staff VALUES (7, 1, 'Co-Pilot');
INSERT INTO Flight_Staff VALUES (8, 1, 'Cabin Crew');
INSERT INTO Flight_Staff VALUES (9, 2, 'Cabin Crew');
INSERT INTO Flight_Staff VALUES (10, 3, 'Ground Support');

SELECT * FROM Person;
SELECT * FROM Staff;
SELECT * FROM Passenger;
SELECT * FROM Airport;
SELECT * FROM Flight;
SELECT * FROM Reservation;
SELECT * FROM Payment;
SELECT * FROM Flight_Staff;

/*GP4

/* Query 1: Total Revenue by Flight */

SELECT
    f.FlightNUM,
    COUNT(r.ReservationID) AS Total_Passengers,
    SUM(NVL(r.Price, 0)) AS Total_Revenue
FROM Reservation r
JOIN Flight f ON f.FlightID = r.FlightID
WHERE r.Status = 'Confirmed'
GROUP BY f.FlightNUM
HAVING SUM(NVL(r.Price, 0)) > 0
ORDER BY Total_Revenue DESC;

/* Query 2: Rank Passengers by Total Spending */

SELECT
    p.FirstName || ' ' || p.LastName AS Passenger_Name,
    SUM(NVL(r.Price, 0)) AS Total_Spent,
    RANK() OVER (ORDER BY SUM(NVL(r.Price, 0)) DESC) AS Spend_Rank
FROM Reservation r
JOIN Passenger pa ON pa.PersonID = r.PassengerID
JOIN Person p ON p.PersonID = pa.PersonID
WHERE r.Status = 'Confirmed'
GROUP BY p.FirstName, p.LastName
ORDER BY Total_Spent DESC;

/* Query 3: List all staff assigned to each flight */

SELECT
    f.FlightNUM,
    a1.Code AS Origin,
    a2.Code AS Destination,
    LISTAGG(s.Role || ' (' || fs.Duty || ')', ', ') WITHIN GROUP (ORDER BY s.Role) AS Staff_Assigned,
    COUNT(fs.StaffID) AS Total_Staff,
    CASE 
        WHEN COUNT(fs.StaffID) < 3 THEN 'Understaffed'
        ELSE 'Adequately Staffed'
    END AS Staffing_Status
FROM Flight f
JOIN Airport a1 ON a1.AirportID = f.OriginAirportID
JOIN Airport a2 ON a2.AirportID = f.DestinationAirportID
JOIN Flight_Staff fs ON fs.FlightID = f.FlightID
JOIN Staff s ON s.PersonID = fs.StaffID
GROUP BY f.FlightNUM, a1.Code, a2.Code
ORDER BY f.FlightNUM;

/* Query 4: Find flight passenger using last name, seat number and flight number*/

SELECT 
    P.PersonID,
    P.FirstName,
    P.LastName,
    R.ReservationID,
    F.FlightNUM,
    R.SeatNumber,
    R.TravelClass,
    F.DepartureTime,
    F.ArrivalTime
FROM Person P
JOIN Passenger Pa ON P.PersonID = Pa.PersonID
JOIN Reservation R ON Pa.PersonID = R.PassengerID
JOIN Flight F ON R.FlightID = F.FlightID
WHERE LOWER(P.LastName) LIKE LOWER('%smith%')   -- case-insensitive last name
  AND LOWER(F.FlightNUM) = LOWER('aa101')      -- case-insensitive flight number
  AND LOWER(R.SeatNumber) = LOWER('12a');
