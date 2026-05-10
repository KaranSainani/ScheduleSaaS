# ScheduleSaaS - Full Stack Appointment Management System

## 📌 Project Overview
**ScheduleSaaS** is a robust Appointment Management System designed as a SaaS solution. It bridges the gap between service providers and clients, offering a seamless scheduling experience. The system is built with a focus on **business logic integrity**, ensuring that time slots are dynamically calculated and protected against overlaps.


---

## ⚙️ Technical Core: Dynamic Duration Engine

One of the most relevant features of this repository is the **Automated End-Time Calculation** and secure scheduling logic:

*   **Backend Authority:** The server fetches the specific service duration from the database (MySQL) and calculates the `endTime` using Java's `LocalDateTime` API.
*   **Collision Prevention:** I implemented a custom **JPQL query** in the `AppointmentRepository` that uses interval mathematics to prevent any overlapping bookings for the same service.
*   **Time-Zone Safety:** All timestamps are handled in **ISO-8601** format to ensure compatibility between the JavaScript frontend and the Java backend.

---

## 🚀 Key Features

### 🎨 Frontend (React.js)
*   **Asynchronous State Management:** Utilizes `async/await` for non-blocking UI updates during API calls.
*   **Role-Based Access Control (RBAC):** Conditional rendering of administrative tools vs. client booking panels.
*   **Dynamic Slot Generation:** Frontend logic that pre-validates business hours (08:00-19:00) before hitting the server.

### ⚙️ Backend (Spring Boot)
*   **Security Suite:** Stateless authentication using **JWT (JSON Web Tokens)** and password encryption with **BCrypt**.
*   **Domain Logic:** Strict validation rules including weekend restrictions and specialized business hour windows.
*   **Error Handling:** A global exception handling layer that returns user-friendly messages for complex database conflicts.

---

## 📂 How it works

The system manages two distinct roles: **ADMIN** and **CLIENT**. All changes made in the UI are reflected in real-time in the Database.

> [!NOTE]
> While new clients can register via the web interface, the **ADMIN** user and initial **Services** are pre-configured in the `config/DataInitializer.java` file. To add new services or modify the admin credentials, update this file.

### User Roles & Permissions

| Feature | ADMIN | CLIENT |
| :--- | :---: | :---: |
| Register as a new client | - | ✅ |
| Book an appointment | ✅ | ✅ |
| Check personal scheduled appointments | ✅ | ✅ |
| Validate/Confirm client appointments | ✅ | - |
| View client list | ✅ | - |
| Delete client users | ✅ | - |

---

## 🗄️ Setup & Installation

### 1. Database Preparation
<br>

- Ensure you have **MySQL** installed and running.

- Create a new local schema (database). Hibernate will automatically generate the tables upon connection:
    ```sql
    CREATE DATABASE schedulesaas_db;
<br>
    
### 2	Environment Variables: 
<br>
To run this project, you will need to set up your local environment variables to secure your credentials. This prevents sensitive data from being hardcoded. Configure your IDE or system with the following:
<br>

- DB_URL: jdbc:mysql://localhost:3306/schedulesaas_db

- DB_USERNAME: Your MySQL username (e.g., root).
  
- DB_PASSWORD: Your MySQL password.


✨ **How to use it?**
<br>

Run the backend first and then do npm run dev on your IDE for the front-end. Vite would show you the PORT where is going to be my web app in your localhost. Make sure that if it is the same as the Back-end PORT in the file security>SecurityConfig.java

---
All code is in a .ZIP file that you can download via Google Drive:
<br>
https://drive.google.com/file/d/1Nw8r3U5uJCWVaPZvNGE6Fmo_uaoH0SxR/view?usp=sharing

