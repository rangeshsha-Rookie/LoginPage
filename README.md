# 🔐 LoginPage

![HTML](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![CSS](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat&logo=nodedotjs&logoColor=white)
![Express](https://img.shields.io/badge/Express.js-000000?style=flat&logo=express&logoColor=white)
![Status](https://img.shields.io/badge/Status-Active-brightgreen)

A full-stack **Login & Authentication System** built with HTML/CSS/JS on the frontend and a Node.js + Express backend — the foundational layer of every secure web application. This project was built to deeply understand the end-to-end authentication pipeline: from input validation, to secure HTTP communication, to session and token-based access control.

> 🧱 **Why this project matters:** Authentication is the entry gate to every full-stack system. Understanding how it works at the implementation level — not just the library level — is what separates surface-level developers from engineers who can reason about security tradeoffs.

---

## ✨ Features

- 🎨 **Responsive Login UI** — Clean, accessible form that adapts across all screen sizes
- 🔒 **Client-Side Validation** — JavaScript-powered input validation (email format, empty field checks, password length rules) before any server call is made
- 🌐 **Node.js + Express Backend** — REST API handles credential verification and authentication logic server-side
- 🪙 **Session & Token Concepts** — Explores both session-based auth (server-side state) and JWT-style token flows (stateless, header-based)
- 🔑 **Password Security Awareness** — Backend architecture demonstrates where hashing (e.g., bcrypt) and salting belong in the auth pipeline
- 🚫 **Error Handling** — Specific, user-friendly error messages for invalid credentials, empty inputs, and server errors
- 📡 **Async Fetch API** — Frontend communicates with backend using `fetch()` + `async/await`, no third-party HTTP library needed

---

## 🏗️ Authentication Architecture

```
┌──────────────────────────────────────────────────────┐
│                     CLIENT SIDE                      │
│                                                      │
│  index.html → input fields → script.js validation   │
│           ↓                                          │
│  fetch('/api/login', { method: 'POST', body: ... })  │
└──────────────────────┬───────────────────────────────┘
                       │ HTTPS / HTTP
┌──────────────────────▼───────────────────────────────┐
│                     SERVER SIDE                      │
│                                                      │
│  Express Route → Credential Check → Response         │
│                                                      │
│  Auth Flows Explored:                                │
│  ┌─────────────────────┐  ┌──────────────────────┐  │
│  │  Session-Based Auth │  │  JWT Token Flow      │  │
│  │  (server stores     │  │  (stateless, client  │  │
│  │   session data)     │  │   holds signed token)│  │
│  └─────────────────────┘  └──────────────────────┘  │
└──────────────────────────────────────────────────────┘
```

---

## 🗂️ Project Structure

```
LoginPage/
├── index.html        # Login form UI — semantic HTML, accessible markup
├── style.css         # Responsive styling, form states, error/success classes
├── script.js         # Frontend validation, fetch() call, UI state management
├── backend/
│   └── server.js     # Express server, route handlers, auth logic, error responses
└── .gitignore
```

---

## 🚀 Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) v16+
- A modern web browser

### 1. Clone the Repository

```bash
git clone https://github.com/rangeshsha-Rookie/LoginPage.git
cd LoginPage
```

### 2. Start the Backend

```bash
cd backend
npm install
node server.js
```

> Server starts at `http://localhost:3000`

### 3. Open the Frontend

```bash
# Open index.html directly, or use a local dev server:
npx serve .
```

---

## 🧠 How It Works — Step by Step

| Step | Layer | What Happens |
|------|-------|--------------|
| 1 | Frontend | User fills the login form (`index.html`) |
| 2 | Frontend | `script.js` validates: empty fields, email regex, password length |
| 3 | Frontend | `fetch()` sends a `POST` request with credentials to `/api/login` |
| 4 | Backend | Express route receives the request, checks credentials against stored data |
| 5 | Backend | On success: returns auth token / session confirmation |
| 6 | Backend | On failure: returns descriptive error (wrong password, user not found) |
| 7 | Frontend | `script.js` reads the response and updates the UI accordingly |

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | HTML5, CSS3, Vanilla JavaScript |
| Backend | Node.js, Express.js |
| Auth Concepts | Session-based auth, JWT token flow, bcrypt hashing |
| HTTP | `fetch()` API + `async/await`, REST conventions |
| Validation | Client-side JS regex + Server-side checks |

---

## 🔐 Security Concepts Learned

Building this project from scratch — without using auth libraries — forced a deep understanding of:

- **Why client-side validation alone is never enough** — it's UX sugar; the server must independently verify every input
- **Session vs. JWT tradeoffs** — sessions are stateful and revocable; JWTs are stateless and scalable but harder to invalidate
- **Where password hashing belongs** — plaintext passwords must never hit the database; `bcrypt` hashing with salt happens server-side before any write
- **HTTP vs. HTTPS and credential exposure** — why credentials over plain HTTP in production are a critical vulnerability
- **CORS in full-stack development** — why a browser blocks cross-origin `fetch()` calls and how `Access-Control-Allow-Origin` headers fix it
- **401 vs. 403** — understanding the difference between "not authenticated" and "not authorized" and when to return each

---

## 🔗 Where This Fits in My Full-Stack Journey

This project is the **security and auth layer** of a larger full-stack picture:

```
LoginPage (Auth & Security)  ──→  DailyDost (Full App with Auth)  ──→  PhishGuard (AI Security Layer)
     ↓                                     ↓                                    ↓
 Understanding the           Applying auth in a real               Extending security to
 auth pipeline               production-ready app                  AI-powered threat detection
```

Each project builds on the auth and backend knowledge established here.

---

## 👨‍💻 Author

**Rangesh Gupta**
- GitHub: [@rangeshsha-Rookie](https://github.com/rangeshsha-Rookie)
- LinkedIn: [in/rangesh-gupta](https://linkedin.com/in/rangesh-gupta)
- 🎓 B.E. Computer Engineering (Data Science) @ SLRTCE '29
- 🌟 Google Student Ambassador 2026 | AI Builder | Data Analyst

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
