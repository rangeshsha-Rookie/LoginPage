<div align="center">

# 🔐 LoginPage — Full-Stack Authentication System

### JWT · bcrypt · MongoDB · Express · REST API

[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)](https://nodejs.org/)
[![Express](https://img.shields.io/badge/Express-000000?style=for-the-badge&logo=express&logoColor=white)](https://expressjs.com/)
[![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white)](https://www.mongodb.com/)
[![JWT](https://img.shields.io/badge/JWT-000000?style=for-the-badge&logo=jsonwebtokens&logoColor=white)](https://jwt.io/)
[![bcrypt](https://img.shields.io/badge/bcrypt-red?style=for-the-badge)](https://www.npmjs.com/package/bcryptjs)

> A production-ready full-stack authentication system implementing industry-standard security patterns — JWT session management, bcrypt password hashing, RESTful auth routes, and MongoDB user persistence — built as a foundational module for larger full-stack applications.

</div>

---

## 📋 Table of Contents

- [About](#-about)
- [Architecture](#-architecture)
- [Security Implementation](#-security-implementation)
- [Tech Stack](#-tech-stack)
- [API Reference](#-api-reference)
- [Getting Started](#-getting-started)
- [Project Structure](#-project-structure)
- [Security Concepts Learned](#-security-concepts-learned)
- [Author](#-author)

---

## 🧠 About

**LoginPage** is more than a UI form — it's a full-stack authentication module that explores the real mechanics behind secure user identity systems. The project implements the complete auth lifecycle from user registration to protected session management using JWT tokens and hashed credentials.

This project was built to deeply understand how modern web applications handle authentication before applying these patterns in larger projects like [DailyDost](https://github.com/rangeshsha-Rookie/DailyDost) and [PhishGuard India](https://github.com/rangeshsha-Rookie/PhishGuard-India-UPI-Fraud-Detection).

---

## 🏗 Architecture

```
┌─────────────────────────────────────────────────────────┐
│                     CLIENT (Browser)                     │
│   index.html  ←→  script.js  ←→  style.css              │
│         │                                                │
│   POST /api/auth/register  |  POST /api/auth/login       │
└──────────────────┬──────────────────────────────────────┘
                   │  HTTP + JWT Bearer Token
┌──────────────────▼──────────────────────────────────────┐
│                  BACKEND (Node.js + Express)              │
│                                                          │
│  server.js                                               │
│      │                                                   │
│      ├── routes/auth.js    ← Register & Login routes     │
│      │       │                                           │
│      │       ├── bcryptjs  ← Password hashing (salt x10)│
│      │       └── jsonwebtoken ← Token sign & verify     │
│      │                                                   │
│      └── models/User.js   ← Mongoose schema              │
│              │                                           │
└──────────────┼──────────────────────────────────────────┘
               │  Mongoose ODM
┌──────────────▼──────────────────────────────────────────┐
│               MongoDB Atlas (Cloud Database)              │
│    Collection: users { _id, email, passwordHash, ... }   │
└─────────────────────────────────────────────────────────┘
```

---

## 🔒 Security Implementation

This project implements five core security layers found in production authentication systems:

| Security Layer | Implementation | Purpose |
|---|---|---|
| **Password Hashing** | `bcryptjs` with salt rounds | Passwords never stored as plaintext |
| **JWT Tokens** | `jsonwebtoken` — sign + verify | Stateless session management |
| **Environment Secrets** | `dotenv` — `.env` for JWT_SECRET | Sensitive config never in source code |
| **CORS Policy** | `cors` middleware on Express | Controlled cross-origin access |
| **MongoDB Schema Validation** | Mongoose model constraints | Data integrity at the DB layer |

### JWT Flow

```
1. User registers → password bcrypt-hashed → user saved to MongoDB
2. User logs in  → password compared via bcrypt.compare()
3. Match found   → JWT signed with JWT_SECRET → token returned to client
4. Client stores token → sends as Authorization: Bearer <token> header
5. Protected routes → middleware verifies token → grants/denies access
```

---

## 🛠 Tech Stack

| Layer | Technology | Version |
|---|---|---|
| **Frontend** | HTML5, CSS3, Vanilla JavaScript | — |
| **Backend Runtime** | Node.js | LTS |
| **Web Framework** | Express.js | v5.1.0 |
| **Database** | MongoDB (via Mongoose ODM) | v8.19.3 |
| **Auth — Tokens** | jsonwebtoken (JWT) | v9.0.2 |
| **Auth — Hashing** | bcryptjs | v3.0.3 |
| **Config Management** | dotenv | v17.2.3 |
| **CORS** | cors middleware | v2.8.5 |

---

## 📡 API Reference

### `POST /api/auth/register`
Register a new user.

**Request Body:**
```json
{
  "email": "user@example.com",
  "password": "yourpassword"
}
```

**Response (201):**
```json
{
  "message": "User registered successfully",
  "token": "<jwt_token>"
}
```

---

### `POST /api/auth/login`
Authenticate an existing user.

**Request Body:**
```json
{
  "email": "user@example.com",
  "password": "yourpassword"
}
```

**Response (200):**
```json
{
  "message": "Login successful",
  "token": "<jwt_token>"
}
```

---

## 🚀 Getting Started

### Prerequisites

```bash
node >= 16.x
npm
MongoDB Atlas URI (free tier works)
```

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/rangeshsha-Rookie/LoginPage.git
cd LoginPage

# 2. Install backend dependencies
cd backend
npm install

# 3. Create environment file
cp .env.example .env
# Add: MONGO_URI=your_mongodb_atlas_uri
# Add: JWT_SECRET=your_secret_key
# Add: PORT=5000

# 4. Start the backend server
node server.js
```

Open `index.html` directly in your browser or use Live Server extension.

---

## 📁 Project Structure

```
LoginPage/
├── index.html              ← Login/Register UI
├── script.js               ← Frontend API calls & token handling
├── style.css               ← UI styling
│
└── backend/
    ├── server.js           ← Express app entry point
    ├── routes/
    │   └── auth.js         ← Register & Login route handlers
    ├── models/
    │   └── User.js         ← Mongoose User schema
    └── package.json        ← Dependencies (JWT, bcrypt, mongoose, cors)
```

---

## 🎓 Security Concepts Learned

Building this project developed hands-on understanding of core authentication engineering principles:

- **Why passwords must never be stored as plaintext** — and how bcrypt's cost factor + salt prevents rainbow table attacks
- **Stateless vs. stateful session management** — JWT eliminates server-side session storage entirely
- **Token anatomy** — Header (alg) · Payload (claims) · Signature (HMAC-SHA256) — and why only the server can issue valid tokens
- **Environment variable hygiene** — separating secrets from source code via `.env` and `.gitignore`
- **Schema-level validation** — using Mongoose to enforce data integrity before writing to the database
- **CORS and API security** — controlling which origins can call the backend

These patterns are directly applied in production-grade projects like [PhishGuard India](https://github.com/rangeshsha-Rookie/PhishGuard-India-UPI-Fraud-Detection) (threat scoring API) and [DailyDost](https://github.com/rangeshsha-Rookie/DailyDost) (user authentication module).

---

## 👤 Author

**Rangesh Gupta**

- 🐙 GitHub: [@rangeshsha-Rookie](https://github.com/rangeshsha-Rookie)
- 💼 LinkedIn: [in/rangesh-gupta](https://linkedin.com/in/rangesh-gupta)
- 🎓 B.E. Computer Engineering (Data Science) @ SLRTCE '29
- 🌟 Google Student Ambassador 2026 | AI Builder | Data Analyst

---

<div align="center">

Part of a full-stack authentication learning series · Foundation for production projects

⭐ **Star this repo if you found it useful!**

</div>
