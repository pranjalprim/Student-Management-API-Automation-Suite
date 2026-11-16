# 🎓 Student Details REST API Automation Suite

Automated end-to-end API testing suite built with **Postman** and executed via **Newman CLI** for the [TheTestingWorld Student Details API](https://thetestingworldapi.com/). This project validates full CRUD operations, nested relational endpoints (Technical Skills & Addresses), response schemas, data types, and execution performance.

---

## 📋 Table of Contents
- [Tech Stack & Tools](#-tech-stack--tools)
- [API Endpoints Tested](#-api-endpoints-tested)
- [Latest Test Execution Summary](#-latest-test-execution-summary)
- [Known Issues & Defect Log](#-known-issues--defect-log)
- [Project Structure](#-project-structure)
- [How to Run Locally](#-how-to-run-locally)

---

## 🛠️ Tech Stack & Tools
- **API Client & Scripting:** Postman (JavaScript / Chai Assertions)
- **CLI Test Runner:** Newman `v6.2.2`
- **HTML Reporting:** `newman-reporter-html` & `newman-reporter-htmlextra`
- **Environment Management:** Postman Environment Variables (`Student_Details_Environment`)

---

## 🔗 API Endpoints Tested

**Base URL:** `https://thetestingworldapi.com`

| # | Request Name | Method | Endpoint | Purpose | Status |
| :--- | :--- | :---: | :--- | :--- | :---: |
| 1 | **Get Student** | `GET` | `/api/studentsDetails` | Retrieve all student records | ⚠️ Partial (4/9 Passed) |
| 2 | **Create Student** | `POST` | `/api/studentsDetails` | Create a new student profile | ✅ Passed (18/18) |
| 3 | **Get Specific Student** | `GET` | `/api/studentsDetails/{{id}}` | Fetch newly created student by ID | ⚠️ Partial (9/10 Passed) |
| 4 | **Update Student** | `PUT` | `/api/studentsDetails/{{id}}` | Modify existing student details | ⚠️ Partial (5/6 Passed) |
| 5 | **Get Specific Student after update** | `GET` | `/api/studentsDetails/{{id}}` | Verify updated student details | ⚠️ Partial (9/10 Passed) |
| 6 | **Create Technical Skills** | `POST` | `/api/technicalskills` | Add technical skills for the student | ✅ Passed (6/6) |
| 7 | **Create Student Address** | `POST` | `/api/addresses/{{id}}` | Add permanent/present address | ✅ Passed (6/6) |
| 8 | **FINAL STUDENT DETAILS** | `GET` | `/api/FinalStudentDetails/{{id}}` | Validate complete aggregated profile | ✅ Passed (11/11) |
| 9 | **Delete Student** | `GET` | `/{{id}}` | Remove student record | ❌ Failed (404 HTML) |

---

## 📊 Latest Test Execution Summary

* **Execution Date:** November 16, 2026 (20:56 GMT+0600)
* **Collection:** `Rest_API_Testing_For_Student_Details`
* **Environment:** `Student_Details_Environment`

| Metric | Total | Passed | Failed |
| :--- | :---: | :---: | :---: |
| **Iterations** | 1 | 1 | 0 |
| **Requests** | 9 | 9 | 0 |
| **Pre-request Scripts** | 4 | 4 | 0 |
| **Test Scripts** | 9 | 8 | 1 |
| **Assertions** | 76 | 68 | 8 |
| **Skipped Tests** | 0 | - | - |

* **Total Run Duration:** `4.9s` – `5.2s`
* **Average Response Time:** `403ms` – `438ms`
* **Total Data Received:** `15.61 KB`
* **Overall Assertion Pass Rate:** `89.47%` (68/76 Assertions Passed)

---

## 🐞 Known Issues & Defect Log

During the automated test run, **9 failures** (8 assertion failures + 1 script error) were identified and documented:

1. **Get Student (`GET /api/studentsDetails`):**
   - *Payload Size Exceeded:* Response size reached `12.48 KB` (`12,782 bytes`), exceeding the `12 KB` threshold assertion.
   - *Script ReferenceError:* `responsebody is not defined` caused 4 schema/array validation assertions to fail due to variable casing in the test script.
2. **Get Specific Student / After Update (`GET /api/studentsDetails/{{id}}`):**
   - *Alternate Environment Key Mismatch:* Expected `undefined` to deeply equal `'Mr.'` / `'Miss'` / `'Ms.'`.
3. **Update Student (`PUT /api/studentsDetails/{{id}}`):**
   - *API Response Typo:* API returned `'update  data success'` (double space) instead of `'update data success'`.
4. **Delete Student (`GET /10895233`):**
   - *Endpoint / Method Misconfiguration:* Request sent as `GET` to `/{{id}}` instead of `DELETE /api/studentsDetails/{{id}}`, returning a `404 Not Found` HTML page (`JSONError: Unexpected token '<' at 1:1`).

---

## 📁 Project Structure

```text
├── collections/
│   └── Rest_API_Testing_For_Student_Details.postman_collection.json
├── environments/
│   └── Student_Details_Environment.postman_environment.json
├── reports/
│   ├── newman-run-report.html
│   └── Rest_API_Testing_For_Student_Details-summary.html
└── README.md
