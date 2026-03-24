# 📦 PulseCare - Project Modules

## 🧠 Overview
The system is divided into multiple modules based on functionality. Each module handles a specific part of the application.

---

## 🔐 1. Authentication Module

### Description:
Handles user registration, login, and security.

### Features:
- User Registration (Patient, Doctor, Admin)
- Login functionality
- JWT-based authentication
- Role-based authorization

---

## 👤 2. Patient Module

### Description:
Manages patient-related operations.

### Features:
- Register patient
- View patient profile
- Update patient details
- View list of doctors
- View prescriptions
- Check doctor availability
- Book and cancel appointment

---

## 👨‍⚕️ 3. Doctor Module

### Description:
Manages doctor-related operations.

### Features:
- Add doctor (Admin)
- View doctors list
- Search doctor by specialization
- Manage doctor availability schedule
- View assigned appointments

---

## 📅 4. Appointment Module

### Description:
Handles appointment booking and management.

### Features:
- Book appointment (Patient selects doctor based on availability)
- View appointments (Patient & Doctor)
- Cancel appointment
- Update appointment status (Scheduled, Completed, Cancelled)

---

## 💊 5. Prescription Module

### Description:
Handles medical prescriptions.

### Features:
- Add prescription (Doctor)
- View prescription (Patient)
- Store medicines and notes
- Link prescription with appointment

---

## 🔔 6. Notification Module

### Description:
Handles communication with users.

### Features:
- Email notifications (Registration, Appointment confirmation)
- Appointment reminders
- (Optional) SMS notifications

---

## 💳 7. Payment Module (Optional)

### Description:
Handles payment processing for appointments.

### Features:
- Online payment for booking
- Payment status tracking

---

## 🤖 8. AI Chatbot Module (Optional)

### Description:
Provides basic health assistance using AI.

### Features:
- Answer common health queries
- Provide basic guidance