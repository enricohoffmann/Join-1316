# Join – Kanban Project Management App

A collaborative Kanban-style task management application built with vanilla JavaScript and Firebase. Organize your work across customizable board columns, manage contacts, and track progress — all in real time.

---

## Table of Contents

- [About the Project](#about-the-project)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Getting Started](#getting-started)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [License](#license)

---

## About the Project

**Join** is a full-featured web application inspired by tools like Trello. It allows teams to create tasks, assign them to contacts, prioritize work, and move tasks through a visual Kanban board — from *To Do* all the way to *Done*.

This project was developed as part of my web development training at the [Developer Akademie](https://developerakademie.com/). It demonstrates a complete multi-page JavaScript application without any frontend framework, using Firebase as the backend.

---

## Features

- **Authentication** — Email/password login, user registration, and guest access
- **Summary Dashboard** — At-a-glance overview of task counts by status, deadline highlights, and a personalized time-of-day greeting
- **Kanban Board** — Four columns: *To Do*, *In Progress*, *Awaiting Feedback*, *Done*
  - Drag-and-drop to move tasks between columns (position persisted to Firebase)
  - Real-time search/filter across all task cards
  - Click a card to open a detailed view with subtask checkboxes
  - Edit tasks inline from the detail view
- **Add Task** — Rich task creation form with title, description, due date, priority (Urgent / Medium / Low), category (Technical Task / User Story), multi-contact assignment, and subtasks
- **Contacts** — Full CRUD contact management, sorted alphabetically with color-coded avatar initials
- **Responsive Design** — Separate desktop and mobile layouts, dynamically swapped at runtime based on viewport width; landscape-mode protection on mobile devices
- **Legal Pages** — Help, Privacy Policy, and Legal Notice

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | Vanilla HTML, CSS, JavaScript (ES6) |
| Backend / Database | Firebase Realtime Database |
| Authentication | Firebase Authentication (anonymous + email/password) |
| Firebase SDK | v10.12.0 (CDN) |
| Fonts | Inter, Mulish, Open Sans (self-hosted) |
| Documentation | JSDoc |

No build tools or package managers are required — the project runs directly in the browser.

---

## Getting Started

### Prerequisites

- A modern web browser (Chrome, Firefox, Edge, Safari)
- A Firebase project with **Realtime Database** and **Authentication** enabled
- A local web server (e.g. VS Code [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer)) — required because the app uses `fetch()` to load HTML partials

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/join-1316.git
   cd join-1316
   ```

2. **Configure Firebase**

   Open `config/firebaseConfig.js` and replace the placeholder values with your own Firebase project credentials:
   ```js
   const firebaseConfig = {
     apiKey: "YOUR_API_KEY",
     authDomain: "YOUR_PROJECT.firebaseapp.com",
     databaseURL: "https://YOUR_PROJECT-default-rtdb.europe-west1.firebasedatabase.app",
     projectId: "YOUR_PROJECT",
     storageBucket: "YOUR_PROJECT.appspot.com",
     messagingSenderId: "YOUR_SENDER_ID",
     appId: "YOUR_APP_ID"
   };
   ```

3. **Set Firebase Security Rules**

   In the Firebase Console, set your Realtime Database rules to allow authenticated reads/writes. A minimal development ruleset:
   ```json
   {
     "rules": {
       ".read": "auth != null",
       ".write": "auth != null"
     }
   }
   ```

4. **Serve the project**

   Open the project folder with a local web server and navigate to `index.html` in your browser.

---

## Usage

1. **Log in** with an existing account or use *Guest Login* to explore without an account
2. **Add tasks** via the *Add Task* page or directly from the board using the `+` button in any column
3. **Assign contacts** to tasks — manage your team members under the *Contacts* page first
4. **Organize on the board** — drag cards between columns as work progresses
5. **Track progress** on the *Summary* dashboard

---

## Project Structure

```
join-1316/
├── index.html                  # Login page
├── signup.html                 # Registration page
├── summary.html                # Dashboard
├── board.html                  # Kanban board
├── addTask.html                # Add task page
├── contacts.html               # Contacts overview
├── app.js                      # HTML partial loader (includeHtml)
├── script.js                   # Shared utilities & auth guard
├── style.css                   # Global styles
│
├── classes/                    # Core application logic
│   ├── models.js               # Data models (Task, Subtask, Contact, …)
│   ├── firebaseDatabase.js     # Firebase wrapper (CRUD operations)
│   ├── taskComponents.*.js     # Add/Edit task form logic (split via mixins)
│   ├── addTaskCache.js         # Task form state management
│   ├── boardTaskDetail*.js     # Board detail view / edit / delete logic
│   └── …
│
├── scripts/                    # Page-specific scripts
│   ├── addEditContacts.js      # Contact CRUD
│   ├── boardSearch.js          # Board search/filter
│   ├── dragAndDrop.js          # Drag-and-drop functionality
│   ├── summary.js              # Dashboard logic
│   └── …
│
├── config/
│   └── firebaseConfig.js       # Firebase project configuration
│
├── assets/                     # Images, icons
├── fonts/                      # Self-hosted web fonts
└── jsdocs/                     # Generated JSDoc documentation
```

---

## License

This project was created for educational purposes as part of the [Developer Akademie](https://developerakademie.com/) curriculum. Feel free to use it as a reference or learning resource.
