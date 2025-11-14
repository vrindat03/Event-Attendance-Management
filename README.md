# Event-Attendance-Management
🎓 Digital Attendance System - Admin Dashboard Frontend

This repository contains the single-page, fully functional HTML/CSS/JavaScript frontend for the Admin Dashboard of a digital attendance management system. The interface is designed to be easily integrated with a Java Spring Boot backend via RESTful APIs.

🛠️ Technology Stack (Frontend)

📄 HTML5 & CSS3: Core structure and styling.

💨 Tailwind CSS: Used via CDN for rapid, responsive, utility-first styling.

💡 JavaScript (ES6+): Handles all client-side logic, view switching, form management, and data handling (using a local cache for demonstration).

🖼️ Lucide Icons: Lightweight, modern icon library used in the application (visualized here with emojis).

✨ Key Features of the Dashboard

This application provides robust, single-page functionality for user management:

👥 Role-Based Management (CRUD): Create, Read, Update, and Delete (CRUD) users for Students and Faculty.

📝 Dynamic Forms: The "Create/Edit User" form dynamically changes required fields based on the selected role (Student or Faculty).

Student Fields: Full Name, Email, Student ID, Branch, Year of Registration.

Faculty Fields: Full Name, Email, Employee ID, Department, Subject.

🔄 Role Assignment: The Admin can assign or revoke the Event Coordinator role to any Faculty member directly from the Faculty List using an intuitive toggle switch.

🔎 Filtering: The Faculty List includes a filter to quickly view all Faculty, only Event Coordinators, or only Faculty who are not Coordinators.

💾 Data Persistence (Mock): Data changes (create, edit, delete, coordinator toggles) are currently saved in a local JavaScript cache (appData). These are the core functions that must be replaced by API calls.

✅ UX Features: Includes password visibility toggle and confirmation modals for critical actions (Delete).

🚀 Backend Integration Guide (Java/Spring Boot)

The current JavaScript code includes placeholders for backend integration using the fetch API structure. You must connect the following UI actions to your REST endpoints.

All mock data handling is confined to the appData object and related functions (loadFacultyData, loadStudentsData, etc.).

1. Data Loading Endpoints (GET)

The loadFacultyData() and loadStudentsData() functions need to be updated to fetch data from your API.

Frontend Function

Suggested API Endpoint

HTTP Method

loadFacultyData()

GET /api/admin/faculty

Retrieve list of all faculty members.

loadStudentsData()

GET /api/admin/students

Retrieve list of all student members.

2. User Management Endpoints (CRUD)

All form submissions and table actions are delegated to specific data attributes (data-action="submit-create-user", data-action="edit-user", etc.).

Frontend Action

Suggested API Endpoint

HTTP Method

Create User

POST /api/admin/users/create

POST

Update User

PUT /api/admin/users/update/{id}

PUT

Delete User

DELETE /api/admin/users/delete/{id}

DELETE

Toggle Coordinator

PUT /api/admin/faculty/{id}/coordinator

PUT

3. Frontend Modification Checklist

To connect the application:

Locate Data Functions: Find async function loadFacultyData() and async function loadStudentsData() near the bottom of the script.

Replace Mock Data: Replace the const facultyList = [...] and const studentList = [...] lines with actual fetch calls:

// Example: Replacing mock data with a fetch call
const response = await fetch('/api/admin/faculty', {
    headers: { 'Authorization': 'Bearer YOUR_AUTH_TOKEN' } // Include auth header
});
const facultyList = await response.json();

// appData.faculty = facultyList; // Save to cache
// renderFacultyList(); // Render data


Update CRUD Logic: Modify the logic inside the submit-create-user, submit-edit-user, and confirm-delete event handlers to make API calls before calling the respective render...List() functions.

🏃 Getting Started

To run this frontend:

Clone this repository to your local machine.

Open the files in any modern web browser.

No server is required for the frontend demonstration. All required libraries (Tailwind CSS, Lucide Icons) are loaded via CDN.
