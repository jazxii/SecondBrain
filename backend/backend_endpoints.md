### 🧠 Full Backend Endpoint Canvas — Full-Stack AI Project - A11y-insights
**Stack:** FastAPI + MongoDB + OpenAI + React (Frontend)

---

## 🚀 Overview
This canvas outlines **all backend endpoints** required for a complete full-stack AI application — covering authentication, AI integration, JIRA automation, reports, and user utilities.

---

## 🔐 1. AUTHENTICATION MODULE
**Router:** `/auth`

| Endpoint | Method | Description |
|-----------|---------|-------------|
| `/signup` | POST | Register a new user, send OTP |
| `/verify-otp` | POST | Verify OTP and activate account |
| `/login` | POST | Authenticate user and issue JWT |
| `/refresh` | POST | Refresh JWT token |
| `/forgot-password` | POST | Initiate password reset flow |
| `/reset-password` | POST | Reset password using OTP or token |
| `/logout` | POST | Revoke refresh token |
| `/resend-otp` | POST | Resend verification OTP |

---

## 👤 2. USER MODULE
**Router:** `/users`

| Endpoint | Method | Description |
|-----------|---------|-------------|
| `/me` | GET | Fetch logged-in user info |
| `/me/update` | PUT | Update profile details |
| `/me/password` | PUT | Change password |
| `/me/avatar` | POST | Upload or update avatar |
| `/me/delete` | DELETE | Delete user account |
| `/all` | GET | Get list of all users (admin only) |

---

## 📊 3. REPORT MODULE (AI Reports)
**Router:** `/reports`

| Endpoint | Method | Description |
|-----------|---------|-------------|
| `/` | GET | List all reports for a user |
| `/{report_id}` | GET | Get a single report |
| `/create` | POST | Generate a new report (via OpenAI) |
| `/{report_id}/update` | PUT | Edit an existing report |
| `/{report_id}/delete` | DELETE | Delete report |
| `/share` | POST | Share report via email or link |
| `/export/pdf` | POST | Export report to PDF |
| `/stats` | GET | Get report usage analytics |

---

## 🤖 4. AI MODULE (OpenAI Integration)
**Router:** `/ai`

| Endpoint | Method | Description |
|-----------|---------|-------------|
| `/generate` | POST | Send user input to OpenAI |
| `/analyze` | POST | Analyze stored report or user data |
| `/summary` | POST | Summarize report or text |
| `/compare` | POST | Compare two reports |
| `/models` | GET | List supported AI models |
| `/settings` | GET/PUT | Get or update AI preferences |

---

## 🧾 5. JIRA AUTOMATION MODULE
**Router:** `/jira`

| Endpoint | Method | Description |
|-----------|---------|-------------|
| `/config` | GET/PUT | Get or update JIRA API credentials |
| `/create-issue` | POST | Create a new JIRA ticket |
| `/link-issue` | POST | Link an existing JIRA story/bug |
| `/sync-status` | GET | Sync JIRA issue statuses |
| `/bulk-create` | POST | Create multiple JIRA issues from Excel |
| `/projects` | GET | Fetch accessible JIRA projects |
| `/teams` | GET | Fetch teams and assignees |

---

## ⚙️ 6. ADMIN MODULE
**Router:** `/admin`

| Endpoint | Method | Description |
|-----------|---------|-------------|
| `/users` | GET | Get all users |
| `/reports` | GET | Access all user reports |
| `/activity` | GET | Get recent activity logs |
| `/audit-log` | GET | Detailed backend audit logs |
| `/config` | GET/PUT | Manage global app settings |

---

## 💬 7. NOTIFICATIONS MODULE
**Router:** `/notifications`

| Endpoint | Method | Description |
|-----------|---------|-------------|
| `/send` | POST | Send email/SMS/in-app notification |
| `/list` | GET | List notifications for a user |
| `/mark-read/{id}` | PUT | Mark a notification as read |
| `/preferences` | GET/PUT | Get or update user notification preferences |

---

## 🧩 8. INTEGRATIONS MODULE
**Router:** `/integrations`

| Endpoint | Method | Description |
|-----------|---------|-------------|
| `/connect/slack` | POST | Connect Slack workspace via OAuth |
| `/send/slack` | POST | Send report/summary to Slack channel |
| `/github` | POST | Link GitHub repo for automation (optional) |

---

## 🗂️ 9. FILE MANAGEMENT MODULE
**Router:** `/files`

| Endpoint | Method | Description |
|-----------|---------|-------------|
| `/upload` | POST | Upload file (CSV, PDF, DOCX) for AI analysis |
| `/download/{id}` | GET | Download stored file or report |
| `/delete/{id}` | DELETE | Remove a file |
| `/list` | GET | List all uploaded files |

---

## 🕵️‍♂️ 10. ANALYTICS & LOGGING MODULE
**Router:** `/analytics`

| Endpoint | Method | Description |
|-----------|---------|-------------|
| `/usage` | GET | Get user-level analytics |
| `/system` | GET | Get system-wide stats (admin only) |
| `/logs` | GET | Retrieve backend logs with filters |

---

## 📦 Directory Structure Additions
```
backend/
 ├── routers/
 │   ├── jira.py
 │   ├── notifications.py
 │   ├── admin.py
 │   ├── integrations.py
 │   ├── analytics.py
 │   └── files.py
 ├── services/
 │   ├── jira_service.py
 │   ├── ai_service.py
 │   ├── report_service.py
 │   ├── user_service.py
 │   └── notification_service.py
```

---

## ⚙️ Middleware & Security Considerations
- JWT authentication middleware for all protected routes
- Role-based access control (Admin/User)
- Input validation using Pydantic schemas
- Rate limiting for OTP & JIRA routes
- Background tasks for long jobs (Celery / FastAPI BackgroundTasks)
- Logging middleware for audit trails

---

## 🧱 Development Phases
**Phase 1 (Core Build):**
- `/auth`, `/users`, `/reports`, `/ai`

**Phase 2 (Enhancements):**
- `/jira`, `/notifications`, `/files`, `/analytics`

**Phase 3 (Integrations/Admin):**
- `/admin`, `/integrations`, extended AI features

---

Would you like me to extend this with a **development timeline (Week 1–6)** that prioritizes API completion, testing, and frontend integration order?

