# AI Resume Builder 🚀

An intelligent, full-stack web application designed to help job seekers create, customize, and optimize professional resumes effortlessly. Powered by modern web technologies and OpenAI's language models, this application provides AI-assisted content refinement, automated resume parsing from PDFs, dynamic template switching, and real-time live preview with custom color themes.

---

## ✨ Features

- **🤖 AI-Powered Enhancements**
  - **Professional Summary Generator:** Enhance rough draft summaries into polished, impactful professional statements with OpenAI.
  - **Job Description & Achievement Polish:** Automatically rewrite and format work experience bullet points for maximum recruiter impact.
  - **Smart PDF Resume Import:** Upload an existing PDF resume to extract and auto-populate all builder sections automatically.

- **🎨 Dynamic Templates & Customization**
  - Multiple professional resume designs:
    - *Classic Template*
    - *Modern Template*
    - *Minimal Template*
    - *Minimal Image Template*
  - **Live Accent Color Picker:** Customize resume branding with live, real-time color updates.
  - **Photo Uploads:** Cloud image hosting for profile pictures powered by ImageKit.

- **📝 Comprehensive Resume Sections**
  - Personal Information & Contact Details
  - Professional Summary
  - Work Experience & Employment History
  - Education & Degrees
  - Featured Projects & Live Links
  - Skills & Proficiencies

- **🌐 Public Sharing & PDF Export**
  - Generate unique, shareable public links for any resume.
  - Clean browser print and PDF export ready for job applications.

- **🔒 Authentication & User Dashboard**
  - Secure JWT authentication with bcrypt password hashing.
  - Central dashboard to create, manage, preview, duplicate, and delete multiple resumes.

---

## 🛠️ Tech Stack

### Frontend
- **Framework:** React 19 + Vite
- **Styling:** Tailwind CSS v4
- **State Management:** Redux Toolkit
- **Routing:** React Router v7
- **Icons & UI:** Lucide React, React Hot Toast
- **PDF Extraction:** `react-pdftotext`
- **HTTP Client:** Axios

### Backend
- **Runtime:** Node.js & Express 5
- **Database:** MongoDB (via Mongoose ODM)
- **Authentication:** JSON Web Tokens (JWT) + Bcrypt
- **File Uploads:** Multer
- **Cloud Storage:** ImageKit Node.js SDK
- **AI Integration:** OpenAI API

---

## 📁 Project Structure

```text
resume-builder/
├── client/                     # Frontend React application
│   ├── public/                 # Static assets & icons
│   ├── src/
│   │   ├── app/                # Redux store & authentication slices
│   │   ├── assets/             # Images, SVGs, dummy profiles
│   │   ├── components/         # Builder form sections, templates, home UI
│   │   │   ├── home/           # Landing page sections (Hero, Features, Testimonials)
│   │   │   └── templates/      # Resume layout templates (Classic, Modern, Minimal, etc.)
│   │   ├── configs/            # Axios API client configuration
│   │   └── pages/              # Route pages (Home, Dashboard, ResumeBuilder, Preview, Login)
│   ├── .env.example            # Client environment template
│   ├── package.json
│   └── vite.config.js
│
├── server/                     # Backend Node/Express API
│   ├── configs/                # MongoDB, ImageKit, OpenAI, and Multer configs
│   ├── controllers/            # User, Resume, and AI business logic
│   ├── middlewares/            # JWT authentication middleware
│   ├── models/                 # Mongoose schemas (User, Resume)
│   ├── routes/                 # Express API routes (users, resumes, ai)
│   ├── .env.example            # Server environment template
│   ├── package.json
│   └── server.js               # Application entry point
│
├── .gitignore
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites
- [Node.js](https://nodejs.org/) (v18.0.0 or higher recommended)
- [MongoDB](https://www.mongodb.com/) (Local instance or MongoDB Atlas cluster)
- [OpenAI API Key](https://platform.openai.com/)
- [ImageKit Account](https://imagekit.io/) (for profile image uploads)

---

### Environment Setup

#### 1. Server Configuration
Navigate to `server/` and create your `.env` file based on `.env.example`:

```bash
cd server
cp .env.example .env
```

Configure the following variables in `server/.env`:

```env
PORT=5000
JWT_SECRET=your_jwt_secret_key
MONGODB_URI=your_mongodb_connection_string
IMAGEKIT_PRIVATE_KEY=your_imagekit_private_key
OPENAI_API_KEY=your_openai_api_key
OPENAI_BASE_URL=https://api.openai.com/v1
OPENAI_MODEL=gpt-4o-mini
```

#### 2. Client Configuration
Navigate to `client/` and create your `.env` file based on `.env.example`:

```bash
cd ../client
cp .env.example .env
```

Configure `client/.env`:

```env
VITE_BASE_URL=http://localhost:5000
```

---

### Installation & Running

#### 1. Start Backend Server
```bash
cd server
npm install
npm run server     # Starts with nodemon for hot-reloading
# or: npm start
```
The server will run on `http://localhost:5000`.

#### 2. Start Frontend Client
```bash
cd client
npm install
npm run dev
```
Open your browser and navigate to `http://localhost:5173`.

---

## 🔌 API Endpoints Summary

### Authentication (`/api/users`)
- `POST /register` – Register a new user account
- `POST /login` – Authenticate user and receive JWT token
- `GET /data` – Fetch authenticated user profile
- `GET /resumes` – Fetch all resumes created by the user

### Resume Management (`/api/resumes`)
- `POST /create` – Create a new resume record
- `PUT /update` – Update resume details, sections, and profile image
- `DELETE /delete/:resumeId` – Remove a resume
- `GET /get/:resumeId` – Retrieve authenticated user's resume
- `GET /public/:resumeId` – Public view endpoint for sharing

### AI Services (`/api/ai`)
- `POST /enhance-pro-sum` – Enhance professional summary using AI
- `POST /enhance-job-desc` – Refine work experience bullet points
- `POST /upload-resume` – Convert extracted PDF resume text into structured builder data

---

## 📄 License

This project is licensed under the [ISC License](LICENSE).
