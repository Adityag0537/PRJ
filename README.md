# ViBe

ViBe is a full-stack learning platform built with a React/Vite frontend and a Node.js/Express backend. This guide explains how to set up the project for local development.

---

# Tech Stack

### Frontend

* React
* TypeScript
* Vite
* Tailwind CSS
* Firebase Authentication

### Backend

* Node.js
* Express
* TypeScript
* MongoDB
* Firebase Admin SDK

---

# Prerequisites

Install the following before starting:

* Node.js (v20 or later recommended)
* pnpm
* Git
* MongoDB (local or Atlas)
* Firebase project (or access to the team's Firebase project)

Install pnpm:

```bash
npm install -g pnpm
```

Verify:

```bash
pnpm -v
```

---

# Clone the Repository

```bash
git clone https://github.com/Adityag0537/PRJ.git
cd PRJ
```

---

# Install Dependencies

Install backend dependencies:

```bash
cd backend
pnpm install
```

Install frontend dependencies:

```bash
cd ../frontend
pnpm install
```

---

# Environment Configuration

The repository contains example environment files.

## Backend

```bash
cd backend
cp .example.env .env
```

Fill in the required values:

```env
APP_MODULE=all

DB_URL=
DB_NAME=

FIREBASE_PROJECT_ID=
FIREBASE_CLIENT_EMAIL=
FIREBASE_PRIVATE_KEY=
```

---

## Frontend

Create:

```text
frontend/.env
```

using the provided `.env.example`.

Required variables:

```env
VITE_BASE_URL=http://localhost:3141/api

VITE_FIREBASE_API_KEY=
VITE_FIREBASE_AUTH_DOMAIN=
VITE_FIREBASE_PROJECT_ID=
VITE_FIREBASE_STORAGE_BUCKET=
VITE_FIREBASE_MESSAGING_SENDER_ID=
VITE_FIREBASE_APP_ID=
VITE_FIREBASE_MEASUREMENT_ID=

VITE_IS_RECAPTCHA_ENABLED=false
VITE_RECAPTCHA_SITE_KEY=
VITE_E2E_TESTING=false
```

---

# Firebase Setup

The project requires Firebase Authentication.

If your team has an existing Firebase project, use the credentials provided by the maintainers.

Otherwise:

1. Create a Firebase project.
2. Enable **Authentication**.
3. Enable:

   * Email/Password
   * Google
4. Register a Web App.
5. Copy the Firebase Web configuration into `frontend/.env`.
6. Generate a Firebase Service Account and configure the backend `.env`.

---

# MongoDB

Use either a local MongoDB instance:

```env
DB_URL=mongodb://localhost:27017
DB_NAME=vibe
```

or MongoDB Atlas:

```env
DB_URL=mongodb+srv://<username>:<password>@cluster.mongodb.net
DB_NAME=vibe
```

---

# Running the Application

### Backend

```bash
cd backend
pnpm start
```

The backend runs at:

```text
http://localhost:3141
```

Interactive API documentation:

```text
http://localhost:3141/reference
```

### Frontend

```bash
cd frontend
pnpm dev
```

The frontend runs at:

```text
http://localhost:5173
```

---

# Troubleshooting

### `FirebaseError: auth/invalid-api-key`

The frontend Firebase configuration is missing or invalid.

Verify the values in `frontend/.env`.

---

### `Container not initialized`

Ensure the backend environment contains:

```env
APP_MODULE=all
```

---

### MongoDB connection failed

Verify:

* MongoDB is running.
* `DB_URL` is correct.
* `DB_NAME` exists.

---

### White screen on startup

Open the browser Developer Console (F12).

A common cause is missing or invalid Firebase environment variables.

---

### Dependency installation fails

This project uses **pnpm**.

Use:

```bash
pnpm install
```

instead of:

```bash
npm install
```

---

# Contributing

1. Fork the repository.
2. Create a feature branch.
3. Make your changes.
4. Verify both backend and frontend run successfully.
5. Submit a Pull Request.

Contributions that improve documentation, fix bugs, or add features are welcome.
