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
<img width="1065" height="637" alt="Screenshot 2026-07-31 115259" src="https://github.com/user-attachments/assets/34af596e-9576-4097-9664-1850b99a9fda" />


### Entities and Attributes

| **Entity** | **Attributes (PK, FK)** | **Notes** |
| --- | --- | --- |
| **Member** | MemberID *(PK)*, MemberName, MembershipType, StartDate | Each member enrolls in programs, books sessions, attends classes, and makes payments. |
| **Program** | ProgramID *(PK)*, ProgramName, Schedule | Fitness programs offered by the gym; linked to trainers and sessions. |
| **Trainer** | TrainerID *(PK)*, TrainerName, Specialization | Trainers conduct sessions and are assigned to programs. |
| **Session** | SessionID *(PK)*, Date, Time, MemberID *(FK)*, TrainerID *(FK)* | Represents scheduled workout/training sessions. |
| **Attendance** | AttendanceID *(PK)*, MemberID *(FK)*, SessionID *(FK)*, Status | Tracks whether a member attended a session. |
| **Payment** | PaymentID *(PK)*, MemberID *(FK)*, Amount, PaymentType | Records membership or session payments made by members. |

### Relationships and Constraints

| **Relationship** | **Cardinality** | **Participation** | **Notes** |
| --- | --- | --- | --- |
| Member–Program | M : N | Optional | A member can enroll in multiple programs; each program can have many members. |
| Program–Trainer | N : M | Optional | Trainers can be assigned to multiple programs; programs can have multiple trainers. |
| Program–Session | M : N | Total on Session side | Each program consists of multiple sessions; sessions belong to programs. |
| Member–Session | M : N | Optional | Members can book multiple sessions; sessions can be attended by multiple members. |
| Session–Payment | N : 1 | Total on Payment side | Payments are linked to sessions; one payment may cover multiple sessions. |
| Trainer–Attendance | 1 : M | Total | A trainer manages attendance records for sessions they conduct. |
| Attendance–Member | 1 : N | Total | Attendance records are tied to members and sessions. |

### Assumptions
- A Trainer can specialize in multiple areas and may lead multiple programs.

- Session ID uniquely identifies each scheduled workout session.

- Payment Type could be Cash, Card, Online, etc.

- A member can miss sessions without losing membership, but attendance is still recorded.
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
<img width="972" height="560" alt="image" src="https://github.com/user-attachments/assets/d20618ba-ec44-4ec7-b622-5c77240294ae" />


### Entities and Attributes

| **Entity** | **Attributes (PK, FK)** | **Notes** |
| --- | --- | --- |
| **Member** | M_ID *(PK)*, Name, Contact | Each member can borrow books and register for events. |
| **Loans** | Loan_ID *(PK)*, M_ID *(FK)*, Book_ID *(FK)*, Loan_Date, Ret_Date, Fine_Amt | Tracks borrowing and returning of books; fine applied if overdue. |
| **Book** | Book_ID *(PK)*, Book_Name, Author | Each book can be borrowed multiple times; uniquely identified by Book_ID. |
| **Room** | R_ID *(PK)*, Room_No, Capacity | Rooms are used for events or study sessions. |
| **Event** | Event_ID *(PK)*, Title, Date, Room_ID *(FK)* | Represents cultural or author events organized by the library. |
| **Speaker** | S_ID *(PK)*, Name | Speakers/authors associated with events. |

### Relationships and Constraints

| **Relationship** | **Cardinality** | **Participation** | **Notes** |
| --- | --- | --- | --- |
| Member–Loans | 1 : M | Total  Loans side | A member can borrow many books; each loan belongs to one member. |
| Book–Loans | 1 : M | Total  Loans side | A book can appear in many loans; each loan refers to one book. |
| Member–Event | M : N | Optional | Members can register for multiple events; events can have many members. |
| Event–Speaker | 1 : M | Optional | Each event can have multiple speakers; each speaker can speak at one or more events. |
| Speaker–Room | 1 : 1 | Total | Each speaker is assigned to one room for their event. |
| Event–Room | 1 : M | Total  Event side | Each event must be held in one room; a room can host multiple events. |
### Assumptions
- Each Book has a unique ID and can be borrowed by one member at a time.

- Fine_Amt is calculated based on overdue days × fixed rate.

- Room can host multiple events but only one event at a time.

- Members must have valid membership to borrow books or register for events.

- Return Date must be later than or equal to Loan Date.

- Event Date must be unique per event title and room combination.

- Speaker–Room relationship assumes one speaker per room per event session.

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
<img width="837" height="627" alt="image" src="https://github.com/user-attachments/assets/e1076620-5f1d-41f8-9e2e-463f5c7260d3" />


### Entities and Attributes

| **Entity** | **Attributes (PK, FK)** | **Notes** |
| --- | --- | --- |
| **Customer** | C_ID *(PK)*, Name, Contact | Customers can reserve tables or walk in. |
| **Reservation** | Reserv_ID *(PK)*, Date, Time, NoOfGuests, C_ID *(FK)* | Each reservation includes date, time, and number of guests; linked to a customer. |
| **Order** | Order_ID *(PK)*, Reserv_ID *(FK)*, Dish_ID *(FK)* | Each reservation can have multiple orders; each order contains one or more dishes. |
| **Dish** | Dish_ID *(PK)*, Name, Price, Category | Dishes belong to categories such as Starter, Main, or Dessert. |
| **Bill** | Bill_ID *(PK)*, Reserv_ID *(FK)*, TotalAmount, ServiceCharge | Generated per reservation; includes food and service charges. |
| **Waiter** | Waiter_ID *(PK)*, Name | Waiters are assigned to serve reservations. |

### Relationships and Constraints

| **Relationship** | **Cardinality** | **Participation** | **Notes** |
| --- | --- | --- | --- |
| Customer–Reservation | 1 : M | Total on Reservation side | A customer can make multiple reservations; each reservation belongs to one customer. |
| Reservation–Order | 1 : M | Total on Order side | Each reservation can have multiple orders; each order is linked to one reservation. |
| Order–Dish | M : 1 | Total on Dish side | Each order includes one or more dishes; each dish can appear in multiple orders. |
| Reservation–Bill | 1 : 1 | Total on both sides | Each reservation generates one bill. |
| Reservation–Waiter | M : 1 | Total on Reservation side | Each reservation is served by one waiter; a waiter can serve multiple reservations. |
### Assumptions
- Customers may walk in or reserve tables in advance.

- Each reservation is linked to exactly one bill.

- Orders are placed per reservation, not directly by customers without a reservation.

- Dishes are categorized as Starter, Main, or Dessert for menu organization.

- ServiceCharge is a fixed percentage added to the total bill. 
---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
