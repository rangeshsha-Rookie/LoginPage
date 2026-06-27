# 🔐 LoginPage — Full-Stack Authentication System

> **Secure Login & Registration System with JWT Authentication, Password Hashing, and MongoDB Integration**

![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=node.js&logoColor=white)
![Express](https://img.shields.io/badge/Express-000000?style=flat-square&logo=express&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=flat-square&logo=mongodb&logoColor=white)
![JWT](https://img.shields.io/badge/JWT-000000?style=flat-square&logo=jsonwebtokens&logoColor=white)
![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=flat-square)

---

## 📌 Overview

**LoginPage** is a complete full-stack authentication system built from scratch using vanilla JavaScript on the frontend and Node.js + Express on the backend. It implements industry-standard security practices — password hashing with bcrypt, stateless authentication with JWT tokens, and persistent user storage with MongoDB via Mongoose.

This project was built to demonstrate end-to-end auth flow knowledge, from the HTML/CSS/JS frontend all the way through API design, middleware, and database modeling.

---

## ✨ Features

- 🔒 **Secure Password Hashing** — passwords stored using `bcryptjs` (never plain text)
- 🎫 **JWT Authentication** — stateless token-based auth with expiry management
- 📦 **MongoDB Integration** — user data persisted via Mongoose ODM
- 🌐 **CORS Enabled** — cross-origin requests handled cleanly with `cors` middleware
- 🔑 **Environment Variables** — sensitive config managed via `dotenv`
- 📱 **Responsive Frontend** — clean login/register UI with HTML, CSS, and vanilla JS
- 🚦 **API Routes** — structured RESTful routes for auth operations
- 🛡️ **Input Validation** — server-side validation before DB operations

---

## 🗂️ Project Structure

```
LoginPage/
├── index.html          # Frontend login/register page
├── style.css           # Styling for the auth UI
├── script.js           # Frontend JS — form handling, fetch calls, token storage
│
└── backend/
    ├── server.js       # Express app entry point
    ├── package.json    # Dependencies & scripts
    ├── .gitignore      # Node modules & env excluded
    ├── models/         # Mongoose user schema/model
    └── routes/         # Auth route handlers (login, register)
```

---

## 🛠️ Tech Stack

### Frontend
| Technology | Purpose |
|------------|---------|
| HTML5 | Structure — login & registration forms |
| CSS3 | Styling — responsive layout, form design |
| Vanilla JavaScript | Logic — form submission, fetch API calls, JWT token handling |

### Backend
| Package | Version | Purpose |
|---------|---------|--------|
| `express` | ^5.1.0 | Web server & routing framework |
| `mongoose` | ^8.19.3 | MongoDB ODM — schema, model, queries |
| `bcryptjs` | ^3.0.3 | Password hashing & comparison |
| `jsonwebtoken` | ^9.0.2 | JWT generation & verification |
| `cors` | ^2.8.5 | Cross-origin resource sharing |
| `dotenv` | ^17.2.3 | Environment variable management |

---

## ⚙️ Setup & Installation

### Prerequisites
- Node.js v18+
- MongoDB (local or MongoDB Atlas)

### 1. Clone the repository
```bash
git clone https://github.com/rangeshsha-Rookie/LoginPage.git
cd LoginPage
```

### 2. Install backend dependencies
```bash
cd backend
npm install
```

### 3. Configure environment variables
Create a `.env` file in the `backend/` directory:
```env
PORT=5000
MONGO_URI=mongodb://localhost:27017/loginpage
JWT_SECRET=your_super_secret_key_here
JWT_EXPIRES_IN=7d
```

### 4. Start the backend server
```bash
node server.js
# Server running at http://localhost:5000
```

### 5. Open the frontend
Open `index.html` directly in your browser, or serve it with Live Server (VS Code extension).

---

## 🔌 API Endpoints

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| `POST` | `/api/auth/register` | Register a new user | ❌ |
| `POST` | `/api/auth/login` | Login and receive JWT | ❌ |
| `GET` | `/api/auth/profile` | Get authenticated user's profile | ✅ JWT |

### Example: Register
```json
POST /api/auth/register
{
  "username": "rangesh",
  "email": "rangesh@example.com",
  "password": "securepassword123"
}
```

### Example: Login Response
```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "user": {
    "id": "64abc...",
    "username": "rangesh",
    "email": "rangesh@example.com"
  }
}
```

---

## 🔐 Security Practices

- ✅ Passwords hashed with **bcrypt** (salt rounds: 10) — never stored in plain text
- ✅ **JWT tokens** signed with a secret key — stateless, no session storage needed
- ✅ Sensitive keys stored in **`.env`** — never committed to version control
- ✅ **CORS** configured to control allowed origins
- ✅ `node_modules/` excluded via `.gitignore`

---

## 📚 What I Learned

Building this project helped solidify:
- Full-stack request/response flow from browser form → API → database → response
- How `bcryptjs` salt-and-hash works under the hood
- JWT structure (header.payload.signature) and token verification middleware
- Mongoose schema design and async CRUD operations
- Express router architecture for modular API structure
- Environment variable best practices for production-ready code

---

## 👤 Author

**Rangesh Gupta**
- 🎓 B.E. Computer Engineering (Data Science) — SLRTCE, Mumbai (2025–2029)
- 🤖 Google Student Ambassador 2026
- 💼 [LinkedIn](https://linkedin.com/in/rangesh-gupta) | [GitHub](https://github.com/rangeshsha-Rookie)

---

## 📜 License

This project is open source and available under the [MIT License](LICENSE).

---

*Clean auth. Secure by design. 🔐*
