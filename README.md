# OsteoCare — Osteoarthritis (OA) Patient Assessment System

A clinical-grade, frontend-only web application for standardized Osteoarthritis symptom stratification, WOMAC & KOOS disability index monitoring, and patient-centered clinical workflows.

---

## 🚀 Quick Start

### 1. Installation
```bash
npm install
```

### 2. Launch Local Development Server
```bash
npm run dev
```
Open your browser to: **`http://localhost:5173`** (or the port specified in the console).

### 3. Build for Production
```bash
npm run build
```

---

## 🔑 Demo Access Credentials

All authentication and patient registry data run completely in the browser using `localStorage`.

### 👨‍⚕️ Clinician Admin Portal
- **URL**: `/admin-login`
- **Username**: `admin`
- **Password**: `admin123`
*(Note: Clearly marked in code for production replacement with secure OAuth / JWT backend).*

### 🧑‍💼 Sample Patient Accounts
All seeded patient accounts use password: **`Patient@123`**
- **Eleanor Vance** (`eleanor.vance@example.com`): High-Risk Bilateral Knee OA (VAS 8.5/10, WOMAC 82%)
- **Arthur Pendelton** (`arthur.pendelton@example.com`): High-Risk Severe Right Hip OA (VAS 8.0/10)
- **Margaret Zhao** (`margaret.zhao@example.com`): High-Risk Post-traumatic Knee OA with recurring effusions
- **Robert Chen** (`robert.chen@example.com`): Moderate-Risk Bilateral Knee OA (VAS 5.5/10)
- **Dorothy Miller** (`dorothy.miller@example.com`): Moderate-Risk Hip & Hand OA
- **James Wilson** (`james.wilson@example.com`): Low-Risk Early-Stage Right Knee OA (VAS 3.2/10)
- **Evelyn Clark** (`evelyn.clark@example.com`): Low-Risk Mild Hand / Knee OA
- **Harold Gomez** (`harold.gomez@example.com`): Moderate-Risk Bilateral Knee OA with recent Hyaluronic Acid injection

---

## 🌟 Key Features

### 1. 10-Step Patient Assessment Wizard
1. **Demographics & Medical History**: Comorbidities, family history, and drug allergies.
2. **Pain Assessment**: Visual Analog Scale (VAS 0–10 interactive slider), interactive Joint Map, duration, diurnal pattern, and triggers.
3. **WOMAC & KOOS Index**: Pain (5 items), Stiffness (2 items), Physical Function (17 items), Sport/Rec, and QoL with **live scoring computation**.
4. **Joint-Specific Exam**: Active Flexion & Extension deficit ROM sliders, Crepitus severity, and Swelling/Effusion classification.
5. **Activity & Disability**: Walking distance tolerance, stair ambulation, sit-to-stand transfers, and computed disability index.
6. **Quality of Life (SF-12/36)**: Physical Component Summary (PCS) and Mental Component Summary (MCS).
7. **Medications & Injections**: Analgesic tracker, joint supplements, PT history, and intra-articular injections (Steroid, HA, PRP).
8. **Lifestyle & Biometrics**: Live BMI calculator and joint compressive force estimates (every 1 lb adds ~4 lbs joint force).
9. **Symptom Timeline**: Onset tracking, acute flare-up frequency, and milestone event log.
10. **Surgeries & Interventions**: Orthopedic surgery history, joints, and outcome notes.
- **Auto-Save & Resume**: Continuously saves draft to `localStorage` with prompt to resume on page reload.
- **Pre-Submission Review**: Read-only summary with direct "Edit" jump links.
- **Printable Clinical Summary**: Dedicated `@media print` formatted dossier ready to print or save as PDF for doctor visits.

### 2. Clinician Admin Console & Cohort Analytics
- **Patient Registry Table**: Multi-field search, filters by Risk Level, Affected Joint, Account Status, and sorting by VAS/WOMAC/Date.
- **One-Click CSV Export**: Download full registry datasets with computed metrics.
- **Interactive Recharts Visualizations**:
  - Pain score distribution histogram
  - Clinical risk stratification ratio (donut chart)
  - Primary joint affection prevalence
  - BMI and biomechanical joint load classifications
- **Patient Dossier Detail View**: Longitudinal history and comparison against cohort benchmarks.

---

## 🏥 Architecture & Simulation Boundaries

| Feature | Implementation Mode | Production Integration Point |
|---|---|---|
| **State Persistence** | `localStorage` (Seeded with 8 patient records) | REST / GraphQL API with PostgreSQL / MongoDB |
| **Authentication** | Dual Context (`patient` & `admin` sessions) | OAuth 2.0 / JWT Auth & Clinical EHR SSO |
| **Password Recovery** | Simulated one-time token generator | SendGrid / AWS SES email dispatch |
| **Clinical Formulas** | Live client-side calculation (WOMAC / KOOS / SF-12 / BMI) | Real-time validated calculation pipeline |
| **Report Export** | Browser Print Engine (`@media print`) & CSV Generator | Server-side PDF generation (Puppeteer / PDFKit) |
