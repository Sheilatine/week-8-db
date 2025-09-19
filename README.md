# 🏥 Clinic Booking System – Relational Database Project

## 📋 Overview

This project implements a *full-featured relational database* for managing a medical *clinic's appointments, patients, doctors, treatments, and billing* using *MySQL*.

It is designed to support real-world use cases such as appointment scheduling, treatment tracking, billing, and doctor specialization management.

---

## 🗃️ Features

* Manage *patients* and their contact details.
* Register *doctors* and associate them with one or more *specializations*.
* Schedule and track *appointments* between doctors and patients.
* Record *treatments* administered during appointments.
* Generate and manage *bills* based on treatments provided.
* Enforce *data integrity* through foreign keys and constraints.

---

## 🛠️ Technologies

* *Database:* MySQL
* *Language:* SQL
* *Schema Type:* Relational
* *Data Integrity:* Enforced with PRIMARY KEY, FOREIGN KEY, UNIQUE, and NOT NULL constraints

---

## 🗂️ Database Schema

### 1. *Patients*

| Field           | Type     | Description          |
| --------------- | -------- | -------------------- |
| patient\_id     | INT (PK) | Unique patient ID    |
| first\_name     | VARCHAR  | Patient’s first name |
| last\_name      | VARCHAR  | Patient’s last name  |
| date\_of\_birth | DATE     | Patient DOB          |
| email           | VARCHAR  | Unique email address |
| phone           | VARCHAR  | Contact number       |
| address         | TEXT     | Full address         |

---

### 2. *Doctors*

| Field       | Type     | Description         |
| ----------- | -------- | ------------------- |
| doctor\_id  | INT (PK) | Unique doctor ID    |
| first\_name | VARCHAR  | Doctor’s first name |
| last\_name  | VARCHAR  | Doctor’s last name  |
| email       | VARCHAR  | Unique email        |
| phone       | VARCHAR  | Contact number      |
| hire\_date  | DATE     | Date of employment  |

---

### 3. *Specializations*

| Field              | Type     | Description                     |
| ------------------ | -------- | ------------------------------- |
| specialization\_id | INT (PK) | Unique specialization ID        |
| name               | VARCHAR  | Unique field (e.g., Cardiology) |

---

### 4. *Doctor\_Specializations*

(Many-to-Many join between Doctors and Specializations)

| doctor\_id         | INT (FK) |
| ------------------ | -------- |
| specialization\_id | INT (FK) |

---

### 5. *Appointments*

| Field             | Type     | Description                       |
| ----------------- | -------- | --------------------------------- |
| appointment\_id   | INT (PK) | Unique appointment ID             |
| patient\_id       | INT (FK) | Linked patient                    |
| doctor\_id        | INT (FK) | Linked doctor                     |
| appointment\_date | DATETIME | Scheduled date and time           |
| reason            | TEXT     | Reason for visit                  |
| status            | ENUM     | Scheduled / Completed / Cancelled |

---

### 6. *Treatments*

| Field                  | Type     | Description              |
| ---------------------- | -------- | ------------------------ |
| treatment\_id          | INT (PK) | Unique treatment ID      |
| appointment\_id        | INT (FK) | Associated appointment   |
| treatment\_description | TEXT     | Description of treatment |
| cost                   | DECIMAL  | Cost of the treatment    |

---

### 7. *Bills*

| Field           | Type             | Description                      |
| --------------- | ---------------- | -------------------------------- |
| bill\_id        | INT (PK)         | Unique bill ID                   |
| appointment\_id | INT (FK, UNIQUE) | One-to-one link with appointment |
| total\_amount   | DECIMAL          | Total amount charged             |
| paid            | BOOLEAN          | Payment status                   |
| payment\_date   | DATE             | Date of payment (if paid)        |

---

## 🚀 Getting Started

### 📦 Importing the Database

1. Create the database and schema:

bash
mysql -u your_user -p < clinic_booking_system.sql


2. (Optional) Insert sample data:

bash
mysql -u your_user -p ClinicBookingSystem < clinic_sample_data.sql

## 📄 Files Included

| File Name                   | Description                         |
| --------------------------- | ----------------------------------- |
| clinic_booking_system.sql | SQL schema: tables + constraints    |
| README.md                 | Documentation (you’re reading it)   |


## 🧠 Future Improvements

* Add authentication system for staff logins
* Include support for prescriptions and medications
* Add role-based access control
* Support scheduling rules and availability

