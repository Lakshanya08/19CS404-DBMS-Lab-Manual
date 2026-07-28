
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
|--------|---------------------|-------|
| Member | Member_ID (PK), Name, Membership_Type, Start_Date | Stores details of gym members. |
| Program | Program_ID (PK), Program_Name, Category, Duration | Stores information about fitness programs such as Yoga, Zumba, and Weight Training. |
| Trainer | Trainer_ID (PK), Name, Qualification, Phone | Stores trainer information and specialization. |
| Personal_Session | Session_ID (PK), Session_Date, Session_Time, Member_ID (FK), Trainer_ID (FK) | Records personal training sessions booked by members. |
| Attendance | Attendance_ID (PK), Session_ID (FK), Member_ID (FK), Status | Records attendance for each personal training session. |
| Payment | Payment_ID (PK), Payment_Date, Amount, Payment_Method, Member_ID (FK) | Stores membership and personal session payment details. |
### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|-------------|----------------|-------|
| Member JOINS Program | M:N | Total – Partial | A member can join multiple programs, and a program can have many members. |
| Trainer ASSIGNED TO Program | M:N | Total – Total | A trainer can teach multiple programs, and a program can have multiple trainers. |
| Member BOOKS Personal Session | 1:N | Partial – Total | One member can book many personal training sessions; every session belongs to one member. |
| Trainer CONDUCTS Personal Session | 1:N | Partial – Total | One trainer can conduct many sessions; each session is conducted by one trainer. |
| Personal Session HAS Attendance | 1:N | Total – Total | Attendance is recorded for each session. |
| Member MAKES Payment | 1:N | Partial – Total | A member can make multiple payments; every payment belongs to one member. |

### Assumptions
1.	Every Member has a unique Member_ID. 
2.	Every Trainer has a unique Trainer_ID. 
3.	Every Program has a unique Program_ID. 
4.	A member may enroll in multiple programs. 
5.	A trainer may be assigned to multiple programs. 
6.	Each personal training session is conducted by one trainer for one member. 
7.	Attendance is recorded for each personal session. 
8.	Payments may be for either membership fees or personal training sessions.

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

| Entity            | Attributes (PK, FK)                                                                    | Notes                                                       |
| ----------------- | -------------------------------------------------------------------------------------- | ----------------------------------------------------------- |
| **Member**        | **Member_ID (PK)**, Name, Email, Phone_No, Membership_Status                           | Stores information about library members.                   |
| **Book**          | **Book_ID (PK)**, Title, Author, Publisher, Edition, Language                          | Stores details of all books available in the library.       |
| **Borrow_Record** | **Borrow_ID (PK)**, Member_ID (FK), Book_ID (FK), Due_Date, Return_Date, Borrow_Status | Records every book borrowing transaction.                   |
| **Event**         | **Event_ID (PK)**, Event_Name, Event_Date, Start_Time, End_Time                        | Stores information about library events.                    |
| **Speaker**       | **Speaker_ID (PK)**, Speaker_Name, Qualification, Phone_No                             | Stores details of speakers/authors participating in events. |
| **Fine**          | **Payment_ID (PK)**, Borrow_ID (FK), Amount, Fine_Date, Payment_Date, Payment_Status   | Stores overdue fine details for late book returns.          |

### Relationships and Constraints


| Relationship                         | Cardinality | Participation                           | Notes                                                                                      |
| ------------------------------------ | ----------- | --------------------------------------- | ------------------------------------------------------------------------------------------ |
| **Member — Borrows — Borrow_Record** | 1 : N       | Partial (Member), Total (Borrow_Record) | One member can have many borrow records; each borrow record belongs to one member.         |
| **Borrow_Record — For — Book**       | N : 1       | Total                                   | Each borrow record refers to one book; a book can appear in many borrow records over time. |
| **Borrow_Record — Generates — Fine** | 1 : 0..1    | Partial                                 | A borrow record generates a fine only if the book is returned late.                        |
| **Member — Registers — Event**       | M : N       | Partial                                 | Members may register for multiple events, and an event may have many registered members.   |
| **Event — Has — Speaker**            | M : N       | Total (Event), Partial (Speaker)        | Every event has one or more speakers, while a speaker may participate in multiple events.  |

### Assumptions
1.	Every member has a unique Member_ID. 
2.	Every book has a unique Book_ID. 
3.	A member can borrow multiple books, but each borrow record refers to only one book. 
4.	Borrow details such as loan date, due date, and return date are stored in Borrow_Record. 
5.	A fine is generated only if a book is returned after the due date. 
6.	Members can register for multiple events. 
7.	Each event may have multiple speakers. 
8.	A speaker may participate in multiple library events. 
9.	All primary keys are unique and cannot be NULL. 
10.	One borrow record can generate at most one fine.

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

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
