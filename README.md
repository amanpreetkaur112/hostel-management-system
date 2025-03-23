# Hostel Management System
SQL based Database Management project

## 🏫 Project Overview
This Project is based on **SQL based Hostel Management System**. It handles student information, hostel room allocation, employee records, purchase and expense tracking, fee calculations, salary management, and overall profit/loss calculation. This system is designed to manage all essential hostel operations efficiently and ensures a streamlined process for hostel administration and financial management.

---

## ✨ Features
- Student information management
- Hostel room allocation for boys and girls
- Hostel fee calculation (per month & per day charges)
- Employee records and salary deduction based on absenteeism
- Daily purchase tracking (groceries, essentials, etc.)
- Expense management and profit calculation
- Comprehensive relational database design with normalization
- Clear linkage between students, hostels, employees, and financial data

---

## 👈 Database Structure

### 1. `student_s2`
| Column       | Type        | Description                      |
|-------------|------------|----------------------------------|
| id          | INT        | Primary Key, Auto Incremented    |
| std_name    | VARCHAR(50)| Student Name                     |
| address     | VARCHAR(50)| Student Address                  |
| branch      | VARCHAR(10)| Academic Branch                  |
| batch       | VARCHAR(10)| Batch Year                       |
| phn_no      | NUMERIC(50)| Phone Number                     |
| gender      | VARCHAR(10)| Gender                           |
| sem         | INT        | Semester                         |

---

### 2. `girlsh` & `boys_h1`
| Column        | Type         | Description                            |
|--------------|-------------|----------------------------------------|
| serial_no    | INT         | Primary Key, Auto Incremented          |
| std_id       | INT         | Foreign Key referencing `student_s2(id)`|
| name         | VARCHAR(50) | Student Name                           |
| building_no  | INT         | Building Number                        |
| room_no      | INT         | Room Number                            |
| hostel_fee   | DOUBLE      | Monthly Hostel Fee                     |
| room_type    | VARCHAR(30) | Room Type (Single, Double, Triple)     |

---

### 3. `girls_h_fee` & `boys_h1_fee`
| Column            | Type        | Description                                 |
|------------------|------------|---------------------------------------------|
| serial_no        | INT        | Serial Number                               |
| stdid            | INT        | Foreign Key referencing `girlsh/boys_h1.std_id` |
| std_name         | VARCHAR(50)| Student Name                                |
| room_no          | INT        | Room Number                                 |
| hostel_fee       | DOUBLE     | Hostel Fee                                  |
| perDay_roomCharge| DOUBLE     | Per Day Hostel Fee                          |

---

### 4. `employee`
| Column        | Type        | Description                              |
|--------------|------------|------------------------------------------|
| employeeid   | INT        | Primary Key                              |
| employee_name| VARCHAR(50)| Employee Name                            |
| phone        | NUMERIC(10)| Phone Number                             |
| salary       | DOUBLE     | Monthly Salary                           |
| DOJ          | DATE       | Date of Joining                          |
| absent       | INT        | Number of Days Absent                    |
| received_sal | DOUBLE     | Net Salary Received                      |

---

### 5. `salaries`
| Column        | Type        | Description                              |
|--------------|------------|------------------------------------------|
| serial_no    | INT        | Primary Key, Auto Incremented            |
| emp_id       | INT        | Foreign Key referencing `employee(employeeid)` |
| emp_name     | VARCHAR(50)| Employee Name                            |
| emp_sal      | DOUBLE     | Monthly Salary                           |
| per_day_sal  | DOUBLE     | Per Day Salary                           |

---

### 6. `purchase`
| Column      | Type        | Description                              |
|------------|------------|------------------------------------------|
| serial_no  | INT        | Primary Key, Auto Incremented            |
| day_no     | INT        | Day Number                               |
| rice, wheat, vegetable, oil, salt, sugar, spices, non_veg, other | DOUBLE | Daily purchase items cost |
| sum        | DOUBLE     | Total purchase cost                      |

---

### 7. `expense_s`
| Column         | Type        | Description                              |
|---------------|------------|------------------------------------------|
| serial_no     | INT        | Primary Key, Auto Incremented            |
| purchase_product | DOUBLE | Sum of Purchases                         |
| renovation    | DOUBLE     | Renovation Expenses                      |
| emp_salaries  | DOUBLE     | Total Employee Salaries                  |
| sum_of_expenses| DOUBLE    | Total Expenses                           |
| date          | DATE       | Expense Date                             |

---

### 8. `profit`
| Column         | Type        | Description                              |
|---------------|------------|------------------------------------------|
| day           | INT        | Day Number                               |
| purchase      | DOUBLE     | Daily Purchase Cost                      |
| salary        | DOUBLE     | Total Salary Paid                        |
| girls_h_charge| DOUBLE     | Total Girls Hostel Fee Collected         |
| boys_h_charge | DOUBLE     | Total Boys Hostel Fee Collected          |
| per_day_profit| DOUBLE     | Daily Profit                             |

---

### 9. `mainp_` (Summary Table)
| Column         | Type        | Description                              |
|---------------|------------|------------------------------------------|
| serial_no     | INT        | Primary Key, Auto Incremented            |
| std_id        | INT        | FK to `student_s2(id)`                   |
| name, branch  | VARCHAR    | Student Info                             |
| room_no, hostel_fee | DOUBLE| Hostel Info                             |
| emp_id        | INT        | FK to `salaries(emp_id)`                 |
| emp_name, emp_salary | VARCHAR/DOUBLE| Employee Info                  |
| day_no        | INT        | Day Number                               |
| purchase, sum_of_expenses, sum_of_hostelfee, per_day_profit | DOUBLE | Financial Summary |

---

## 📊 ER Diagram
The detailed **ER Diagram** illustrating the relationships between tables is provided in the project files.

---

## ⚙️ How to Run
1. Open MySQL command line or any MySQL GUI (like phpMyAdmin, MySQL Workbench).
2. Run the following commands:

```sql
CREATE DATABASE project;
USE project;
```
3. Execute each of the provided SQL code files in sequence:
   - Create `student_s2` table & insert data.
   - Create `girlsh`, `boys_h1`, hostel fee tables, employee & salaries tables, etc.
4. Run the final SELECT statements to verify:
```sql
SELECT * FROM student_s2;
SELECT * FROM girlsh;
SELECT * FROM boys_h1;
SELECT * FROM employee;
SELECT * FROM purchase;
SELECT * FROM expense_s;
SELECT * FROM profit;
SELECT * FROM mainp_;
```

---

## 🚀 Possible Future Enhancements
- Web-based dashboard for hostel admin to manage records.
- Login system for students and employees.
- Automated alerts for pending fees or salaries.
- Integration with payment gateways.
- Detailed analytics & monthly reports generation.

---

## 📜 License
This project is developed for academic purposes. Free to use, modify, and enhance.

---

## 👌 Acknowledgments
Special thanks to my group members for their valuable contributions and teamwork, which greatly assisted in the development of this project.
Thanks Sneha, Neha, Chetna, Agniva and Dhanesh.

