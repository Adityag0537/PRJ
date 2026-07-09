# ViBe

ViBe is an innovative educational platform that enhances learning through continuous assessment and interactive challenges. Designed to ensure that every student fully masters the material before progressing, ViBe uses smart question generation and adaptive reviews to reinforce understanding and foster deeper learning.

[![Watch the video](https://img.youtube.com/vi/Qc0FY260A98/maxresdefault.jpg)](https://youtu.be/Qc0FY260A98)

### [Click here to Watch](https://youtu.be/Qc0FY260A98)

## Key Features

- **Active Learning Through Adaptive Challenges:**  
  ViBe continuously assesses student comprehension and prompts a review of the material when needed, ensuring robust mastery before advancement.

- **AI-Enhanced Question Generation:**  
  Advanced algorithms generate contextually relevant questions that are both challenging and informative, helping to solidify knowledge.

- **Secure and Integrity-Assured Assessments:**  
  ViBe incorporates positive, AI-driven monitoring features that promote a fair and secure testing environment. These integrity safeguards include:
  - **Smart Proctoring:** AI-powered monitoring ensures that assessments are conducted honestly, providing a supportive framework that maintains academic integrity.
  - **Engagement Verification:** The system checks that students are actively engaged, reinforcing a positive learning atmosphere.

## Inspiration

ViBe draws inspiration from the classical Indian tale of Vikram and Betaal. In the story, Betaal challenges King Vikramaditya with riddles, and any incorrect answer prompts a review of the challenge. Similarly, ViBe reinforces learning by requiring students to revisit content if their responses do not meet the mark, ensuring a deep and lasting understanding of the material.

## Quick Start

For detailed setup instructions and comprehensive guides for both developers and end users, please refer to our [Documentation(In Progress)](https://continuousactivelearning.github.io/vibe/).

## License

ViBe is licensed under the [MIT License](LICENSE).

## Feedback and Contributions

We welcome your feedback, contributions, and suggestions. Please:

- **Report Issues:** Open an issue on the repository.
- **Contribute:** Fork the repository, create a feature branch, and submit a pull request.
- **Contact:** Reach out to us at [dled@iitrpr.ac.in](mailto:dled@iitrpr.ac.in).

---

Explore our [Documentation](https://vicharanashala.github.io/vibe/) for further details on usage, setup, and development.

# PRJ
# ViBe – Local Development Setup

This guide walks you through setting up the ViBe project for local development.

---

## Prerequisites

Before you begin, ensure you have the following installed:

* Node.js (v20+ recommended)
* pnpm
* MongoDB (local or MongoDB Atlas)
* Git
* Firebase CLI (optional, for Firebase emulators)

Install pnpm globally:

```bash
npm install -g pnpm
```

Verify installation:

```bash
pnpm -v
```

---

# Clone the repository

```bash
git clone <repository-url>
cd vibe
```

---

# Install dependencies

### Backend

```bash
cd backend
pnpm install
```

### Frontend

```bash
cd ../frontend
pnpm install
```

---

# Backend Environment Setup

Create a `.env` file inside the `backend` directory.

```bash
cp .example.env .env
```

Update the required values.

### Required

* `APP_MODULE=all`
* `DB_URL`
* `DB_NAME`

### Firebase (Development)

The backend uses Firebase Admin SDK.

Create a Firebase project and generate a Service Account key.

Add the following variables:

```
FIREBASE_PROJECT_ID=
FIREBASE_CLIENT_EMAIL=
FIREBASE_PRIVATE_KEY=
```

---

# Frontend Environment Setup

Create a `.env` file inside the `frontend` directory.

```
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

These values are available from **Firebase Console → Project Settings → General → Your Apps**.

---

# MongoDB

You can use either:

## Local MongoDB

```
DB_URL=mongodb://localhost:27017
DB_NAME=vibe
```

or

## MongoDB Atlas

```
DB_URL=mongodb+srv://<username>:<password>@cluster.mongodb.net
DB_NAME=vibe
```

---

# Running the Backend

```bash
cd backend
pnpm start
```

The backend will start at

```
http://localhost:3141
```

API documentation is available at

```
http://localhost:3141/reference
```

---

# Running the Frontend

```bash
cd frontend
pnpm dev
```

The frontend is usually available at

```
http://localhost:5173
```

---

# Firebase Setup

## Frontend

Create a Firebase project.

Enable:

* Authentication

  * Email/Password
  * Google

Register a Web App and copy the Firebase configuration into `frontend/.env`.

## Backend

Generate a Firebase Service Account:

Firebase Console

→ Project Settings

→ Service Accounts

→ Generate New Private Key

Copy the values into `backend/.env`.

---

# Common Issues

## Firebase: auth/invalid-api-key

The frontend `.env` is missing or contains invalid Firebase configuration.

---

## Container not initialized

Ensure:

```
APP_MODULE=all
```

is set inside the backend `.env`.

---

## MongoDB connection failed

Verify:

* MongoDB is running
* `DB_URL`
* `DB_NAME`

---

## White screen after running frontend

Open the browser Developer Console (F12).

Most commonly this is caused by missing Firebase environment variables.

---

## Dependency installation issues

Always use **pnpm**, not npm.

Install dependencies with

```bash
pnpm install
```

instead of

```bash
npm install
```

---

# Development Notes

* The backend uses Firebase Admin SDK.
* The frontend uses Firebase Authentication.
* MongoDB must be configured before starting the backend.
* Some background jobs expect existing database data. When running with an empty database, these jobs may need to be disabled during development.

---

# Contributing

1. Create a feature branch.
2. Make your changes.
3. Run the application locally.
4. Ensure both frontend and backend start successfully.
5. Submit a Pull Request.

