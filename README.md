# CGPA & Attendance Calculator Web Application

A clean, responsive, full-stack student utility web application featuring a **Grade-Count CGPA Calculator** and an **Attendance Tracker**. Built with a **React (Vite)** frontend and an **Express.js (Node.js)** REST API backend.

---

## 📸 Overview & Features

### 1. CGPA Calculator
- **Grade Count Input**: Enter the count of subjects obtained in each grade letter:
  - **S Grade** = 10 Grade Points
  - **A Grade** = 9 Grade Points
  - **B Grade** = 8 Grade Points
  - **C Grade** = 7 Grade Points
  - **D Grade** = 6 Grade Points
  - **E Grade** = 5 Grade Points
  - **F Grade** = 0 Grade Points
- **Exact Calculation**:
  $$\text{CGPA} = \frac{(S \times 10) + (A \times 9) + (B \times 8) + (C \times 7) + (D \times 6) + (E \times 5) + (F \times 0)}{\text{Total Subjects}}$$
- Computes instantly via the Express REST API backend (`POST /api/calculate-cgpa`).
- Clean dark navy/amber/blue theme matching college portal aesthetics.

### 2. Attendance Tracker
- Easily accessible via the top-right toggle button (**`GO TO ATTENDANCE CALCULATOR`**).
- **Inputs**:
  - `Total number of classes`
  - `Number of classes attended`
- **Features**:
  - Computes exact attendance percentage ($$\frac{\text{Attended}}{\text{Total}} \times 100$$).
  - Displays progress bar and percentage (`75%`, `80%`, etc.).
  - **75% Exam Eligibility Indicator**:
    - If `< 75%`: Shows warning and calculates how many consecutive classes are needed to reach 75%.
    - If `≥ 75%`: Shows "Eligible for Exams" and calculates how many classes can be safely missed.

---

## 🏗️ Project Architecture

```text
Cgpa/
├── README.md                      # Comprehensive project documentation
│
├── backend/                       # Node.js + Express REST API Server
│   ├── index.js                   # Express server and calculation API routes
│   └── package.json               # Backend dependencies (express, cors, morgan)
│
└── frontend/                      # React 19 + Vite Application
    ├── public/                    # Static assets
    ├── src/
    │   ├── components/
    │   │   ├── CgpaCalculator.jsx     # CGPA grade count form & result display
    │   │   └── AttendanceTracker.jsx  # Attendance tracker & 75% eligibility meter
    │   ├── services/
    │   │   └── api.js                 # Centralized fetch client for backend APIs
    │   ├── App.jsx                    # View switching & root application layout
    │   ├── App.css                    # Component styling & dark theme
    │   ├── index.css                  # Global reset & typography
    │   └── main.jsx                   # React DOM entry point
    ├── index.html                 # HTML entry with updated title
    ├── vite.config.js             # Vite development server & proxy setup (/api -> :5000)
    └── package.json               # Frontend dependencies (react, vite)
```

---

## 📡 REST API Reference

### 1. Calculate CGPA
- **Endpoint**: `POST /api/calculate-cgpa`
- **Request Body**:
  ```json
  {
    "s": 2,
    "a": 2,
    "b": 3,
    "c": 7,
    "d": 0,
    "e": 0,
    "f": 0
  }
  ```
- **Response**:
  ```json
  {
    "success": true,
    "cgpa": "7.93",
    "totalSubjects": 14,
    "totalPoints": 111,
    "breakdown": {
      "s": 2,
      "a": 2,
      "b": 3,
      "c": 7,
      "d": 0,
      "e": 0,
      "f": 0
    }
  }
  ```

---

### 2. Calculate Attendance
- **Endpoint**: `POST /api/calculate-attendance`
- **Request Body**:
  ```json
  {
    "totalClasses": 100,
    "attendedClasses": 75
  }
  ```
- **Response**:
  ```json
  {
    "success": true,
    "totalClasses": 100,
    "attendedClasses": 75,
    "percentage": 75,
    "formatted": "75%",
    "exactFormatted": "75%",
    "isEligible": true,
    "status": "Eligible for Exams",
    "classesNeeded": 0,
    "classesCanMiss": 0
  }
  ```

---

### 3. Health Check
- **Endpoint**: `GET /api/health`
- **Response**:
  ```json
  {
    "status": "ok",
    "service": "CGPA & Attendance Calculator API",
    "timestamp": "2026-10-26T07:18:02.257Z"
  }
  ```

---

## 🚀 How to Run the Project

### Prerequisites
- Node.js (v18+ or v20+)
- npm (v9+)

### 1. Start the Backend API
```powershell
cd c:\Project\Cgpa\backend
npm start
```
> Express server runs on: **`http://localhost:5000`**

### 2. Start the Frontend React App
```powershell
cd c:\Project\Cgpa\frontend
npm run dev
```
> Vite dev server runs on: **`http://localhost:3000`**

---

## 🌐 Localhost Access
- **Frontend User Interface**: [http://localhost:3000](http://localhost:3000)
- **Backend API Server**: [http://localhost:5000](http://localhost:5000)
