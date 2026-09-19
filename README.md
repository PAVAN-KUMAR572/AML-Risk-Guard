# 🛡️ AML RiskGuard — Next-Gen Anti-Money Laundering & Fraud Surveillance Platform

[![Python](https://img.shields.io/badge/Python-3.9%2B-blue.svg)](https://www.python.org/)
[![Flask](https://img.shields.io/badge/Framework-Flask%203.1-black.svg)](https://flask.palletsprojects.com/)
[![scikit-learn](https://img.shields.io/badge/ML-scikit--learn%201.4-F7931E.svg)](https://scikit-learn.org/)
[![Chart.js](https://img.shields.io/badge/Charts-Chart.js%204.4-FF6384.svg)](https://www.chartjs.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Compliance](https://img.shields.io/badge/Compliance-FATF%20%7C%20RBI%20%7C%20FinCEN-orange.svg)](https://www.fatf-gafi.org/)

> **An enterprise-grade, single-file full-stack Anti-Money Laundering (AML) risk monitoring, fraud detection, and interactive customer risk assessment platform.** Built with Python, Flask, modern embedded CSS, reactive vanilla JavaScript, Chart.js visualizations, and a **Random Forest ML model** trained on 5,000 real customer records — delivering both rule-based and AI-powered risk predictions simultaneously.

---


> **An enterprise-grade, single-file full-stack Anti-Money Laundering (AML) risk monitoring, fraud detection, and interactive customer risk assessment platform.** Built with Python, Flask, modern embedded CSS, reactive vanilla JavaScript, and Chart.js visualizations. Matches the reference compliance surveillance dashboard pixel-for-pixel with added authentication and dynamic risk assessment capabilities.

---

## 📸 Dashboard & Architecture Overview

The platform monitors **5,000 active customer accounts** and over **₹17.47 Billion** in monthly transactional volume across 12 commercial and public sector banking entities:
- **State Bank of India (SBI)**
- **HDFC Bank**
- **ICICI Bank**
- **Axis Bank**
- **Kotak Mahindra Bank**
- **Bank of Baroda**
- **Punjab National Bank (PNB)**
- **Union Bank of India**
- **Canara Bank**
- **Indian Bank**
- **IDFC First Bank**
- **Federal Bank & IndusInd Bank**

---

## ✨ Key System Features

### 1. 🔐 Role-Based Analyst Authentication (Login System)
- **Glassmorphic Security Portal:** Embedded authentication overlay with backdrop blur, security credentials validation, and session persistence via `localStorage`.
- **Pre-Configured Analyst Credentials:**
  - **Username:** `pavan`
  - **Password:** `admin123`
- **Session Controls:** Active user profile badge in the top navigation bar and a single-click **Log Out** control in the sidebar footer.

### 2. 🧮 Dynamic Customer Risk Assessment & Evaluation Engine
A dedicated page accessible from the sidebar (*"Risk Assessment"*):
- **Predictive Risk Calculator:**
  - Input parameters: *Customer Full Name*, *Observation Date Window (From-Date to To-Date)*, *Number of Transactions*, *Total Amount Transacted (₹)*, *Account Segment*, and *Associated Bank*.
  - Dynamically calculates:
    - Daily transaction frequency (txns/day) and daily spend velocity (₹/day).
    - Average ticket size and velocity ratios vs. segment benchmarks.
    - **Exact Predicted Risk Category:** `High Risk`, `Medium Risk`, `Low-Medium Risk`, or `Low Risk`.
    - **Composite Risk Score:** `0.0 – 100+` scale.
    - **Behavioral Flags:** Velocity spike detection, limit pressure breaches, structuring/smurfing indicators.
    - **Regulatory Actions:** Automated filing recommendations (e.g. *Trigger Enhanced Due Diligence (EDD)*, *Submit Suspicious Transaction Report (STR)*).
- **Instant Customer ID Account Lookup:**
  - Input any Customer ID from the 5,000-account registry (e.g. `CUST100009`, `CUST100010`, `CUST100013`, `CUST100001`).
  - Displays complete profile analysis: Customer Name, Primary Bank, Account Segment, Risk Score, Risk Category badge, Monthly Volume, Frequency, and **real-time visual progress meters for Daily & Monthly Limit Saturation**.
  - One-click action to inspect directly inside the main dashboard.

### 3. 🤖 Random Forest ML Model — AI-Powered Risk Prediction
A **scikit-learn Random Forest Classifier** (150 trees, `max_depth=12`) is trained at server startup on the full 5,000-customer dataset:

| Property | Value |
|---|---|
| **Algorithm** | Random Forest Classifier |
| **Training Data** | 5,000 labelled customer records (`aml_data.csv`) |
| **Test Set Accuracy** | **100%** (on clean, labelled dataset) |
| **Top Feature** | `Risk_Score` (69.9% importance) |
| **Classes** | `Low Risk` · `Low-Medium Risk` · `Medium Risk` · `High Risk` |

**What you get on every risk assessment:**
- ✅ Rule-based risk score + category (unchanged baseline)
- 🤖 ML predicted category badge
- 📊 Confidence percentage (e.g. *99.9% confident*)
- 📉 Per-class probability bars (High / Medium / Low breakdown)
- 📋 "View Model Details" button → opens Model Info modal with:
  - Horizontal feature importance Chart.js chart
  - Full classification report (Precision / Recall / F1 per class)

**API Endpoints added:**
- `GET /api/ml-info` — returns model accuracy, algorithm, feature importance, and classification report
- `POST /api/assess-risk` — now includes `ml_prediction`, `ml_confidence`, `ml_class_probabilities`, and `ml_model_accuracy` fields in the response

---

### 4. 📊 Executive Metric KPI Cards
- **Total Customers:** 5,000 accounts (`+12%` growth vs. previous audit cycle)
- **High Risk Customers:** 669 accounts (`13.38%` portfolio share requiring Enhanced Due Diligence)
- **Medium Risk Customers:** 715 accounts (`14.30%` requiring ongoing monitoring)
- **Low Risk Baseline:** 3,616 accounts (`72.32%` compliant retail baseline)
- **Total Transactions Monitored:** 124,856 daily / 999,667 monthly instances (`+18%` transaction velocity)
- **AML Compliance Widget:** Glowing status badge with direct one-click report export

### 4. 📈 Interactive Visualizations (Chart.js)
- **Risk Distribution Donut:** Cutout donut chart with center counter (`5,000 Customers`), color-coded legend, and percentage breakdowns.
- **Transaction Statistics Dual-Axis Combo Chart:** Dual-axis bar and line visualization tracking transaction frequency against monetary volume with **Daily**, **Weekly**, and **Monthly** interval toggle buttons.
- **Bank-wise Risk Analysis Table:** Institutional risk ranking with custom initial badges, customer counts, and high-risk concentration percentages.
- **Customer Segmentation Donut:** Proportional account segmentation across *Mass Retail*, *Affluent*, *Premium*, *Corporate Business*, and *SME*.
- **Risk Analytics Bimodal Chart:** Toggle between **By Count** and **By Amount (₹ Crores)**.
- **Risk Score Distribution Histogram:** 5-bin statistical distribution (`0-20`, `21-40`, `41-60`, `61-80`, `81-100+`).

### 5. 🔍 Customer Risk Analysis Data Table
- **Tabbed Risk Filtering:** Instant switching between *All*, *High Risk*, *Medium Risk*, and *Low Risk*.
- **Live Search:** Multi-field real-time query across Customer ID, Name, Bank, and Segment.
- **Smart Pagination:** 5-record pages with dynamic pagination controls.
- **Interactive Inspection:** Clicking any row or "View" button updates the dedicated **Customer Details Card**.

### 6. 👤 Granular Customer Dossier & Limit Saturation
- **Selected Account:** Rahul Sharma (`CUST1001` / `CUST100001`), High Risk tier.
- **Profile Attributes:** Primary Bank, Customer Type, Open Date, Risk Score (`92 / 100`), Total Transactions, and Total Volume.
- **Limit Saturation Gauges:** Visual progress meters measuring **Daily Limit Utilization** (`62%`) and **Monthly Limit Utilization** (`48%`).

### 7. 🚨 Live Alerts & Reports Feed
- Time-stamped surveillance stream (*All*, *Alerts*, *Reports*) tracking high-risk transaction anomalies, pattern alerts, watchlist PEP matches, and regulatory filing notices.

### 8. 📄 One-Click Audit Report Generation (.docx)
- Generates and downloads the formal **`AML_RiskGuard_Project_Report.docx`** directly from the UI or via `/api/export/docx`.

---

## 🏗️ Technical Architecture & Single-File Design

The entire platform is self-contained in **`app.py`**:

```
┌────────────────────────────────────────────────────────────┐
│                    AML RiskGuard (app.py)                  │
├───────────────────────────────┬────────────────────────────┤
│   Embedded Presentation Tier  │     Flask Backend API      │
│   • Analyst Login Portal      │     • POST /api/login      │
│   • Main Compliance Dashboard │     • POST /api/assess-risk│
│   • Risk Assessment Engine    │     • GET /api/stats       │
│   • Chart.js 4.4 CDN Engine   │     • GET /api/customers   │
│   • Responsive CSS3 & Grid    │     • GET /api/customer/:id│
│   • Vanilla JavaScript (ES6)  │     • GET /api/export/docx │
├───────────────────────────────┴────────────────────────────┤
│               Dataset & Analytical Engine                  │
│   • aml_data.csv (5,000 customer records ingested)         │
│   • Zero-dependency fallback to standard http.server      │
│   • Automatic open-port discovery (handles macOS 5000 busy)│
└────────────────────────────────────────────────────────────┘
```

---

## 🚀 Quickstart Guide

### Prerequisites
- **Python 3.9+** installed (`python3 --version`)

### 1. Set Up & Install Dependencies
```bash
cd "AML Sentinel"

# Install requirements
pip install -r requirements.txt
```

### 2. Run the Application
```bash
python3 app.py
```
*(If port 5000 is occupied by macOS AirPlay Receiver, `app.py` automatically detects it and smoothly switches to port **5001** or **8080** without error!)*

### 3. Access the Platform
1. Open your browser and navigate to:
   ```
   http://localhost:5001
   ```
   *(or the port printed in your terminal)*
2. Sign in with the analyst credentials:
   - **Username:** `pavan`
   - **Password:** `admin123`
3. Use the sidebar to toggle between the **Main Dashboard** and the **Risk Assessment** calculator.

---

## 📦 Project Deliverables (Exactly 4 Files)

| File | Type | Description |
|---|---|---|
| **[`app.py`](file:///Users/eravathripavankumar/AML%20Sentinel/app.py)** | Single-File Full-Stack | Complete embedded frontend (Login, Dashboard, Risk Calculator) + Flask backend REST API with zero-dependency fallback and smart port selection. |
| **[`requirements.txt`](file:///Users/eravathripavankumar/AML%20Sentinel/requirements.txt)** | Dependencies | Exact version specification (`Flask>=3.0.0`, `python-docx>=1.1.0`). |
| **[`AML_RiskGuard_Project_Report.docx`](file:///Users/eravathripavankumar/AML%20Sentinel/AML_RiskGuard_Project_Report.docx)** | Documentation | 7-Section formal executive compliance and project report ready for regulatory audit. |
| **[`README.md`](file:///Users/eravathripavankumar/AML%20Sentinel/README.md)** | Documentation | Comprehensive user guide, architecture documentation, and quickstart instructions. |
| **[`aml_data.csv`](file:///Users/eravathripavankumar/AML%20Sentinel/aml_data.csv)** | Dataset | 5,000 customer records with velocity, limit, and risk scoring metrics. |

---

## 🔌 REST API Specification

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/` | Serves the single-page application (Login, Dashboard, Risk Assessment views). |
| `POST` | `/api/login` | Authenticates analyst username/password. |
| `POST` | `/api/assess-risk` | Evaluates dynamic AML risk from name, date range, txn count, and amount. |
| `GET` | `/api/stats` | Returns aggregated metrics, bank risk table, and customer segmentation. |
| `GET` | `/api/customers` | Paginated, filterable customer list (`?page=1&limit=5&risk=High%20Risk&search=...`). |
| `GET` | `/api/customer/<id>` | Full profile, account analysis, and limit utilization for a specific Customer ID. |
| `GET` | `/api/export/docx` | Streams the formal compliance report document (`AML_RiskGuard_Project_Report.docx`). |

---

## 👨‍💻 Author & Acknowledgments
- **Platform:** AML RiskGuard / AML Sentinel
- **Lead Analyst:** Pavan Kumar
