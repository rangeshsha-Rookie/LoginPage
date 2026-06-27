# 🔐 LoginPage

![HTML](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![CSS](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat&logo=nodedotjs&logoColor=white)
![Status](https://img.shields.io/badge/Status-Active-brightgreen)

A clean, responsive **Login Page** with a full-stack architecture — HTML/CSS/JS frontend paired with a Node.js backend for handling authentication logic. Built as a foundational project to understand end-to-end user authentication flows.

---

## ✨ Features

- 🎨 **Responsive UI** — Clean login form that works across all screen sizes
- 🔒 **Frontend Validation** — JavaScript-powered input validation before form submission
- 🌐 **Backend Integration** — Node.js backend in `/backend` folder handles authentication requests
- 💡 **Modular Structure** — Separate `index.html`, `style.css`, and `script.js` for clean separation of concerns
- 🚫 **Error Handling** — User-friendly error messages for invalid credentials

---

## 🗂️ Project Structure

```
LoginPage/
├── index.html        # Login form UI
├── style.css         # Styling and responsive layout
├── script.js         # Frontend validation and form handling
├── backend/          # Node.js backend for auth logic
│   └── server.js     # Express server & route handlers
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

### 2. Run the Backend

```bash
cd backend
npm install
node server.js
```

> Server starts at `http://localhost:3000` (or the configured port).

### 3. Open the Frontend

Open `index.html` directly in your browser, or serve it via a local server:

```bash
# Using VS Code Live Server extension, or:
npx serve .
```

---

## 🧠 How It Works

1. User enters credentials on the login form (`index.html`)
2. `script.js` validates the input client-side (empty fields, email format, etc.)
3. On valid submission, a `fetch()` / `XMLHttpRequest` sends the data to the backend
4. The backend (`/backend/server.js`) verifies credentials and returns a success or error response
5. The frontend displays the appropriate message to the user

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | HTML5, CSS3, Vanilla JavaScript |
| Backend | Node.js, Express.js |
| Validation | Client-side JS + Server-side checks |

---

## 📚 What I Learned

- Structuring a full-stack project from scratch
- Connecting a plain HTML/CSS/JS frontend to a Node.js backend
- Handling form submission with `fetch()` and async/await
- Client-side validation patterns before server communication
- Basic Express.js routing and request/response handling

---

## 👨‍💻 Author

**Rangesh Gupta**
- GitHub: [@rangeshsha-Rookie](https://github.com/rangeshsha-Rookie)
- LinkedIn: [in/rangesh-gupta](https://linkedin.com/in/rangesh-gupta)

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
