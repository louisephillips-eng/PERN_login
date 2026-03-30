# PERN Auth App

A full-stack authentication application built with PostgreSQL, Express, React, and Node.js. Supports user registration and login with JWT-based authentication via HTTP-only cookies.

---

## Tech Stack

**Frontend**
- React (Vite)
- React Router

**Backend**
- Node.js & Express
- PostgreSQL (`pg`)
- bcryptjs (password hashing)
- jsonwebtoken (JWT)
- cookie-parser
- cors

---

## Features

- User registration with hashed passwords
- User login with JWT stored in HTTP-only cookie
- Protected routes via auth middleware
- Logout (clears cookie)
- `/me` endpoint to fetch authenticated user

---

## Project Structure

```
├── client/                 # React frontend (Vite)
│   └── src/
│       └── App.jsx
├── server/                 # Express backend
│   ├── config/
│   │   └── db.js           # PostgreSQL pool
│   ├── middleware/
│   │   └── auth.js         # JWT protect middleware
│   ├── routes/
│   │   └── auth.js         # Auth routes
│   └── server.js           # Entry point
├── .env
├── .gitignore
└── README.md
```

---

## Getting Started

### Prerequisites

- Node.js v18+
- PostgreSQL running locally

### 1. Clone the repo

```bash
git clone https://github.com/your-username/your-repo.git
cd your-repo
```

### 2. Install dependencies

```bash
# Backend
cd server
npm install

# Frontend
cd ../client
npm install
```

### 3. Set up environment variables

Create a `.env` file in the `server/` directory:

```env
PORT=5000
CLIENT_URL=http://localhost:5173
JWT_SECRET=your_jwt_secret_here
DATABASE_URL=postgresql://your_user:your_password@localhost:5432/your_db
```

### 4. Set up the database

```sql
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(150) UNIQUE NOT NULL,
    password TEXT NOT NULL
);
```

### 5. Run the app

```bash
# Terminal 1 — backend
cd server
npm run dev

# Terminal 2 — frontend
cd client
npm run dev
```

- Backend: `http://localhost:5000`
- Frontend: `http://localhost:5173`

---

## API Endpoints

| Method | Endpoint            | Access    | Description              |
|--------|---------------------|-----------|--------------------------|
| POST   | `/api/auth/register`| Public    | Register a new user      |
| POST   | `/api/auth/login`   | Public    | Login and set cookie     |
| GET    | `/api/auth/me`      | Protected | Get logged-in user       |
| POST   | `/api/auth/logout`  | Protected | Logout and clear cookie  |

---

## Environment Variables

| Variable       | Description                        |
|----------------|------------------------------------|
| `PORT`         | Port for the Express server        |
| `CLIENT_URL`   | Frontend URL (for CORS)            |
| `JWT_SECRET`   | Secret key for signing JWTs        |
| `DATABASE_URL` | PostgreSQL connection string       |
