# 🩺 Doctor Appointment App

A Flutter-based **Doctor Appointment Application** that allows patients to discover doctors, view doctor profiles, book appointments, and manage their appointments.

The application also includes a **Doctor Panel** where doctors can manage their profiles, availability, and appointment requests.

---

## 📱 Project Overview

The Doctor Appointment App is designed with two different user roles:

### 👤 Patient

Patients can:

* Create an account
* Login securely
* Browse doctors
* Search doctors
* Filter doctors by specialization
* View doctor details
* Check doctor availability
* Select appointment date and time
* Book appointments
* View upcoming appointments
* View appointment history
* Cancel appointments
* Manage their profile
* Logout

### 👨‍⚕️ Doctor

Doctors can:

* Login to the doctor panel
* View dashboard
* Manage doctor profile
* Add specialization
* Add qualification and experience
* Set consultation fee
* Manage availability
* View appointment requests
* Accept appointments
* Reject appointments
* View upcoming appointments
* View completed appointments
* Manage profile
* Logout

---

# 🎯 Project Objectives

The main objectives of this project are:

* Build a real-world Flutter application
* Implement multiple screens and navigation
* Implement user authentication
* Implement role-based access
* Connect Flutter with a backend API
* Store user authentication data locally
* Implement doctor search and filtering
* Implement appointment booking
* Manage appointment status
* Create reusable Flutter widgets
* Practice API integration and database operations

---

# 🛠️ Technologies Used

## Frontend

* Flutter
* Dart
* Material Design

## Backend

* Node.js
* Express.js
* REST API

## Database

* MongoDB

## Authentication

* JWT Authentication
* SharedPreferences

---

# 🏗️ Application Architecture

```text
Flutter Application
        │
        │ HTTP Requests
        ▼
   REST API
        │
        ▼
 Node.js + Express
        │
        ▼
    MongoDB
```

---

# 👥 User Roles

The application supports two user roles.

```text
                 Application
                      │
              ┌───────┴───────┐
              │               │
           Patient          Doctor
              │               │
              ▼               ▼
        Patient Panel    Doctor Panel
```

---

# 📱 Main Screens

## Authentication

* Splash Screen
* Login Screen
* Register Screen
* Forgot Password Screen

---

## Patient Screens

### Home

The home screen provides:

* Search bar
* Doctor categories
* Popular doctors
* Recommended doctors
* Quick appointment access

### Explore Doctors

Patients can:

* Search doctors
* Filter doctors
* Browse specializations
* View doctor cards

### Doctor Details

Displays:

* Doctor profile image
* Doctor name
* Specialization
* Qualification
* Experience
* Consultation fee
* About doctor
* Available dates
* Available time slots

### Book Appointment

Patients can:

* Select doctor
* Select date
* Select time
* Enter appointment information
* Confirm appointment

### My Appointments

Appointments are divided into:

```text
Upcoming
Completed
Cancelled
Rejected
```

### Profile

Patients can:

* View profile
* Edit profile
* View appointments
* Manage account
* Logout

---

# 👨‍⚕️ Doctor Panel

## Doctor Dashboard

Displays:

* Today's appointments
* Pending appointment requests
* Upcoming appointments
* Appointment statistics

## Doctor Appointments

Doctors can view:

```text
Pending
Accepted
Completed
Cancelled
Rejected
```

Doctors can accept or reject pending appointment requests.

## Availability

Doctors can manage:

* Available days
* Available time slots
* Consultation availability

## Doctor Profile

Doctors can manage:

* Name
* Profile image
* Specialization
* Qualification
* Experience
* Consultation fee
* About
* Contact information

---

# 🔐 Authentication Flow

The authentication flow works as follows:

```text
User Opens App
      ↓
Splash Screen
      ↓
Check Login Status
      ↓
 ┌────┴────┐
 │         │
Logged In  Not Logged In
 │         │
 ▼         ▼
Home      Login
          │
          ▼
       Register
          │
          ▼
        Login
          │
          ▼
     JWT Token
          │
          ▼
   Save Local Data
          │
          ▼
     Open Dashboard
```

---

# 🔑 Role-Based Navigation

After login, the user's role determines which panel is opened.

```text
Login
  │
  ▼
Check User Role
  │
  ├── patient → Patient Home
  │
  └── doctor → Doctor Dashboard
```

---

# 💾 Local Storage

SharedPreferences is used to store basic authentication information locally.

Example:

```text
token
userId
userName
userRole
isLoggedIn
```

This allows the application to remember the user's login state.

---

# 📡 API Communication

Flutter communicates with the backend using REST APIs.

Example API structure:

```text
POST   /api/auth/register
POST   /api/auth/login

GET    /api/doctors
GET    /api/doctors/:id

PUT    /api/users/profile

POST   /api/appointments
GET    /api/appointments
PUT    /api/appointments/:id
DELETE /api/appointments/:id

GET    /api/doctors/:id/availability
PUT    /api/doctors/availability
```

The exact API endpoints can be modified according to the backend implementation.

---

# 🗄️ Database Models

## User

```text
User
├── _id
├── name
├── email
├── password
├── phone
├── profileImage
├── role
└── createdAt
```

Possible roles:

```text
patient
doctor
```

---

## Doctor

```text
Doctor
├── _id
├── userId
├── name
├── specialization
├── qualification
├── experience
├── consultationFee
├── profileImage
├── about
└── availability
```

---

## Appointment

```text
Appointment
├── _id
├── patientId
├── doctorId
├── date
├── time
├── reason
├── status
└── createdAt
```

Appointment status:

```text
pending
accepted
rejected
completed
cancelled
```

---

# 📂 Flutter Project Structure

```text
lib/
│
├── main.dart
│
├── models/
│   ├── user_model.dart
│   ├── doctor_model.dart
│   └── appointment_model.dart
│
├── screens/
│   │
│   ├── splash/
│   │   └── splash_screen.dart
│   │
│   ├── auth/
│   │   ├── login_screen.dart
│   │   ├── register_screen.dart
│   │   └── forgot_password_screen.dart
│   │
│   ├── patient/
│   │   ├── home_screen.dart
│   │   ├── explore_screen.dart
│   │   ├── doctor_details_screen.dart
│   │   ├── booking_screen.dart
│   │   ├── appointments_screen.dart
│   │   └── profile_screen.dart
│   │
│   └── doctor/
│       ├── doctor_dashboard.dart
│       ├── doctor_appointments.dart
│       ├── availability_screen.dart
│       └── doctor_profile.dart
│
├── services/
│   ├── api_service.dart
│   └── auth_service.dart
│
├── widgets/
│   ├── doctor_card.dart
│   ├── appointment_card.dart
│   ├── custom_button.dart
│   └── custom_text_field.dart
│
└── utils/
    ├── colors.dart
    ├── constants.dart
    └── routes.dart
```

---

# 🧭 Patient Bottom Navigation

```text
┌──────────┬──────────┬──────────────┬──────────┐
│   Home   │ Explore  │ Appointments │ Profile  │
└──────────┴──────────┴──────────────┴──────────┘
```

---

# 🧭 Doctor Bottom Navigation

```text
┌────────────┬──────────────┬──────────────┬─────────┐
│ Dashboard  │ Appointments │ Availability │ Profile │
└────────────┴──────────────┴──────────────┴─────────┘
```

---

# 📅 Appointment Workflow

```text
Patient
   │
   ▼
Search Doctor
   │
   ▼
Doctor Details
   │
   ▼
Select Date
   │
   ▼
Select Time
   │
   ▼
Confirm Appointment
   │
   ▼
Appointment Created
   │
   ▼
Pending
   │
   ▼
Doctor Reviews Request
   │
   ├──────────────┐
   ▼              ▼
Accepted        Rejected
   │
   ▼
Upcoming Appointment
   │
   ▼
Appointment Completed
```

---

# 🎨 UI Design

The application follows a clean and modern healthcare UI.

### Design Principles

* Clean interface
* Simple navigation
* Consistent spacing
* Rounded cards
* Clear typography
* Reusable components
* Responsive layouts
* Proper loading states
* Proper error messages
* Empty-state screens

### Suggested Theme

```text
Primary Color     → Medical Blue
Secondary Color   → Teal
Background        → Light
Cards             → White
Text              → Dark
Status            → Different indicators
```

---

# 🚀 Getting Started

## 1. Clone the Repository

```bash
git clone <repository-url>
```

Navigate into the project:

```bash
cd doctor_appointment_app
```

---

## 2. Install Dependencies

```bash
flutter pub get
```

---

## 3. Configure API URL

Update the API base URL according to your backend.

Example:

```dart
const String baseUrl = "http://YOUR_IP_ADDRESS:8000/api";
```

For a physical Android device, use the computer's local network IP when the backend is running on the same Wi-Fi network.

---

## 4. Start the Backend

Navigate to the backend folder:

```bash
cd backend
```

Install dependencies:

```bash
npm install
```

Start the server:

```bash
npm start
```

---

## 5. Run Flutter

From the Flutter project:

```bash
flutter run
```

You can run the application on:

* Android Emulator
* Physical Android Device
* Windows
* Chrome

---

# 🧪 Testing

The application should be tested for:

### Authentication

* Register with valid information
* Register with existing email
* Login with valid credentials
* Login with invalid credentials
* Logout
* Login persistence

### Doctor

* Search doctor
* Open doctor details
* View availability
* Update doctor profile
* Accept appointment
* Reject appointment

### Appointment

* Select date
* Select time
* Create appointment
* View appointment
* Cancel appointment
* Complete appointment
* Check appointment status

---

# 🔒 Security Considerations

The application should:

* Never store plain-text passwords locally
* Use JWT for authenticated API requests
* Validate user input
* Validate requests on the backend
* Protect doctor-only APIs
* Protect patient-only APIs
* Verify appointment ownership
* Handle expired authentication tokens

---

# 📈 Future Enhancements

Possible future features include:

* Push notifications
* Email notifications
* Online payment
* Video consultation
* Chat between doctor and patient
* Prescription management
* Medical reports
* Ratings and reviews
* Appointment reminders
* Admin panel
* Doctor verification
* Location-based doctor search

---

# 📌 Project Status

```text
🚧 Under Development
```

The project is being developed as a complete Flutter-based doctor appointment application with separate patient and doctor workflows.

---

# 👨‍💻 Learning Outcomes

By completing this project, you will practice:

* Flutter UI development
* Stateful and Stateless Widgets
* Navigation
* Forms and validation
* API integration
* JSON handling
* Authentication
* JWT
* SharedPreferences
* CRUD operations
* MongoDB integration
* Role-based access
* Reusable widgets
* Responsive UI
* Real-world project architecture

---

# 📄 License

This project is created for **learning and development purposes**.

You can modify and extend the project according to your requirements.
