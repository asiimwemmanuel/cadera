# Cadera — Student Information System (SIS)

Cadera is a modern, modular **Student Information System (SIS)** designed to streamline student data management, academic performance tracking, and report generation.
Built for scalability and usability, it allows administrators & teachers to interact with academic data efficiently.

## Project Status

🛠️ **In Maintenance** — Cadera is actively being improved with additional features.

## Built By

- **Joshua Mukisa** — Frontend Engineer
- **Emmanuel Asiimwe** — Backend Developer & Database Architect
- **Albert Jordan** — UI/UX Designer

## Key Features

- **Dynamic Report Generation**
- **Class & Subject Management**
- **Role-Based Access Control** (Admin, Teacher, Student)
- **Exportable Report Cards** (PDF, Excel)
- **Search & Filter Functionality**

## Tech Stack

- **Frontend:** React.js, Tailwind CSS
- **Backend:** NestJS (modular architecture, TypeScript)
- **Database:** PostgreSQL (managed via Prisma)
- **Authentication:** JWT (JSON Web Tokens)
- **Tools:** Git, GitHub, Docker, Postman, Figma

---

> The following sections are only relevant to devs and maintainers

---

## Submodule READMEs

- [Backend README](./backend/README.md) — Backend setup, architecture, and API design.
- [Frontend README](./frontend/README.md) — Frontend setup, component structure, and UI design.

## Getting Started

To run locally:

### Clone the repository

```bash
git clone https://github.com/asiimwemmanuel/cadera.git
```

### Set up dev env

Follow the instructions in the respective submodule README files for frontend and backend dependencies.

- **Start both frontend and backend:**

  ```bash
  bun dev
  ```

- **Start only the backend:**

  ```bash
  bun dev:backend
  ```

- **Start only the frontend:**

  ```bash
  bun dev:frontend
  ```

> For more detailed setup instructions, refer to the respective **submodule README** files.
