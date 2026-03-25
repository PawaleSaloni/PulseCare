# 🌐 PulseCare - API Design

## 🧠 Overview
This document defines REST APIs for Authentication, Patient, Doctor, Admin, Appointment, and Prescription modules.

Base URL: /api

---

# 🔐 1. Authentication APIs

## Register Patient
POST /api/auth/register

Request:
{
  "name": "Saloni",
  "email": "saloni@gmail.com",
  "password": "123456"
}

Response:
{
  "message": "Patient registered successfully"
}

---

## Login (All Roles)
POST /api/auth/login

Request:
{
  "email": "user@gmail.com",
  "password": "123456"
}

Response:
{
  "token": "JWT_TOKEN",
  "role": "PATIENT"
}

---

# 👤 2. Patient APIs

## Get Patient Profile
GET /api/patient/profile

## Update Patient Profile
PUT /api/patient/profile

## View All Doctors
GET /api/patient/doctors

## Search Doctors by Specialization
GET /api/patient/doctors?specialization=cardiology

## Book Appointment
POST /api/patient/appointments

Request:
{
  "doctorId": 1,
  "appointmentDate": "2026-03-26T10:00:00"
}

## View Appointments
GET /api/patient/appointments

## Cancel Appointment
DELETE /api/patient/appointments/{id}

## View Prescriptions
GET /api/patient/prescriptions

---

# 👨‍⚕️ 3. Doctor APIs

## Get Doctor Profile
GET /api/doctor/profile

## Update Availability
PUT /api/doctor/availability

Request:
{
  "available": true
}

## View Appointments
GET /api/doctor/appointments

## Update Appointment Status
PUT /api/doctor/appointments/{id}

Request:
{
  "status": "COMPLETED"
}

## Add Prescription
POST /api/doctor/prescriptions

Request:
{
  "appointmentId": 1,
  "medicines": "Paracetamol",
  "notes": "Take twice daily"
}

---

# 👩‍💼 4. Admin APIs

## Add Doctor
POST /api/admin/doctors

Request:
{
  "name": "Dr. Patel",
  "email": "dr@gmail.com",
  "password": "123456",
  "specialization": "Dermatologist"
}

## View All Doctors
GET /api/admin/doctors

## View All Patients
GET /api/admin/patients

## View All Appointments
GET /api/admin/appointments

## Delete User
DELETE /api/admin/users/{id}

---

# 📅 5. Appointment APIs (General)

## Get Appointment by ID
GET /api/appointments/{id}

---

# 💊 6. Prescription APIs (General)

## Get Prescription by ID
GET /api/prescriptions/{id}

---

# 🔐 Security

- JWT-based authentication required
- Role-based access:
  - ADMIN → /api/admin/**
  - DOCTOR → /api/doctor/**
  - PATIENT → /api/patient/**

---

# 📬 Tools for Testing

- Postman