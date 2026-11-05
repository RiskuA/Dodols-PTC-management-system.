# University Management System (UMS)
Starter full-stack project using React + Vite, Node.js + Express, and MySQL.

## Features in this starter
- JWT login and role-based authorization
- Dashboard summary
- Students CRUD
- Courses CRUD
- User/role foundation
- MySQL schema + seed admin
- Responsive React UI

## Requirements
- Node.js 20+
- MySQL 8+

## Setup
1. Create database and tables:
   ```bash
   mysql -u root -p < database/schema.sql
   ```
2. Backend:
   ```bash
   cd backend
   cp .env.example .env
   # Set DB credentials and JWT_SECRET in .env
   npm install
   npm run dev
   ```
3. Frontend (new terminal):
   ```bash
   cd frontend
   npm install
   npm run dev
   ```
4. Open the Vite URL (usually http://localhost:5173).

## Seed administrator
Schema seeds `admin@ums.local` with a bcrypt hash for password `Admin123!`.
Change this immediately after first login. (Hash is generated using bcryptjs.)

## Notes
This is a functional starter foundation, not a production-certified university platform. Before production, add HTTPS, secure secrets, backups, audit trails, validation, rate limiting, email verification, and institution-specific workflows.

## Android + Windows online support
See `ONLINE-ANDROID-WINDOWS.md`. Frontend includes PWA manifest/service worker and Capacitor configuration. Deploy to HTTPS to install on Android and Windows; Android APK can be built through Android Studio.

## Expanded module set
Role dashboards and navigation now cover Admin, Registrar, Dean/HOD, Lecturer, Student, Finance, Admissions, Exam Officer, Librarian, HR and Student Affairs. Modules include students, courses, departments, registration, attendance, assessments/results, payments, admissions, library catalog, staff/users, and report center.

## Initial administrator
The schema intentionally does not insert a broken demo password. After configuring backend `.env` and starting the API, create your real admin:
`POST /api/auth/create-admin` JSON body: `{"fullName":"University Admin","email":"admin@youruniversity.edu","password":"Use-a-strong-password","setupKey":"YOUR_ADMIN_SETUP_KEY"}`
Then sign in. Rotate `ADMIN_SETUP_KEY` and disable/remove the setup route after first admin creation in production.
