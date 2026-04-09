# AI Interview Prep 🚀

AI Interview Prep is a full-stack application that helps users prepare for interviews using AI-generated interview strategy reports.

The app includes:
- A React + Vite frontend for authentication, report generation, and viewing interview plans.
- A Node.js + Express backend with MongoDB for auth, persistence, and AI-powered analysis.
- Google Gemini integration to generate interview questions, skill-gap analysis, and preparation plans.

## Architecture 🏗️

- Frontend: React 19, React Router, Axios, Sass, Vite
- Backend: Express 5, Mongoose, JWT, Cookie-based auth, Multer
- AI/Docs: Google GenAI SDK, Zod schema validation, PDF parsing and PDF generation
- Database: MongoDB

Project structure:

```text
Backend/
  server.js
  src/
    app.js
    config/
    controllers/
    middlewares/
    models/
    routes/
    services/
Frontend/
  src/
    features/
      auth/
      interview/
```

## Core Features ✨

- User registration, login, logout, and current-user session check
- Protected routes on frontend for authenticated users
- Upload resume (PDF) or provide self-description
- Generate interview report from:
  - Job description
  - Resume text and/or self-description
- Report includes:
  - Match score
  - Technical questions with intention and answer strategy
  - Behavioral questions with intention and answer strategy
  - Skill gaps with severity
  - Day-wise preparation plan
- Generate downloadable resume PDF from saved report context
- View previous reports from dashboard/home list

## Prerequisites ✅

- Node.js 18+
- npm 9+
- MongoDB instance (local or cloud)
- Google AI API key

## Environment Variables 🔐

Create `Backend/.env`:

```env
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_strong_jwt_secret
GOOGLE_GENAI_API_KEY=your_google_genai_api_key
```

## Installation 📦

Install backend dependencies:

```bash
cd Backend
npm install
```

Install frontend dependencies:

```bash
cd ../Frontend
npm install
```

## Run Locally ▶️

Run backend (Terminal 1):

```bash
cd Backend
npm run dev
```

Backend default: `http://localhost:3000`

Run frontend (Terminal 2):

```bash
cd Frontend
npm run dev
```

Frontend default: `http://localhost:5173`

## API Overview 🔌

Base URL: `http://localhost:3000`

Auth routes:
- `POST /api/auth/register`
- `POST /api/auth/login`
- `GET /api/auth/logout`
- `GET /api/auth/get-me` (protected)

Interview routes (protected):
- `POST /api/interview/` (multipart form-data with `resume`, `jobDescription`, `selfDescription`)
- `GET /api/interview/`
- `GET /api/interview/report/:interviewId`
- `POST /api/interview/resume/pdf/:interviewReportId`

## Notes 📝

- Frontend API clients are currently configured to call `http://localhost:3000`.
- Backend CORS is configured for `http://localhost:5173` with credentials enabled.
- Auth token is stored in cookies and validated with JWT on protected routes.

## Scripts ⚙️

Backend (`Backend/package.json`):
- `npm run dev` - start backend with nodemon

Frontend (`Frontend/package.json`):
- `npm run dev` - start Vite dev server
- `npm run build` - create production build
- `npm run preview` - preview production build
- `npm run lint` - run ESLint

## Troubleshooting 🛠️

- If login/session fails:
  - Ensure backend is running on port 3000
  - Ensure frontend is running on port 5173
  - Verify CORS and cookies are enabled in browser
- If report generation fails:
  - Check `GOOGLE_GENAI_API_KEY`
  - Verify MongoDB connectivity via `MONGO_URI`
- If file upload fails:
  - Ensure `resume` is sent as form-data


