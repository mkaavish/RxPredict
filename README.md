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

## Architecture

Browser
└── Next.js App Router (Vercel)
├── /dashboard — Server component, parallel DB queries
├── /inventory — SWR client, drug catalog table
├── /inventory/[id] — Forecast chart + order recommendation
├── /alerts — Alert feed with type/severity filters
└── /upload — CSV/Excel ingestion pipeline

API Routes
├── /api/forecast/[drugId] — Runs forecasting engine, returns ForecastResult
├── /api/alerts — GET (list) / POST (regenerate) / PATCH (acknowledge)
└── /api/upload/dispensed — Parses file, batch inserts, triggers alerts

Forecasting Engine (server-side)
├── SMA, Exponential Smoothing, SES, Holt-Winters, Croston
├── Auto mode: benchmarks all models, picks lowest WAPE
└── Outputs: predicted values, confidence intervals, reorder point, safety stock

---

## Screenshots
<img width="1512" height="826" alt="image" src="https://github.com/user-attachments/assets/faf72f68-ce72-4e74-8805-53876beae1e2" />
<img width="1512" height="824" alt="image" src="https://github.com/user-attachments/assets/5c4130a8-f9c9-4bf5-91fe-111313481f11" />
<img width="1512" height="826" alt="image" src="https://github.com/user-attachments/assets/3e166e66-6cbb-4cbe-b841-4f334512b06d" />
<img width="1269" height="571" alt="image" src="https://github.com/user-attachments/assets/f5622625-1b33-4eaa-8196-582e36a0e75f" />
<img width="1512" height="828" alt="image" src="https://github.com/user-attachments/assets/0e6f0a70-fabb-4e72-9e12-476ccff36be5" />
<img width="1512" height="825" alt="image" src="https://github.com/user-attachments/assets/140ca20e-f4b0-4d6d-996f-ab8a156be94b" />
<img width="1512" height="826" alt="image" src="https://github.com/user-attachments/assets/cdda6d1b-a788-4b99-ad4d-6f82ddb39c45" />

---
## Contact
Built by [@mkaavish](https://github.com/mkaavish)  
Business Email: mkhht.llc@gmail.com 
Personal Email: mkaavish@gmail.com
Live product: [rxpredict.app](https://rxpredict.app)
