# 🎓 Student Management REST API Automation Suite

![Postman](https://img.shields.io/badge/Postman-FF6C37?style=for-the-badge&logo=postman&logoColor=white)
![Newman](https://img.shields.io/badge/Newman-28A745?style=for-the-badge&logo=npm&logoColor=white)
![NodeJS](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)

An end-to-end automated API testing framework built using **Postman** and **Newman** to validate the core functionalities and RESTful endpoints of the **Student Details Management System**.

This suite verifies end-to-end CRUD operations, data integrity across linked relational entities (skills and addresses), dynamic payload handling via environment variables, and execution via command-line interface (CLI).

---

## 📌 Features & Test Highlights

* **Complete CRUD Validation:** Automated testing for `GET`, `POST`, `PUT`, and `DELETE` requests for student profiles.
* **Dynamic API Chaining:** Automatic extraction and passing of runtime dynamic variables (e.g., dynamic `student_id` extracted from POST creation to subsequent requests).
* **Nested Entity Association:** Sequential test coverage for related entities including technical skills (`/api/technicalskills`) and addresses (`/api/addresses/{id}`).
* **Comprehensive Assertions:**
  * HTTP status code checks (`200 OK`, `201 Created`).
  * Response time thresholds and payload size checks.
  * JSON Schema and key-value pair validation.
  * Dynamic environment state synchronization.
* **CLI Execution & Reporting:** Integrates **Newman** for running headless collections and generating structured execution summaries.

---

## 🧪 Test Execution & Workflow Summary

| Execution Order | Request Name | Method | Endpoint / Resource | Objective / Assertion Summary |
| :---: | :--- | :---: | :--- | :--- |
| **1** | Get Student List | `GET` | `/api/studentsDetails` | Fetch list of all students & validate response size/time. |
| **2** | Create Student | `POST` | `/api/studentsDetails` | Create a new student profile and extract `id` dynamically. |
| **3** | Get Specific Student | `GET` | `/api/studentsDetails/{id}` | Validate fetched student against created attributes. |
| **4** | Update Student | `PUT` | `/api/studentsDetails/{id}` | Update existing record parameters (e.g., name, course). |
| **5** | Verify Student Update | `GET` | `/api/studentsDetails/{id}` | Assert updated attributes in response payload. |
| **6** | Create Technical Skills | `POST` | `/api/technicalskills` | Bind skill sets to the student ID. |
| **7** | Create Student Address | `POST` | `/api/addresses/{id}` | Associate current/permanent address with student ID. |
| **8** | Final Student Details | `GET` | `/api/FinalStudentDetails/{id}` | Validate final aggregated JSON structure and array payloads. |

---

## 🛠️ Tech Stack & Prerequisites

* **Postman** (Desktop Client or Web)
* **Node.js** (v14.x or higher)
* **Newman CLI** (`npm install -g newman`)
* **Newman HTML Reporter** (`npm install -g newman-reporter-htmlextra`)

---

## 🚀 How to Run locally

### 1. Clone the Repository
```bash
git clone [https://github.com/pranjalprim/Student-Management-API-Automation-Suite.git](https://github.com/pranjalprim/Student-Management-API-Automation-Suite.git)
cd Student-Management-API-Automation-Suite
