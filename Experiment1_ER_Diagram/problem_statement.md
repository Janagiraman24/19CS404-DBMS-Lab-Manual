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
<img width="1512" height="816" alt="Screenshot 2026-05-02 133732" src="https://github.com/user-attachments/assets/88c1ccc9-4883-4de2-b986-3700a5f8915c" />


### Entities and Attributes

| Entity     | Attributes (PK, FK)                                                           | Notes                                |
| ---------- | ----------------------------------------------------------------------------- | ------------------------------------ |
| Member     | **Member_ID (PK)**, Name, Membership_Type, Start_Date                         | Stores details of gym members        |
| Program    | **Program_ID (PK)**, Program_Name, Duration_Time                              | Stores fitness program details       |
| Trainer    | **Trainer_ID (PK)**, Trainer_Name, Specialization                             | Stores trainer information           |
| Session    | **Session_ID (PK)**, Date, Time, Member_ID (FK)                               | Stores booked training sessions      |
| Attendance | **Attendance_ID (PK)**, Session_ID (FK), Member_ID (FK), Date, Time, Status   | Stores attendance records of members |
| Payment    | **Payment_ID (PK)**, Payment_Date, Time, Status, Payment_Type, Member_ID (FK) | Stores payment transaction details   |


### Relationships and Constraints

| Relationship                  | Cardinality | Participation         | Notes                                                               |
| ----------------------------- | ----------- | --------------------- | ------------------------------------------------------------------- |
| Joins (Member–Program)        | M : N       | Partial participation | A member can join many programs and a program can have many members |
| Assigned To (Program–Trainer) | N : M       | Partial participation | Multiple trainers can handle multiple programs                      |
| Books (Member–Session)        | 1 : N       | Total on Session      | One member can book many sessions                                   |
| Recorded (Session–Attendance) | 1 : N       | Total on Attendance   | One session can have many attendance records                        |
| Makes (Member–Payment)        | 1 : N       | Total on Payment      | One member can make many payments                                   |


### Assumptions

-Each member has a unique Member_ID. 

-A trainer may specialize in multiple fitness areas but one specialization is stored.

-Each session is booked by only one member.

-Attendance is recorded for every session conducted.

-Payments are made only by registered members.

### Result:
The ER model represents members, trainers, programs, sessions, attendance, and payments with their relationships in a gym management system.
It is simple, efficient, minimizes data redundancy, and supports future database expansion.


