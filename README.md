# Durniti Watch Bangladesh - Backend

**A citizen powered platform for reporting and monitoring corruption in Bangladesh.**

Durniti Watch Bangladesh is a web based platform designed to help citizens report corruption, bribery, and irregularities in public service delivery. The backend provides secure APIs for report submission, evidence management, user authentication, report verification, and administrative operations.

This project is developed collaboratively by a team of **4 members**.

## Table of Contents

- [Project Overview](#project-overview)
- [Key Features](#key-features)
- [Technology Stack](#technology-stack)
- [Project Folder Structure](#project-folder-structure)
- [Installation and Setup](#installation-and-setup)
- [Environment Variables](#environment-variables)
- [Running the Project](#running-the-project)
- [Team Members and Responsibilities](#team-members-and-responsibilities)
- [Development Workflow](#development-workflow)
- [API Design Guidelines](#api-design-guidelines)
- [Security and Privacy](#security-and-privacy)
- [Git Commit Convention](#git-commit-convention)
- [Contribution Guidelines](#contribution-guidelines)
- [Project Roadmap](#project-roadmap)
- [License](#license)

## Project Overview

**Project Name:** Durniti Watch Bangladesh  
**Repository:** [durniti-watch-bd-backend](https://github.com/hzamanshohag/durniti-watch-bd-backend)  
**Team Size:** 4 Members

### Mission

To provide a secure and accessible platform where citizens can document suspected corruption, submit supporting evidence, and help authorized reviewers identify and investigate reported irregularities.

## Key Features

### 1. User Authentication and Authorization
- User registration and login.
- Secure password hashing.
- JWT-based authentication.
- Role-based access control (RBAC).
- User profile management.
- Anonymous reporting support.

### 2. Corruption Reporting
Citizens can submit reports containing:

- Government office or organization name.
- Division, district, upazila, and location.
- Service or application type.
- Reported bribe amount.
- Incident date and description.
- Accused person's name or position, when appropriate.
- Optional photo, video, and document evidence.
- Anonymous reporting preference.

### 3. Report Management
- Create, view, and update reports according to permissions.
- Track report status.
- Filter reports by district, office, date, and category.
- Search and paginate report listings.
- Manage duplicate, incomplete, or inappropriate submissions.

### 4. Evidence Management
- Upload supporting evidence.
- Validate file types and sizes.
- Restrict evidence access to authorized users.
- Track evidence metadata and ownership.
- Support secure evidence review and removal workflows.

### 5. Verification and Moderation
- Review submitted reports.
- Request additional information.
- Verify evidence and update report status.
- Maintain moderation records.
- Record important administrative actions.

### 6. AI Assistant
- Provide information about using the platform.
- Help users understand the reporting process.
- Support Bangla and English interactions.
- Explain general anti-corruption reporting procedures.

AI-generated responses must not be treated as proof that an allegation is true.

### 7. Administration
- Manage users and roles.
- Review reports and evidence.
- Monitor report statistics.
- Manage categories and moderation workflows.
- Maintain audit logs for sensitive actions.

## Technology Stack

### Currently Installed

| Technology | Purpose |
|---|---|
| Node.js | JavaScript runtime |
| Express.js | REST API framework |
| TypeScript | Type-safe development |
| MongoDB | Document database |
| Mongoose | MongoDB ODM and schema management |
| Zod | Request and environment validation |
| tsx | Execute TypeScript during development |
| Nodemon | Automatically restart the development server |
| TypeScript compiler | Type checking and compilation |

### Recommended Additional Technologies

| Technology | Purpose |
|---|---|
| dotenv | Environment variable management |
| cors | Cross-origin request configuration |
| Helmet | HTTP security headers |
| express-rate-limit | Request rate limiting |
| bcryptjs | Password hashing |
| jsonwebtoken | JWT authentication |
| multer | Multipart file upload handling |
| Pino / pino-http | Structured application logging |
| Vitest or Jest | Automated testing |
| Supertest | API integration testing |
| Cloudinary or private object storage | Evidence file storage |
| OpenAI API | AI assistant integration |
| Swagger / OpenAPI | API documentation |
| Git and GitHub | Version control and collaboration |

The recommended packages are optional additions; they are not all present in the supplied `package.json`.

## Project Folder Structure

The following structure is recommended for a maintainable Express.js, TypeScript, and Mongoose backend.

```text
durniti-watch-bd-backend/
│
├── src/
│   ├── app.ts
│   ├── server.ts
│   │
│   ├── config/
│   │   ├── env.ts
│   │   ├── database.ts
│   │   └── cors.ts
│   │
│   ├── modules/
│   │   ├── auth/
│   │   │   ├── auth.controller.ts
│   │   │   ├── auth.service.ts
│   │   │   ├── auth.route.ts
│   │   │   ├── auth.validation.ts
│   │   │   └── auth.model.ts
│   │   │
│   │   ├── users/
│   │   │   ├── user.controller.ts
│   │   │   ├── user.service.ts
│   │   │   ├── user.route.ts
│   │   │   ├── user.validation.ts
│   │   │   └── user.model.ts
│   │   │
│   │   ├── reports/
│   │   │   ├── report.controller.ts
│   │   │   ├── report.service.ts
│   │   │   ├── report.route.ts
│   │   │   ├── report.validation.ts
│   │   │   └── report.model.ts
│   │   │
│   │   ├── evidence/
│   │   ├── verification/
│   │   ├── categories/
│   │   ├── ai-assistant/
│   │   ├── notifications/
│   │   └── admin/
│   │
│   ├── middlewares/
│   │   ├── auth.middleware.ts
│   │   ├── role.middleware.ts
│   │   ├── validate.middleware.ts
│   │   ├── error.middleware.ts
│   │   └── rate-limit.middleware.ts
│   │
│   ├── models/
│   │   └── audit-log.model.ts
│   │
│   ├── routes/
│   │   └── index.ts
│   │
│   ├── utils/
│   │   ├── ApiError.ts
│   │   ├── ApiResponse.ts
│   │   ├── catchAsync.ts
│   │   └── logger.ts
│   │
│   ├── types/
│   │   └── express.d.ts
│   │
│   └── constants/
│       ├── roles.ts
│       └── report-status.ts
│
├── tests/
│   ├── unit/
│   └── integration/
│
├── docs/
│   ├── api-documentation.md
│   ├── database-design.md
│   └── permissions.md
│
├── uploads/
│   └── .gitkeep
│
├── .env.example
├── .gitignore
├── package.json
├── package-lock.json
├── tsconfig.json
└── README.md
```

### Folder Responsibilities

- `config/`: Database connection, environment configuration, and CORS.
- `modules/`: Business logic organized by feature.
- `controllers/`: Handle incoming requests and outgoing responses.
- `services/`: Implement business rules and database operations.
- `models/`: Define Mongoose schemas and models.
- `routes/`: Register API endpoints.
- `validation/`: Validate request bodies, parameters, and query strings with Zod.
- `middlewares/`: Authentication, authorization, validation, and error handling.
- `utils/`: Shared helpers, logging, and response utilities.
- `tests/`: Unit and integration tests.
- `docs/`: API documentation, database design, and permission specifications.

Keep module-specific files inside their respective feature folders. Avoid creating duplicate models or controllers for the same feature.

## Installation and Setup

### Prerequisites

Install the following before starting:

- Node.js LTS
- npm
- Git
- MongoDB local installation or MongoDB Atlas account
- A code editor such as Visual Studio Code

Check the installed versions:

```bash
node -v
npm -v
git --version
```

### Step 1: Clone the Repository

```bash
git clone https://github.com/hzamanshohag/durniti-watch-bd-backend.git

cd durniti-watch-bd-backend
```

### Step 2: Install Existing Dependencies

```bash
npm install
```

### Step 3: Install Recommended Dependencies

Install useful middleware and authentication packages:

```bash
npm install dotenv cors helmet express-rate-limit bcryptjs jsonwebtoken multer pino pino-http
```

Install development and testing dependencies:

```bash
npm install -D @types/express @types/cors @types/bcryptjs @types/jsonwebtoken @types/multer vitest supertest @types/supertest
```

Review package compatibility and current type-package availability before installing optional dependencies.

### Step 4: Configure TypeScript

Create a `tsconfig.json` file in the root directory.

```json
{
  "compilerOptions": {
    "target": "ES2022",
    "module": "CommonJS",
    "moduleResolution": "Node",
    "rootDir": "./src",
    "outDir": "./dist",
    "strict": true,
    "esModuleInterop": true,
    "forceConsistentCasingInFileNames": true,
    "skipLibCheck": true,
    "resolveJsonModule": true
  },
  "include": ["src/**/*.ts"],
  "exclude": ["node_modules", "dist", "tests"]
}
```

### Step 5: Update `package.json` Scripts

Add the following scripts to the existing `scripts` section:

```json
{
  "scripts": {
    "dev": "nodemon --watch src --ext ts,json --exec tsx src/server.ts",
    "build": "tsc",
    "start": "node dist/server.js",
    "typecheck": "tsc --noEmit",
    "test": "vitest run",
    "test:watch": "vitest"
  }
}
```

Merge these scripts into your existing `package.json`; do not replace the repository metadata or dependency lists.

### Step 6: Create the Environment File

Create `.env` in the project root. Use `.env.example` as the shareable template.

```env
NODE_ENV=development
PORT=5000

DATABASE_URL=mongodb://127.0.0.1:27017/durniti-watch-bd

JWT_SECRET=replace_with_a_long_random_secret
JWT_EXPIRES_IN=1d

CLIENT_URL=http://localhost:3000
```

Never commit the real `.env` file or production credentials to GitHub.

### Step 7: Connect MongoDB

Create `src/config/database.ts`:

```typescript
import mongoose from "mongoose";

export async function connectDatabase(): Promise<void> {
  const databaseUrl = process.env.DATABASE_URL;

  if (!databaseUrl) {
    throw new Error("DATABASE_URL is not configured");
  }

  await mongoose.connect(databaseUrl);

  console.log("MongoDB connected successfully");
}
```

Load environment variables before connecting to the database. Validate required environment variables during application startup.

## Running the Project

Start the development server:

```bash
npm run dev
```

Run TypeScript checks:

```bash
npm run typecheck
```

Build the production version:

```bash
npm run build
```

Start the compiled production server:

```bash
npm start
```

Run tests:

```bash
npm test
```

Once `src/server.ts` and `src/app.ts` have been implemented, the server should listen on the configured port and connect to MongoDB before accepting database-dependent requests.

## Environment Variables

| Variable | Purpose |
|---|---|
| `NODE_ENV` | Application environment |
| `PORT` | Backend server port |
| `DATABASE_URL` | MongoDB connection string |
| `JWT_SECRET` | Secret used to sign JWTs |
| `JWT_EXPIRES_IN` | Token expiration duration |
| `CLIENT_URL` | Allowed frontend origin |

Additional credentials for email delivery, AI services, and file storage should be introduced only when those integrations are implemented.

## Team Members and Responsibilities

The project is developed by four team members. Replace the placeholders below with the actual GitHub usernames and confirmed assignments.

| Member | Role | Main Responsibilities |
|---|---|---|
| Member 1 — [Name / GitHub] | Backend Lead & Architecture | Project structure, Express setup, TypeScript configuration, MongoDB connection, shared middleware, code review, and integration |
| Member 2 — [Name / GitHub] | Authentication & User Management | Registration, login, password hashing, JWT authentication, user profiles, RBAC, and permissions |
| Member 3 — [Name / GitHub] | Corruption Reports & Evidence | Report schemas, report CRUD APIs, location and category filters, anonymous submissions, file upload workflows, and evidence access control |
| Member 4 — [Name / GitHub] | Verification, Admin & Integrations | Report review and verification workflows, admin APIs, AI assistant integration, notifications, testing, and API documentation |

### Shared Responsibilities

Every team member is expected to:

- Follow the agreed folder structure and coding conventions.
- Write and maintain validation schemas.
- Test their own endpoints before merging.
- Update API documentation when contracts change.
- Review teammates' pull requests.
- Keep credentials and sensitive data out of source control.
- Coordinate changes to shared models, middleware, and routes.

**Important:** These are proposed ownership areas, not confirmed assignments. The team should agree on final responsibilities before development begins.

## API Design Guidelines

Use a consistent REST API prefix:

```text
/api/v1
```

### Proposed Endpoints

| Method | Endpoint | Purpose |
|---|---|---|
| POST | `/api/v1/auth/register` | Register a user |
| POST | `/api/v1/auth/login` | Authenticate a user |
| GET | `/api/v1/users/me` | Get the authenticated user's profile |
| PATCH | `/api/v1/users/me` | Update the current user's profile |
| POST | `/api/v1/reports` | Submit a corruption report |
| GET | `/api/v1/reports` | List reports according to visibility rules |
| GET | `/api/v1/reports/:id` | View an accessible report |
| PATCH | `/api/v1/reports/:id` | Update a report when authorized |
| POST | `/api/v1/reports/:id/evidence` | Upload evidence |
| PATCH | `/api/v1/admin/reports/:id/status` | Change report status with appropriate permission |
| POST | `/api/v1/ai/chat` | Send a message to the AI assistant |

These endpoints are a proposed API design and should be aligned with the actual implementation and permission rules.

### Standard Response Format

Successful response:

```json
{
  "success": true,
  "message": "Report submitted successfully",
  "data": {
    "id": "example-report-id",
    "status": "PENDING_REVIEW"
  }
}
```

Error response:

```json
{
  "success": false,
  "message": "Validation failed",
  "errors": [
    {
      "field": "description",
      "message": "Description is required"
    }
  ]
}
```

Use appropriate HTTP status codes, including `200`, `201`, `400`, `401`, `403`, `404`, `409`, `422`, and `500`, as appropriate for each operation.

## Security and Privacy

Because corruption reports may contain sensitive allegations and identifying information, security and privacy must be treated as core requirements.

1. **Authentication:** Protect private endpoints with authentication middleware.
2. **Authorization:** Enforce role and resource-level permissions on the server.
3. **Password security:** Hash passwords using a suitable password-hashing algorithm; never store plaintext passwords.
4. **Anonymous reports:** Do not expose the reporter's identity in public responses. Clearly document what information the system still collects.
5. **Evidence protection:** Keep private evidence out of public directories and enforce authorization before access.
6. **File validation:** Validate file size, extension, MIME type, and actual file content. Use safe storage keys and prevent executable uploads.
7. **Rate limiting:** Limit authentication, reporting, upload, and AI endpoints to reduce abuse.
8. **Input validation:** Use Zod to validate incoming data before business logic executes.
9. **Audit logging:** Record sensitive administrative actions without logging passwords, tokens, or unnecessary personal data.
10. **Report moderation:** Treat submitted allegations as unverified until reviewed through the defined process.
11. **Data minimization:** Collect only information required for the platform's purpose and establish appropriate retention policies.
12. **Error handling:** Avoid returning stack traces, database details, secrets, or internal implementation information to clients.

Public report listings should reveal only fields explicitly approved for public display. Reporters' personal information and private evidence must not become publicly accessible by default.

## Git Commit Convention

Use clear, consistent commit messages.

```bash
git commit -m "chore: initialize backend project"
git commit -m "feat: add user authentication"
git commit -m "feat: implement corruption report APIs"
git commit -m "feat: add evidence upload validation"
git commit -m "fix: handle invalid report requests"
git commit -m "test: add report service tests"
git commit -m "docs: update API documentation"
```

### Branch Naming

```text
main
development
feature/authentication
feature/report-management
feature/evidence-upload
feature/admin-verification
fix/report-validation
docs/api-documentation
```

Use individual feature branches rather than committing unfinished work directly to `main`.

## Development Workflow

1. Review the task and agree on its API contract.
2. Create a feature branch from `development`.
3. Implement the model, validation, service, controller, and route where applicable.
4. Add or update tests.
5. Run `npm run typecheck` and `npm test`.
6. Open a pull request against `development`.
7. Request a teammate's review.
8. Resolve review comments and merge the approved changes.
9. Test the integrated application before promoting stable code to `main`.

### Code Review Checklist

- [ ] TypeScript types are correct.
- [ ] Zod validation is implemented.
- [ ] Authentication and authorization are enforced.
- [ ] Database queries respect resource ownership and visibility.
- [ ] Errors are handled consistently.
- [ ] Sensitive data is not exposed.
- [ ] Tests cover the important scenarios.
- [ ] API documentation is updated.

## Project Roadmap

### Phase 1 — Backend Foundation
- [ ] Initialize Express and TypeScript.
- [ ] Configure environment validation.
- [ ] Connect MongoDB with Mongoose.
- [ ] Add global error handling.
- [ ] Configure CORS and security middleware.

### Phase 2 — Authentication and Users
- [ ] Implement registration and login.
- [ ] Add secure password hashing.
- [ ] Implement authentication and RBAC.
- [ ] Define anonymous reporting behavior.

### Phase 3 — Reports and Evidence
- [ ] Create report schemas and validation.
- [ ] Implement report submission and retrieval.
- [ ] Add filtering, search, and pagination.
- [ ] Implement secure evidence uploads.
- [ ] Add report visibility and access controls.

### Phase 4 — Verification and Administration
- [ ] Implement report moderation.
- [ ] Add evidence review workflows.
- [ ] Implement administrative endpoints.
- [ ] Record sensitive administrative actions.

### Phase 5 — Integrations and Quality
- [ ] Integrate the AI assistant.
- [ ] Add notifications where needed.
- [ ] Publish OpenAPI documentation.
- [ ] Add unit and integration tests.
- [ ] Prepare deployment configuration.
- [ ] Perform security and privacy reviews.

## Contribution Guidelines

We welcome collaboration from team members and other contributors who share the goal of building a reliable and responsible reporting platform.

Before contributing:

1. Read the project documentation.
2. Check existing issues and assigned tasks.
3. Discuss significant architectural changes with the team.
4. Follow the branch and commit conventions.
5. Test your changes before opening a pull request.
6. Never submit real citizens' personal information or confidential evidence in sample data, commits, or test fixtures.

## License

This project currently retains the `ISC` license declaration in `package.json`. Confirm the intended license with the project team and add the corresponding `LICENSE` file before distributing the software.

---

**Durniti Watch Bangladesh**

*Building a more transparent and accountable future through responsible technology.*
