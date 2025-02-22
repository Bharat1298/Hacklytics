SecuroSaur: The AI-Powered Cross-Platform Password Manager

Overview

This project is a cross-platform, AI-powered password manager that provides automated credential management, security monitoring, and seamless integration across devices.

Key Features

✅ Monitors Credentials – Checks if stored passwords or emails have been leaked or are vulnerable.✅ Automated Password Updates – Uses AI and web automation to change passwords securely on supported sites.✅ Import/Export Support – Allows users to import credentials from other password managers and export their vault.✅ Cross-Platform Compatibility – Includes both a browser extension (Chrome/Firefox) and a mobile app (iOS/Android) that can be set as the default password manager.✅ Secure Authentication – Protects access with a master password, multi-factor authentication (MFA via TOTP), and end-to-end encryption.✅ Phishing Detection (Optional) – Integrates with a safe-browsing API (or a uBlock Origin-like API) to warn users about suspicious sites/links.

Tech Stack

Backend & API

Language/Runtime: Node.js with TypeScript

Framework: Express.js for RESTful API endpoints

AI & Automation: TensorFlow.js (AI-driven recommendations), Puppeteer (web automation for password updates)

Database: PostgreSQL with TypeORM (TypeScript ORM)

Authentication: JWT-based authentication, bcrypt for password hashing, Speakeasy for TOTP-based MFA

Security: AES-256 encryption with Node.js crypto module or libsodium; Zero-knowledge approach for sensitive data

Shared Code (Monorepo Structure)

This project follows a monorepo structure with shared libraries:

/password-manager-mvp
│-- backend        # Node.js API and business logic
│-- mobile         # React Native mobile app
│-- extension      # Browser extension (React + TypeScript)
│-- common         # Shared utilities (encryption, AI functions, import/export parsers)

Package Manager: Uses npm workspaces or Yarn Workspaces for managing shared code efficiently.

Clients

Mobile App (React Native)

Framework: React Native (Expo for rapid development)

Features: Sign-up/Login, Vault Management (view, edit, delete credentials), Autofill support, AI-driven login recommendations, Password breach alerts.

Browser Extension (React + TypeScript)

Framework: React + TypeScript (using Manifest V3)

Features: Autofill credentials, Password health check, Trigger AI-driven password updates, Vault management UI.

Project Setup & Development Guide

1. Clone the Repository & Install Dependencies

git clone https://github.com/your-repo/password-manager-mvp.git
cd password-manager-mvp
npm install

2. Start the Backend API

cd backend
npm run dev  # Runs Express server with TypeScript

3. Run the Mobile App

cd mobile
npx expo start

4. Build & Load the Browser Extension

cd extension
npm run build

Load the dist/ folder as an unpacked extension in Chrome/Firefox Developer mode.

API Endpoints

Authentication

POST /api/v1/auth/signup – Create an account with a master password (bcrypt-hashed, securely stored).

POST /api/v1/auth/login – Authenticate and retrieve a JWT token.

Vault Management

GET /api/v1/passwords – Retrieve all saved credentials.

POST /api/v1/passwords – Add a new credential.

PUT /api/v1/passwords/:id – Update an existing credential.

DELETE /api/v1/passwords/:id – Remove a stored credential.

Security & Automation

GET /api/v1/health-check – Check for leaked, weak, or compromised passwords.

POST /api/v1/auto-update/:siteId – Trigger an automated password change (Puppeteer automation).

Security Considerations

Zero-Knowledge Encryption: All passwords stored in the vault are encrypted using AES-256 before being saved.

Multi-Factor Authentication (MFA): Supports TOTP-based authentication using Speakeasy.

Safe Browsing API Integration: Detects phishing links and warns users.

Future Enhancements

Expand AI-driven auto-login recommendations with more sophisticated models.

Extend browser extension functionality to support Edge, Safari.

Add desktop support using Electron.js.

Improve automated password updating for more websites via ML-driven form parsing.
