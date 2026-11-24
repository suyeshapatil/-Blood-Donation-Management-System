# 🩸 Blood Donation Management System (BDMS)

A full-stack web application that helps donors, hospitals, and administrators coordinate blood donation activities and manage emergency blood requests through a centralized platform.

**Live Demo:** [Open BDMS](https://bdms-frontend-production.up.railway.app/)  
**GitHub Repository:** [Blood Donation Management System](https://github.com/suyeshapatil/-Blood-Donation-Management-System)

---

## 📌 Overview

The Blood Donation Management System (BDMS) digitalizes key blood donation workflows. Donors can maintain their profiles and availability, hospitals can search for donors and raise blood requests, and administrators can manage users and oversee system activity.

## ✨ Features

### 👤 Donor
- Register and log in securely.
- Maintain donor details, including blood group, city, and contact information.
- Update donation availability.
- View donation history.

### 🏥 Hospital
- Register and maintain a hospital profile.
- Search donors by blood group and city.
- Create emergency blood requests.
- Track blood request status.

### 🛡️ Administrator
- Manage donor and hospital accounts.
- Approve or reject hospital registrations.
- View donor, request, and blood-stock information.
- Manage users and role assignments.

### 🔐 Common Features
- JWT-based authentication.
- Role-based access control for `DONOR`, `HOSPITAL`, and `ADMIN`.
- Support for all eight standard blood groups: `A+`, `A-`, `B+`, `B-`, `O+`, `O-`, `AB+`, and `AB-`.
- Responsive interface for desktop, tablet, and mobile screens.

---

## 🛠️ Technology Stack

| Layer | Technologies |
|---|---|
| Frontend | React.js, JavaScript, HTML5, CSS3, Axios, React Router |
| Backend | Java, Spring Boot, Spring Security |
| Persistence | Spring Data JPA / Hibernate |
| Database | MySQL |
| Authentication | JWT, Spring Security |
| API Testing | Postman |
| Deployment | Railway |
| Development Tools | Git, GitHub, IntelliJ IDEA, Visual Studio Code |

---

## 🧱 Application Architecture

BDMS follows a frontend-backend architecture:

1. **React frontend** provides the user interface for donors, hospitals, and administrators.
2. **Spring Boot REST API** handles authentication, authorization, validation, and business logic.
3. **MySQL database** stores user, donor, hospital, and blood-request information.
4. **Spring Security and JWT** secure API access and enforce role-based permissions.

---

## 🚀 Live Demo Credentials

The following accounts are intended only for testing the deployed demo:

| Role | Email | Password |
|---|---|---|
| Donor | `demo.donor@gmail.com` | `demo123` |
| Hospital | `demo.hospital@gmail.com` | `demo123` |
| Admin | `admin@gmail.com` | `admin123` |

> **Security note:** Keep these credentials limited to disposable demo accounts. Never publish real user credentials, production passwords, database credentials, or secret JWT keys in a public repository.

If a demo account is unavailable, use the registration flow where enabled.

---

## 💻 Run the Project Locally

### Prerequisites

Install the following before starting:

- Java (version compatible with the backend project)
- Maven (or use the Maven Wrapper included in the repository)
- Node.js and npm
- MySQL Server

### 1. Clone the repository

```bash
git clone https://github.com/suyeshapatil/-Blood-Donation-Management-System.git
cd -Blood-Donation-Management-System
```

If the folder name differs on your machine, change into the cloned repository folder.

### 2. Configure and run the backend

Open a terminal in the backend directory:

```bash
cd BDMS_BACKEND2
```

Create the database in MySQL:

```sql
CREATE DATABASE bdms_db;
```

Update `src/main/resources/application.properties` with your local MySQL settings. For example:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/bdms_db
spring.datasource.username=YOUR_MYSQL_USERNAME
spring.datasource.password=YOUR_MYSQL_PASSWORD
```

Do not commit your actual database password or other secrets. Use environment variables or a local, untracked configuration file for sensitive values if the application supports them.

Run the backend using the Maven Wrapper:

**Windows:**
```bash
mvnw.cmd spring-boot:run
```

**macOS / Linux:**
```bash
./mvnw spring-boot:run
```

Or, if Maven is installed:

```bash
mvn spring-boot:run
```

The backend is expected to start at:

```text
http://localhost:8080
```

### 3. Install and run the frontend

Open another terminal:

```bash
cd BDMS_FRONTEND2
npm install
npm start
```

The frontend is expected to start at:

```text
http://localhost:3000
```

> If your local configuration uses a different API base URL or port, update the frontend API configuration accordingly.

---

## 🔌 REST API Overview

The following table summarizes the main API routes described for this project. The exact request fields and response formats are available in the backend source code and Postman collection.

### Authentication

| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/api/auth/register` | Register a new user |
| `POST` | `/api/auth/login` | Authenticate a user and obtain a JWT |

### Donors

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/api/donors` | Retrieve donors |
| `GET` | `/api/donors/search?bloodGroup=O%2B&city=Pune` | Search donors by blood group and city |
| `GET` | `/api/donors/{id}` | Retrieve a donor by ID |

### Hospitals

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/api/hospitals` | Retrieve hospitals |
| `POST` | `/api/hospitals` | Register a hospital |

### Blood Requests

| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/api/requests` | Create a blood request |
| `GET` | `/api/requests` | Retrieve blood requests |

### Postman Collection

The repository includes a Postman collection at:

```text
BDMS_BACKEND2/BDMS_Postman_Collection.json
```

Import this file into Postman to test the available APIs. Authenticated endpoints may require a valid JWT access token.

---

## 📁 Project Structure

```text
-Blood-Donation-Management-System/
│
├── BDMS_FRONTEND2/
│   ├── public/
│   ├── src/
│   │   ├── api/                 # API integration
│   │   ├── components/          # Reusable UI components
│   │   ├── constants/           # Roles, blood groups, API constants
│   │   ├── context/             # Shared authentication state
│   │   ├── hooks/               # Custom React hooks
│   │   ├── pages/               # Application pages
│   │   ├── routes/              # Application and protected routes
│   │   ├── utils/               # Helper and validation functions
│   │   ├── App.js
│   │   └── main.jsx
│   ├── package.json
│   └── README.md
│
├── BDMS_BACKEND2/
│   ├── src/
│   │   └── main/
│   │       ├── java/com/bdms/backend/
│   │       │   ├── config/      # Application and security configuration
│   │       │   ├── controller/  # REST controllers
│   │       │   ├── dto/         # Request and response DTOs
│   │       │   ├── entity/      # JPA entities
│   │       │   ├── enums/       # Roles, blood groups, statuses
│   │       │   ├── exception/   # Exception handling
│   │       │   ├── mapper/      # Entity and DTO mapping
│   │       │   ├── repository/  # Data repositories
│   │       │   ├── security/    # JWT and security components
│   │       │   ├── service/     # Business logic
│   │       │   ├── util/        # Utility classes
│   │       │   ├── validation/  # Custom validation
│   │       │   └── BdmsBackendApplication.java
│   │       └── resources/
│   │           └── application.properties
│   ├── BDMS_Postman_Collection.json
│   └── pom.xml
│
├── SRS_AC_27.pdf
└── README.md
```

---

## 📸 Screenshots

Add screenshots of the actual running application to the repository and link them here. For example, create a `screenshots/` folder in the repository and add:

| Page | Suggested file |
|---|---|
| Home page | `screenshots/home.png` |
| Donor search | `screenshots/donor-search.png` |
| Donor dashboard | `screenshots/donor-dashboard.png` |
| Hospital dashboard | `screenshots/hospital-dashboard.png` |
| Admin dashboard | `screenshots/admin-dashboard.png` |

Then embed them in this section using Markdown:
<!--
```md
![BDMS Home Page](screenshots/home.png)
```
-->
---

## 🔮 Future Enhancements

- SMS and email notifications for emergency blood requests.
- Blood donation camp and event management.
- Hospital blood-stock inventory tracking.
- Donor eligibility checks based on the last donation date.
- Map integration to help locate nearby donors.

---

## 👩‍💻 Author

**Suyesha Patil**

- GitHub: [@suyeshapatil](https://github.com/suyeshapatil)
- Project: [Blood Donation Management System](https://github.com/suyeshapatil/-Blood-Donation-Management-System)
- Live Demo: [bdms-frontend-production.up.railway.app](https://bdms-frontend-production.up.railway.app/)

---

## 📄 License

This project is available for educational purposes.<!-- If you intend to reuse or distribute it, add a `LICENSE` file to the repository specifying the license terms.-->
