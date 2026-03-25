# 🗄️ PulseCare - Database Schema

## 🧠 Overview
This schema supports role-based authentication, patient-doctor interaction, appointment booking, and prescription management.

---

## 👤 1. users (Authentication Table)

### Description:
Stores login credentials and roles for all users.

| Column       | Type           | Constraints                          |
|-------------|----------------|--------------------------------------|
| id          | BIGINT         | PK, AUTO_INCREMENT                   |
| name        | VARCHAR(100)   | NOT NULL                             |
| email       | VARCHAR(100)   | UNIQUE, NOT NULL                     |
| password    | VARCHAR(255)   | NOT NULL                             |
| role        | VARCHAR(20)    | NOT NULL (ADMIN, DOCTOR, PATIENT)    |
| created_at  | TIMESTAMP      | DEFAULT CURRENT_TIMESTAMP            |

---

## 👤 2. patients

### Description:
Stores additional details of patients.

| Column   | Type         | Constraints                  |
|----------|--------------|------------------------------|
| id       | BIGINT       | PK, AUTO_INCREMENT           |
| user_id  | BIGINT       | FK → users.id, UNIQUE        |
| age      | INT          |                              |
| gender   | VARCHAR(10)  |                              |
| phone    | VARCHAR(15)  |                              |

---

## 👨‍⚕️ 3. doctors

### Description:
Stores doctor-specific details.

| Column            | Type         | Constraints                  |
|------------------|--------------|------------------------------|
| id               | BIGINT       | PK, AUTO_INCREMENT           |
| user_id          | BIGINT       | FK → users.id, UNIQUE        |
| specialization   | VARCHAR(100) |                              |
| experience_years | INT          |                              |
| availability     | BOOLEAN      | DEFAULT TRUE                 |

---

## 📅 4. appointments

### Description:
Stores appointment booking between patient and doctor.

| Column            | Type         | Constraints                         |
|------------------|--------------|-------------------------------------|
| id               | BIGINT       | PK, AUTO_INCREMENT                  |
| patient_id       | BIGINT       | FK → patients.id                    |
| doctor_id        | BIGINT       | FK → doctors.id                     |
| appointment_date | DATETIME     | NOT NULL                            |
| status           | VARCHAR(20)  | (SCHEDULED, COMPLETED, CANCELLED)   |
| created_at       | TIMESTAMP    | DEFAULT CURRENT_TIMESTAMP           |

---

## 💊 5. prescriptions

### Description:
Stores prescriptions given after appointments.

| Column          | Type       | Constraints                         |
|----------------|------------|-------------------------------------|
| id             | BIGINT     | PK, AUTO_INCREMENT                  |
| appointment_id | BIGINT     | FK → appointments.id                |
| doctor_id      | BIGINT     | FK → doctors.id                     |
| patient_id     | BIGINT     | FK → patients.id                    |
| medicines      | TEXT       |                                     |
| notes          | TEXT       |                                     |
| created_at     | TIMESTAMP  | DEFAULT CURRENT_TIMESTAMP           |

---

## 🔔 6. notifications (Optional)

| Column     | Type         | Constraints              |
|------------|--------------|--------------------------|
| id         | BIGINT       | PK                       |
| user_id    | BIGINT       | FK → users.id            |
| message    | TEXT         |                          |
| type       | VARCHAR(20)  | EMAIL, SMS               |
| status     | VARCHAR(20)  | SENT, FAILED             |

---

## 💳 7. payments (Optional)

| Column          | Type        | Constraints             |
|----------------|-------------|--------------------------|
| id             | BIGINT      | PK                       |
| appointment_id | BIGINT      | FK → appointments.id     |
| amount         | DECIMAL     |                          |
| status         | VARCHAR(20) | PAID, PENDING            |
| payment_date   | DATETIME    |                          |

---

## 🔗 Relationships

- users → patients (1:1)
- users → doctors (1:1)
- patients → appointments (1:N)
- doctors → appointments (1:N)
- appointments → prescriptions (1:1)

---

## 🔄 System Flow

Admin → adds doctors  
Patient → registers  
Patient → books appointment → Doctor  
Doctor → adds prescription  

---

## 🔐 Role Logic

- ADMIN → stored only in users table (single user)
- DOCTOR → users + doctors table
- PATIENT → users + patients table