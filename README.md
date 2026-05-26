# RxPredict — Pharmacy Inventory Forecasting SaaS

> Live at [rxpredict.app](https://rxpredict.app)

RxPredict helps independent pharmacies to prevent over or under stock that may effect their profits and sales. Pharmacists upload their dispensing history and the platform automatically forecasts demand per drug, flags reorder alerts, and recommends exact order quantities — all in a clean mobile-friendly dashboard.

> ⚠️ This is a showcase repo. The source code is private.

---

## The Problem

Independent pharmacies manage hundreds of drugs manually. Stock decisions are made on gut feel, leading to:
- **Stockouts** on high-demand drugs that hurt patient trust
- **Overstock** on slow-moving drugs that expire on the shelf
- **No visibility** into demand trends or seasonal patterns

---

## The Solution

RxPredict gives pharmacists a data-driven reorder system without needing a data team.

Upload a CSV → get forecasts, alerts, and order recommendations in seconds.

---

## Features

### 📊 Demand Forecasting
- Runs multiple statistical models per drug (SMA, Exponential Smoothing, Holt-Winters, Croston)
- Automatically selects the best-fit model based on holdout validation (WAPE scoring)
- 7–90 day forecast horizons with confidence intervals

### 🔔 Smart Alerts
- **Reorder alerts** — triggered when stock drops below the calculated reorder point
- **Stockout risk** — flags drugs projected to run out within days
- **Expiry alerts** — warns on drugs expiring within 30 days
- **Overstock alerts** — identifies slow-moving excess inventory

### 📦 Order Recommendations
- Calculates exact order quantities in units and bottles
- Accounts for supplier lead time and safety stock buffer
- Urgency levels: urgent / order soon / stable

### 📁 Bulk Data Upload
- Accepts CSV and Excel (.xlsx / .xls) dispensing history files
- Flexible column name detection (handles common aliases)
- Duplicate prevention via unique constraint on (pharmacy, drug, date)

### 📱 Mobile-First Dashboard
- Fully responsive — designed for iPhone use during pharmacy workflow
- Bottom navigation bar on mobile
- Touch-friendly forecast charts

### 🔐 Multi-Tenant Auth
- Each pharmacy is an isolated Clerk organisation
- Admins invite staff — no self-signup
- Row-level data isolation per pharmacy

---

## Tech Stack

| Layer | Technology |
|---|---|
| Framework | Next.js 16 (App Router, Turbopack) |
| Database | Neon PostgreSQL (serverless) |
| ORM | Drizzle ORM |
| Auth | Clerk (multi-tenant organisations) |
| Charts | Recharts |
| UI | Tailwind CSS + shadcn/ui |
| Deployment | Vercel |
| Error tracking | Sentry |

---

## System Architecture

<img width="1774" height="887" alt="image" src="https://github.com/user-attachments/assets/4f51bd64-9d6e-475f-80c7-f10515b44840" />

> Built for real-time pharmaceutical inventory forecasting and alerting using time-series models and Next.js server architecture.

---
## Contact
Built by [@mkaavish](https://github.com/mkaavish)  
Business Email: mkhht.llc@gmail.com 
Personal Email: mkaavish@gmail.com
Live product: [rxpredict.app](https://rxpredict.app)
