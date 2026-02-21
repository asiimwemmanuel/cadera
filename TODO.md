## 🚀 **Project Overview & Roadmap**

### 1. **MVP Completion (Target: 24th Nov)**

- **DB Backups & Rollback**: Weekly backups and rollback functionality (DB-side). ✅ Completed.
- **Data Migration**: SPC per student, class entries in admin/students. ✅ Completed.
- **CI/CD Improvements**: Local DB setup to avoid mutating production.
- **Midterm Handling**:
  - Midterm only → final = midterm.
  - Midterm + end → final = average.
  - Otherwise → final = null. ✅ Completed.

- **Redesign Reports Template**: Ensure comment limit is 50 words. ✅ Completed.

---

### 2. **Bugs & Fixes**

#### **UI Bugs**:

- **Visual Issues in v2 of UI**:
  - Min/Max sidebar: Labels and Cadera logo disappearing. ❌ In Progress.
  - Grades subject sidebar misalignment + plaintext. ❌ In Progress.

#### **Existing Bug Reports**:

- **Comments Page**: Doesn't refresh on save. (Known bug) ❌ In Progress.

---

### 3. **Future Enhancements / Non-MVP**

- **MTA Implementation**:
  - New subject merchant (ID, name, subscription mechanism). ⏳ Pending.

- **Student Access**: Implement archived student access (target pre-Jan '26). ⏳ Pending.
- **Landing Page**: Design and implement (AM \* JM). ⏳ Pending.
- **Backend Documentation**: Write documentation for the backend (EA). ⏳ Pending.

---

## 📊 **High-Level Implementation & Performance**

- **Analytics & Stats**:
  - Ensure all grades and analytics are accurate (after MTA). ⏳ Pending.

- **Attendance Functionality**: Implement attendance tracking. ⏳ Pending.
- **Performance Optimizations**:
  - Double API calls: ✅ Completed.
  - Simple caching & memoization: ✅ Completed.
  - Prisma Accelerate: ✅ Completed.

---

## 🧑‍💻 **Development Pipeline**

### **Backend Tech Stack**

- **React Frontend** ⇅ HTTP ⇅ **NestJS Controller** ⇅ DTO + Guards ⇅ **NestJS Service Layer** ⇅ Prisma ⇅ PostgreSQL.

### **Deployment & Infrastructure**

- **Prisma Client Generation in CI/CD**:
  - Add Prisma client generation during deployment on Railway (due to different clients in prod and dev).
  - Use `DATABASE_URL` in Prisma config for connection in CI/CD pipeline (no direct connection necessary). ⏳ Pending.

- **Docker & Deployment**:
  - Write `Dockerfile` for backend.
  - Create `docker-compose.yml` for local dev (PostgreSQL + Backend). ⏳ Pending.

---

## 🧩 **Backend Development Tasks**

### 1. **Project Initialization**

- Scaffold NestJS project. ✅ Completed.
- Install dependencies:

  ```bash
  npm i @nestjs/config @nestjs/jwt @nestjs/passport prisma @prisma/client zod
  ```

### 2. **Domain Modeling** (Entities + Relations)

**Core Models**:

- `User` (Roles: ADMIN | TEACHER | STUDENT)
- `StudentProfile` (FK to `User`)
- `TeacherProfile` (FK to `User`)
- `Classroom`
- `Subject`
- `Enrollment` (Student ↔ Class/Subject)
- `Term`
- `PerformanceRecord` (marks, comments, grades, etc.)
- `ReportCard` (generated output)

Run initial migrations:

```bash
npx prisma migrate dev --name init
npx prisma generate
```

### 3. **Authentication & Access Control**

- **JWT Authentication** with PassportJS. ⏳ Pending.
- **Guards**:
  - `JwtAuthGuard`: Token validation.
  - `RolesGuard`: Role-based access. ⏳ Pending.

### 4. **API Endpoints** (REST)

**Core Modules & Endpoints**:

- `AuthModule`, `UsersModule`, `StudentsModule`, `TeachersModule`, `ClassesModule`, `SubjectsModule`, `ReportsModule`.
- Example endpoints:
  - `POST /auth/login`
  - `POST /students/register`
  - `GET /students/:id`
  - `GET /classes/:id/students`
  - `POST /reports/generate`

### 5. **Testing & Validation**

- **Unit Tests** for services (Jest). ⏳ Pending.
- **e2e Tests** using Nest’s testing module. ⏳ Pending.

---

## 📅 **Ongoing Development & Maintenance**

### **Students Page**:

- Prefill fields, editable fields (name, parent email, ID, subject offering). ⏳ Pending.
- **Add New Student Modal**: Flicker bug. ⏳ Pending.

### **Teachers / Classes / Grades / Reports**:

- Teachers Page: Almost done.
- Classes Page: Edit-only, in development.
- Grades, Comments, Reports Pages: Mostly done.
- School Page: Promotion logic pending.

---

## 🔒 **Authentication & Role Separation**

- **Role-Based Access Control (RBAC)**:
  - Grades: ⏳ Pending.
  - Comments: ⏳ Pending.
  - Reports: ✅ Completed.

- Ensure that users cannot access data not fetched (backend enforced). ✅ Completed.

---

## 🏗️ **Hosting & Cost Planning**

- **Monthly DB + Server Costs**: Monitor and calculate. ⏳ Pending.
- **Annual Cost Projection**: ⏳ Pending.

---

### **Notes & Next Steps**:

- **Next Milestone**: Focus on resolving UI bugs, integrating attendance functionality, and completing CI/CD deployment process (Prisma client generation).
- **Midterm/EOT pipeline**: Review and append necessary logic for report generation.
