#  Automated Student Clearance System

A full-stack **MERN** (MongoDB, Express.js, React, Node.js) web application designed to digitize and streamline the university graduation clearance process. It replaces traditional paper-based workflows with real-time status tracking, automated academic eligibility verification, dynamic department management, and executive oversight.

---

##  Key Features

###  Student Portal
* **Automated Eligibility Verification:** Instantly checks student CGPA (minimum 2.5) and failed course records (`F` grades) before allowing clearance initiation. Includes conditional exemption rules (e.g., 1 failed course allowed if CGPA > 3.0) and auto-approval perks (4.0 CGPA auto-clears Datacell).
* **Real-Time Clearance Checklist:** Tracks live approval statuses (`Pending`, `Approved`, `Rejected`, `Resubmitted`) across all institutional departments.
* **Rejection Handling & Resubmission:** Displays specific rejection reasons from department admins and allows one-click resubmission once dues or issues are resolved.
* **Final Clearance Certificate:** Unlocks the official clearance certificate download once all departments approve the request.

###  Department Admin Dashboards
* **Role-Based Queues:** Dedicated views for **Finance, Datacell, Lab, Cafeteria, Library, Photocopier, Report**, and any dynamically added departments.
* **Actionable Workflows:** Admins can approve requests or reject them with custom feedback reasons.
* **Queue Filtering & Search:** Filter pending requests by academic department (`CS`, `SE`, `IT`) and search rejected queues by student registration number.
* **Approval History:** View a historical log of all previously cleared students.

###  Executive Director Dashboard
* **Institutional Oversight:** Real-time breakdown of `Approved`, `Pending`, and `Rejected` counts per department.
* **Dynamic Department Scaling:** Add new clearance departments on the fly without server restarts or code changes.
* **Student Tracking & Certificate Verification:** Filter students by clearance completion status (`All`, `Completed`, `In Progress`), search by name/roll number, and inspect official digital clearance certificates.

---

##  Tech Stack

* **Frontend:** React (Vite), JavaScript (ES6+), CSS-in-JS
* **Backend:** Node.js, Express.js
* **Database:** MongoDB, Mongoose ODM

---

##  Getting Started

### Prerequisites
* [Node.js](https://nodejs.org/) (v16+ recommended)
* [MongoDB](https://www.mongodb.com/) running locally on port `27017` (or a MongoDB Atlas URI)

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/automated-clearance-system.git
cd automated-clearance-system
```

### 2. Backend Setup
```bash
cd backend
npm install
```
Create a `.env` file in the `backend` directory (optional, defaults to local MongoDB):
```env
PORT=5000
MONGODB_URI=mongodb://127.0.0.1:27017/backup
```
Start the backend server:
```bash
node server.js
```

### 3. Frontend Setup
Open a new terminal window:
```bash
cd frontend
npm install
npm run dev
```

### 4. Seed Initial Test Data
With the backend running, open your browser and visit:
```text
http://localhost:5000/api/seed
```
This will populate the database with default departments, test students, CGPA/course records, and admin credentials.

---

##  Default Test Credentials

| Role | Registration ID | Password | Notes |
| :--- | :--- | :--- | :--- |
| **Director** | `admin-director` | `123` | Full executive overview & department creation |
| **Finance Admin** | `admin-finance` | `123` | *(Also `admin-lab`, `admin-library`, `admin-datacell`, etc.)* |
| **Student (Eligible)** | `4010` | `123` | CGPA: 3.2, 0 Failed Courses |
| **Student (4.0 Auto-Clear)** | `4004` | `123` | CGPA: 4.0 (Datacell auto-approved) |
| **Student (Ineligible)** | `4096` | `123` | CGPA: 2.1 (Blocked from applying) |

---

##  Project Structure

```text
├── backend/
│   ├── models/
│   │   ├── User.js
│   │   └── ClearanceRequest.js
│   └── server.js
└── frontend/
    └── src/
        ├── screens/
        │   ├── Login.jsx
        │   ├── Signup.jsx
        │   ├── Dashboard.jsx
        │   └── History.jsx
        ├── endPoints.js
        └── App.jsx
```
