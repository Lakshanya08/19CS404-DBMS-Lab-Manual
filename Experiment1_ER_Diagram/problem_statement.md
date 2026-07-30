
# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:
<img width="940" height="526" alt="image" src="https://github.com/user-attachments/assets/566a33b4-7233-4ba6-8600-1c04900b7af8" />



### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|----------------------|-------|
| **Member** | **Member_ID (PK)**, Name, Membership_type, Start_date | Stores details of gym members. |
| **Program** | **Program_ID (PK)**, Program_name, Category, Duration | Stores information about fitness programs. |
| **Trainer** | **Trainer_ID (PK)**, Name, Qualification, Experience, Phone_no | Stores trainer information. |
| **Session** | **Session_ID (PK)**, Session_date, Session_time, Duration, **Trainer_ID (FK)** | Represents training sessions conducted by trainers. |
| **Attendance** | **Attendance_ID (PK)**, Status, In_time, Remarks, **Session_ID (FK)** | Stores attendance details for each session. |
| **Payment** | **Payment_ID (PK)**, Amount, Payment_date, Payment_method, **Member_ID (FK)** | Stores payment records made by members. |
### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|-------------|----------------|-------|
| **Joins** (Member – Program) | M : N | Partial | A member can join multiple programs, and each program can have many members. |
| **Assigned_to** (Program – Trainer) | M : N | Partial | Multiple trainers can teach multiple programs. |
| **Books** (Member – Session) | 1 : N | Total on Session | One member can book many sessions, while each session is booked by one member. |
| **Conducts** (Trainer – Session) | 1 : N | Total on Session | One trainer conducts many sessions, and every session is conducted by one trainer. |
| **Makes** (Member – Payment) | 1 : N | Total on Payment | A member can make many payments, and each payment belongs to one member. |
| **Has** (Session – Attendance) | 1 : 1 | Total | Every session has one attendance record, and every attendance record belongs to one session. |
### Assumptions

1.	Every Member has a unique Member_ID. 
2.	Every Program has a unique Program_ID. 
3.	Every Trainer has a unique Trainer_ID. 
4.	Every Session has a unique Session_ID. 
5.	Every Attendance record has a unique Attendance_ID. 
6.	Every Payment has a unique Payment_ID. 
7.	A member can enroll in multiple fitness programs. 
8.	A fitness program can have multiple members. 
9.	A trainer can be assigned to multiple programs. 
10.	A program can have multiple trainers. 
11.	Each session is conducted by exactly one trainer. 
12.	A trainer may conduct many sessions. 
13.	A member can book multiple sessions. 
14.	Each payment is made by only one member. 
15.	A member may make multiple payments during their membership


---

# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:

<img width="940" height="610" alt="image" src="https://github.com/user-attachments/assets/5489e6b8-e1e9-4b85-bbc5-e4157664d132" />



### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|----------------------|-------|
| **Member** | **Member_ID (PK)**, Name, Email, Phone_no | Stores library member details. |
| **Book** | **Book_ID (PK)**, Title, Author, Category | Stores information about books available in the library. |
| **Loan_Record** | **Loan_ID (PK)**, Loan_date, Due_date, Return_date, **Member_ID (FK)**, **Book_ID (FK)** | Records book borrowing transactions. |
| **Fine** | **Fine_ID (PK)**, Amount, Fine_date, Payment_status, **Loan_ID (FK)** | Stores fines generated for overdue books. |
| **Event** | **Event_ID (PK)**, Event_name, Event_date, Duration, Description | Stores details of library events. |
| **Speaker** | **Speaker_ID (PK)**, Speaker_name, Bio | Stores details of guest speakers. |
| **Room** | **Room_ID (PK)**, Room_name, Capacity, Location | Stores information about library rooms used for events and reservations. |
### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|-------------|----------------|-------|
| **Borrows** (Member – Loan_Record) | 1 : N | Total on Loan_Record | A member can borrow many books, while each loan record belongs to one member. |
| **For** (Loan_Record – Book) | N : 1 | Total on Loan_Record | Each loan record is for one book, while a book can appear in many loan records over time. |
| **Generates** (Loan_Record – Fine) | 1 : N | Partial | A loan may generate one or more fines if returned late; some loans generate no fine. |
| **Registers** (Member – Event) | M : N | Partial | Members can register for multiple events, and each event can have many members. |
| **Features** (Event – Speaker) | M : N | Partial | An event may feature multiple speakers, and a speaker may participate in multiple events. |
| **Hosts** (Room – Event) | 1 : N | Total on Event | One room can host many events, while each event is hosted in one room. |
| **Reserves** (Member – Room) | N : 1 | Partial | A member can reserve multiple rooms, while a room can be reserved by different members at different times. |


### Assumptions
1.	Every member has a unique Member_ID. 
2.	Every book has a unique Book_ID. 
3.	A member can borrow multiple books, but each loan record belongs to only one member. 
4.	A book can be borrowed many times, but only through different loan records. 
5.	A fine is generated only if a book is returned after its due date. 
6.	A member can register for multiple events, and an event can have multiple members. 
7.	An event can feature multiple speakers, and a speaker can participate in multiple events. 
8.	Every event is hosted in one room, while a room can host many events at different times. 
9.	A member can reserve rooms based on availability, and a room cannot have overlapping reservations. 
10.	All loan, fine, event, and reservation records are maintained in the database for future reference and reporting. 

---

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:

<img width="940" height="616" alt="image" src="https://github.com/user-attachments/assets/7dbc4f16-88ac-45ac-a1ae-d52f0901c5b1" />


### Entities and Attributes


| **Entity**      | **Attributes (PK, FK)**                                                   | **Notes**                                                                          |
| --------------- | ------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| **Customer**    | **Customer_ID (PK)**, Name, Phone_No, Email                               | Stores customer information.                                                       |
| **Reservation** | **Reservation_ID (PK)**, Reservation_Date, Reservation_Time, No_of_Guests | Stores reservation details.                                                        |
| **Order**       | **Order_ID (PK)**, Order_Time, No_of_Orders, Specifications               | Stores customer food orders.                                                       |
| **Dish**        | **Dish_Name (PK)**, Price, Calories, Availability_Status                  | Stores menu item details. |
| **Bill**        | **Bill_ID (PK)**, Food_Charge, Service_Charge, Discount, Total_Amount     | Stores billing information.                                                        |
| **Waiter**      | **Waiter_ID (PK)**, Waiter_Name, Phone_No, Shift                          | Stores waiter details.                                                             |

### Relationships and Constraints


| **Relationship**               | **Cardinality** | **Participation**                       | **Notes**                                                                           |
| ------------------------------ | --------------- | --------------------------------------- | ----------------------------------------------------------------------------------- |
| Customer **Makes** Reservation | **1 : N**       | Total (Reservation), Partial (Customer) | One customer can make many reservations. Every reservation belongs to one customer. |
| Reservation **Places** Order   | **1 : N**       | Total                                   | One reservation may have multiple food orders.                                      |
| Order **Contains** Dish        | **M : N**       | Total                                   | An order contains many dishes, and a dish can appear in many orders.                |
| Reservation **Generates** Bill | **1 : 1**       | Total                                   | Each reservation generates exactly one bill.                                        |
| Waiter **Serves** Bill         | **1 : N**       | Partial (Waiter), Total (Bill)          | One waiter can serve many bills, but each bill is handled by one waiter.            |

### Assumptions

1.	Every customer has a unique Customer_ID. 
2.	A customer can make multiple reservations, but each reservation belongs to only one customer. 
3.	Each reservation is identified by a unique Reservation_ID. 
4.	A reservation can have one or more food orders. 
5.	An order may contain multiple dishes, and the same dish can appear in multiple orders. 
6.	Every dish has a unique Dish_Name and belongs to a restaurant menu. 
7.	One bill is generated for each reservation. 
8.	Each bill includes food charges, service charges, and any applicable discount. 
9.	One waiter can serve many bills/reservations, but each bill is handled by only one waiter.

### Result

The ER diagrams for the City Fitness Club Management System, City Library Event & Book Lending System, and Restaurant Table Reservation & Ordering System were successfully designed based on the given business requirements.

---

