# AI Career Platform

An AI-powered career guidance platform that helps students and job seekers discover career opportunities through personalised recommendations, resume analysis, skill-gap identification, and structured learning paths.

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | React 19, Vite 8, Tailwind CSS 4 |
| Backend | Node.js 22, Express 5, Mongoose / MongoDB |
| AI Service | Python 3.12, FastAPI, PyTorch, Sentence-Transformers, spaCy, XGBoost |

## Features

- **AI Career Guidance** — ranked career matches based on skills and profile
- **Resume Analyzer** — parse PDF/DOCX resumes, extract skills, score quality
- **Skill Gap Analysis** — radar chart of matched vs missing skills
- **Learning Paths** — weekly plans with recommended courses
- **Mock Interviews** — AI-generated questions with semantic answer scoring
- **Job Recommendations** — skill-matched openings with match percentage
- **Placement Drives** — eligibility check and one-click apply
- **Assessments** — topic-wise quizzes with score history
- **Certificates** — upload, verify, and showcase certifications

## Project Structure

```
AI-Career-platform/
├── ai-service/            # Python FastAPI — resume parsing & answer scoring
│   ├── app/
│   │   ├── main.py        # FastAPI entry point
│   │   ├── score_answer.py
│   │   ├── security.py
│   │   └── services/
│   │       └── resume_parser.py
│   └── requirements.txt
├── backend/               # Node.js Express API
│   ├── config/            # MongoDB connection
│   ├── controllers/       # Route handlers
│   ├── data/              # Seed data (careers, jobs, questions)
│   ├── middleware/         # Auth, file upload
│   ├── models/            # Mongoose schemas
│   ├── routes/            # API route definitions
│   ├── scripts/           # Database seed scripts
│   ├── services/          # AI service client
│   ├── utils/             # Matchers, scorers, helpers
│   └── server.js          # Express entry point
├── frontend/              # React SPA
│   ├── public/
│   └── src/
│       ├── components/    # Layout, Sidebar, ProtectedRoute
│       ├── config/        # Navigation config
│       ├── pages/         # All page components
│       └── services/      # Axios API client
├── docker-compose.yml     # Full-stack Docker setup
└── README.md
```

## Prerequisites

- **Node.js** ≥ 18 and npm
- **Python** ≥ 3.10 and pip
- **MongoDB** running locally on port 27017 (or a remote URI)

## Quick Start

### 1. Clone & enter the project

```bash
git clone https://github.com/roshini-official/AI-Career-platform.git
cd AI-Career-platform
```

### 2. Configure environment variables

Copy the example files and edit as needed:

```bash
cp backend/.env.example  backend/.env
cp ai-service/.env.example  ai-service/.env
cp frontend/.env.example  frontend/.env
```

> **Important:** The `AI_SERVICE_SECRET` value must match in both `backend/.env` and `ai-service/.env`.

### 3. Install dependencies (all three services)

```bash
# Backend
cd backend && npm install && cd ..

# Frontend
cd frontend && npm install && cd ..

# AI Service
cd ai-service && pip install -r requirements.txt && cd ..
```

### 4. Run the project (three terminals)

**Terminal 1 — Backend (port 5000):**
```bash
cd backend
npm run dev
```

**Terminal 2 — AI Service (port 8000):**
```bash
cd ai-service
python -m uvicorn app.main:app --host 127.0.0.1 --port 8000
```

**Terminal 3 — Frontend (port 5173):**
```bash
cd frontend
npm run dev
```

Open **http://localhost:5173** in your browser.

### 5. (Optional) Seed the database

```bash
cd backend
npm run seed:careers
npm run seed:jobs
npm run seed:questions
npm run seed:assessments
npm run seed:drives
```

## Docker

Alternatively, run everything with Docker Compose:

```bash
# Create a root .env with your secrets
echo "JWT_SECRET=changeme" > .env
echo "AI_SERVICE_SECRET=changeme" >> .env

docker compose up --build
```

The frontend will be at `http://localhost:8080` and the API at `http://localhost:5000`.

## API Endpoints

| Service | Endpoint | Description |
|---------|----------|-------------|
| Backend | `GET /` | Health check |
| Backend | `POST /api/auth/register` | User registration |
| Backend | `POST /api/auth/login` | User login |
| Backend | `GET /api/careers/recommendations` | Career recommendations |
| Backend | `POST /api/resume/upload` | Resume upload & analysis |
| Backend | `GET /api/jobs` | Job recommendations |
| AI Service | `GET /health` | AI service health check |
| AI Service | `POST /ai/parse-resume` | Resume text extraction |
| AI Service | `POST /ai/score-answer` | Semantic answer scoring |

## Author

**Omkar A Temkar**
B.E. Computer Science and Engineering
