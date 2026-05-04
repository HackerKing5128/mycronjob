# 🕒 MyCronJob

MyCronJob is a lightweight website uptime monitoring system built for **small business owners and solo founders** who don’t have a dedicated backend or DevOps team.

It continuously monitors websites, logs their health, and sends **email alerts** when a website goes down — and again when it recovers.

---

## 🚨 Problem Statement

For many small businesses, a website is the core of their business. However:

- Websites can crash at **unexpected times** (e.g., late night or early morning)
- Business owners are often **unaware** of downtime
- No backend or monitoring team is available to notify them
- Downtime can result in:
  - loss of sales
  - loss of user trust
  - poor customer experience

There is a need for a **simple, automated system** that notifies the owner immediately when their website goes down.

---

## ✅ Solution

MyCronJob solves this problem by:

- Automatically checking websites at regular intervals
- Detecting downtime using HTTP status codes
- Sending **email alerts** when a website goes DOWN
- Sending a **recovery email** when the website comes back UP
- Providing a dashboard to visualize:
  - current website status
  - uptime percentage
  - last downtime duration
  - historical status timeline (🟢 UP / 🔴 DOWN)

All checks and alerts happen **automatically**, without manual intervention.

---

## 🧠 How It Works (High Level)

```
User Dashboard (React)
        ↓
Backend API (Node.js + Express)
        ↓
MongoDB (Data Storage)
        ↑
Background Worker (Cron Job)
        ↓
Website Ping (HTTP Request)
        ↓
Email Alerts + WebSocket Events
```

---

## 🏗 Architecture Overview

### Frontend
- Built with React + Vite
- User authentication (Login / Register)
- Dashboard to:
  - add and delete websites
  - view live website status
  - view uptime percentage
  - view last downtime duration
  - view status history graph
- Real-time updates using WebSockets

### Backend
- Node.js + Express
- JWT-based authentication
- REST APIs for websites and status logs
- WebSocket server for real-time updates
- MongoDB for persistent storage

### Worker
- Runs as a background process
- Uses cron scheduling
- Pings websites on a fixed interval
- Retry logic to avoid false downtime alerts
- Creates immutable status logs
- Sends:
  - downtime email alerts
  - recovery email alerts
  - real-time events to backend

---

## ✨ Core Features

- ✅ Website uptime monitoring
- 🔁 Retry logic before declaring downtime
- 📧 Email alerts (DOWN & RECOVERY)
- 📊 Uptime percentage calculation
- ⏱ Last downtime duration
- 🟢🔴 Status history timeline
- ⚡ Real-time updates via WebSockets
- 🔐 Secure JWT authentication
- 🧩 Clean separation of backend and worker

---

## 🧪 Alert Logic (No Spam)

- Email alerts are sent **only on state change**
  - UP → DOWN → alert email
  - DOWN → UP → recovery email
- No repeated or spam notifications
- Initial checks do not trigger false alerts

---

## 🛠 Tech Stack

### Frontend
- React
- Vite
- Axios
- Socket.IO Client

### Backend
- Node.js
- Express
- MongoDB (Mongoose)
- JWT Authentication
- Socket.IO
- Nodemailer

### Worker
- Node.js
- node-cron
- node-fetch

---

## 📁 Project Structure

```
MyCronJob/
├── frontend/ # React dashboard
├── backend/ # REST API + WebSockets
├── worker/ # Cron job & monitoring logic
└── README.md
```

---

## ▶️ Run Locally

1. Start MongoDB locally on `127.0.0.1:27017` or point both services at another MongoDB instance.
2. Copy `backend/.env.example` to `backend/.env` and fill in `MONGO_URI`, `JWT_SECRET`, and `INTERNAL_SECRET`.
3. Copy `worker/.env.example` to `worker/.env` and use the same `MONGO_URI` and `INTERNAL_SECRET`, plus your email credentials.
4. In separate terminals, run:

```bash
cd backend && npm start
cd worker && npm start
cd frontend && npm run dev
```

The frontend expects the backend at `http://localhost:3000/api`.

---

## 🎯 Target Users

- Small business owners
- Solo founders
- Indie hackers
- Anyone running a website without a backend team

---

## 🚀 Future Improvements

- Multiple alert recipients per website
- SMS / WhatsApp notifications
- Advanced uptime analytics
- Paid plans (monitor more websites)
- Time-weighted uptime calculations

---

## 👨‍💻 Author

Built by **Yash Maheshwari**

---

## 📌 Note

MyCronJob is built with a **real-world engineering mindset**:
- clean architecture
- clear separation of concerns
- production-style background worker
- reliable alerting without noise



