# TruckLink — Driver Hiring & Onboarding Portal

TruckLink is a role-based platform connecting drivers, recruiters, and admins. Drivers create profiles and track approval status, while recruiters can view approved drivers and match them with job opportunities.

**Project:** Zeppelin Labs — P3
**Team:** Abdullah, Hasan, Sidra, Akash, Wajih

---

## Tech Stack

* **Frontend:** React (Vite)
* **Backend:** Django + Django REST Framework
* **Database:** PostgreSQL (Neon)
* **Auth:** JWT
* **Real-time:** Django Channels
* **File Storage:** Cloudinary

---

## User Roles

* **Driver** — signs up, creates profile, tracks approval status, applies to jobs
* **Recruiter** — posts jobs, views approved drivers, shortlists matches
* **Admin** — moderates profiles, manages recruiters, views analytics

---

## My Contribution

**Sidra — Frontend Developer**

* Driver signup and profile pages
* Driver approval/status pages
* Admin analytics UI
* Admin master-data UI


---

## Setup

### Backend

```bash
cd backend
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
```

Create `backend/.env`:

```env
DB_NAME=...
DB_USER=...
DB_PASSWORD=...
DB_HOST=...
DB_PORT=5432
CLOUDINARY_CLOUD_NAME=...
CLOUDINARY_API_KEY=...
CLOUDINARY_API_SECRET=...
```

```bash
python manage.py migrate
python manage.py runserver
```

Runs at `http://127.0.0.1:8000`

### Frontend

```bash
cd frontend
npm install
```

Create `frontend/.env`:

```env
VITE_API_BASE_URL=http://127.0.0.1:8000/api
```

```bash
npm run dev
```

Runs at `http://localhost:5173`

---

## Key API Endpoints

| Endpoint                         | Method | Access    |
| -------------------------------- | ------ | --------- |
| `/api/users/signup/driver/`      | POST   | Public    |
| `/api/users/signup/recruiter/`   | POST   | Public    |
| `/api/token/`                    | POST   | Public    |
| `/api/drivers/profile/`          | POST   | Driver    |
| `/api/drivers/moderation/queue/` | GET    | Admin     |
| `/api/drivers/moderation/<id>/`  | POST   | Admin     |
| `/api/recruiters/profile/`       | POST   | Recruiter |
| `/api/recruiters/jobs/`          | POST   | Recruiter |
| `/api/analytics/`                | GET    | Admin     |

All authenticated endpoints require:

```text
Authorization: Bearer <access_token>
```

---

## Team

| Person    | Task                                                               |
| --------- | ------------------------------------------------------------------ |
| Abdullah  | Backend, authentication, moderation & profile endpoints            |
| Wajih     | Real-time notifications, Cloudinary, matching & deployment         |
| Hasan     | React setup, admin moderation UI & API wiring                      |
| **Sidra** | **Driver signup/profile/status, admin analytics & master-data UI** |
| Akash     | Recruiter dashboard, job posting & matching results UI             |
