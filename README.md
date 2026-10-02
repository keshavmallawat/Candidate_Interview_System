# Candidate Interview System

An AI-assisted technical interview platform built on the MERN stack. Candidates sign in, tell the system which languages and technologies they know, and take an interview made of generated multiple-choice and subjective questions. Answers are scored automatically and kept in a per-candidate history.

> Team project. I worked on roughly half of it; this repository is my copy of the shared codebase.

## Features

- **Generated questions.** The backend asks Gemini (`gemini-2.5-flash`) for a mix of MCQ and subjective questions for each technology a candidate lists, at the difficulty stored on their profile.
- **Automatic scoring.** MCQs are checked directly. Subjective answers are compared with a reference answer by the LLM, and a similarity score at or above a configurable threshold earns the mark. Failed evaluations are retried.
- **Authentication.** Username/password and Google sign-in, with JWTs kept in cookies and a token refresh route.
- **Candidate dashboard.** Profile details, interview history and per-interview results.
- **Admin area.** Role-gated page to list and remove users.

## Tech stack

| Layer | Tools |
| --- | --- |
| Frontend | React 19 (Create React App), React Router 7, Axios, `@react-oauth/google`, React Window |
| Backend | Node.js (ES modules), Express 5, official MongoDB driver, `jsonwebtoken`, `cookie-parser`, CORS |
| AI | Google Gen AI SDK (`@google/genai`) |

## Project structure

```text
backend/
  server.js            Express app and route mounting
  routes/
    auth.js            login, Google login, token refresh, logout, user creation
    dash.js            profile details and interview history
    interview.js       question generation, answer submission, scoring
    admin_routes.js    user listing and removal (admin only)
    Verify_cookies.js  JWT cookie middleware
  sample_questions.json  example of the generated question format
frontend/
  src/                 pages: Login, Dash, Details, Interview, Hist, Admin, AddUser
```

## Getting started

Requirements: Node.js 18 or newer, a MongoDB instance (local or Atlas), a Google Gen AI API key and a Google OAuth client ID.

### Backend

```bash
cd backend
npm install
```

Create `backend/.env.local`:

| Variable | Purpose |
| --- | --- |
| `MONGO_URI` | MongoDB connection string |
| `JWT_SECRET` | Secret used to sign tokens |
| `CLIENT_URL` | Frontend origin allowed by CORS, for example `http://localhost:3000` |
| `API_KEY` | Google Gen AI API key |
| `NO_QUESTIONS` | Questions per interview (optional, default 5) |
| `RATIO` | Share of MCQs, from 0 to 1 (optional, default 0.5) |
| `LLM_SIMILARITY` | Similarity needed to mark a subjective answer correct (optional, default 0.8) |

```bash
node server.js     # listens on http://localhost:5000
```

### Frontend

```bash
cd frontend
npm install
```

Create `frontend/.env`:

```bash
REACT_APP_API_URI=http://localhost:5000
REACT_APP_GOOGLE_CLIENT_ID=your-google-client-id
```

```bash
npm start          # http://localhost:3000
```

## API overview

| Method | Route | Description |
| --- | --- | --- |
| POST | `/login`, `/glogin` | Sign in with credentials or a Google token |
| GET | `/token`, `/refresh`, `/logout` | Session helpers |
| GET | `/check-username` | Username availability |
| POST | `/add-user` | Create a user |
| GET | `/check-hist`, `/check-details` | Interview history and profile |
| POST | `/update-details` | Save languages, technologies and difficulty |
| GET | `/generate/:id` | Generate questions for one of the candidate's topics |
| POST | `/submit` | Submit answers for scoring |
| GET | `/score/:id` | Fetch an interview's score |
| GET | `/get-users` | List users (admin) |
| POST | `/delete-user` | Remove a user (admin) |

Protected routes expect the session cookie issued at login.

## Status

Built as a university project and still a work in progress. There is no automated test suite for the backend yet, and no licence has been chosen, so all rights are reserved.
