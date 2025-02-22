Final MVP Overview
Your MVP is a cross‑platform, AI-powered password manager that:
Monitors Credentials: Continuously checks if passwords or emails have been leaked or are vulnerable.
Automatically Updates Passwords: Uses an AI component combined with web automation to log in and change passwords on supported sites.
Supports Import/Export: Lets users import data from other password managers and export their vault.
Offers Cross‑Platform Clients: Provides a browser extension (Chrome/Firefox) and a mobile app (iOS/Android) that can be set as the default password manager.
Secures Access: Features sign‑up with a master password, multi‑factor authentication (MFA via TOTP), and uses end‑to‑end encryption.
Optionally Detects Phishing: Integrates with a safe‑browsing (or uBlock Origin–like) API to warn users about suspicious sites/links.

Tech Stack
Backend & API
Language/Runtime: Node.js with TypeScript
Framework: Express for RESTful API endpoints
AI & Automation: TensorFlow.js for AI features (e.g., login recommendations) and Puppeteer for web automation (to automate password change flows)
Database: PostgreSQL (using a TypeScript ORM like TypeORM)
Authentication: JSON Web Tokens (JWT) for API auth; use libraries such as bcrypt for password hashing and Speakeasy for TOTP-based MFA
Security: Use Node’s crypto module or libsodium for AES‑256 encryption and implement a zero‑knowledge approach for sensitive data handling

Clients
Mobile App:
Framework: React Native (using Expo for rapid development)
Key Features: Full UI for sign‑up/login, viewing/editing vault, triggering manual/auto password updates, and integration with native autofill services.
Browser Extension:
Framework: React with TypeScript (using Manifest V3)
Key Features: UI for logging in, displaying vault items, autofill capabilities, and triggering automated password changes.
