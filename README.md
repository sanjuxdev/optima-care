# 🏥 OptimaCare — Clinical AI Decision Support System

> An intelligent, explainable AI platform for predicting multi-condition health risks and generating clinician-friendly diagnostic insights — powered by XGBoost, SHAP, and Anthropic Claude.

---

## 📌 Table of Contents

- [Overview](#-overview)
- [Key Features](#-key-features)
- [Screenshots](#-screenshots)
- [System Architecture](#-system-architecture)
- [Tech Stack](#-tech-stack)
- [Model Performance](#-model-performance)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
  - [Prerequisites](#prerequisites)
  - [Backend Setup](#backend-setup)
  - [Frontend Setup](#frontend-setup)
- [Configuration](#-configuration)
- [How It Works](#-how-it-works)
- [API Overview](#-api-overview)
- [Roadmap](#-roadmap)
- [Disclaimer](#️-disclaimer)
- [Acknowledgements](#-acknowledgements)

---

## 🧠 Overview

**OptimaCare** is a full-stack Clinical Decision Support System (CDSS) built for healthcare professionals to assess multi-condition patient risks in real time. It combines machine learning models trained on clinical datasets with **Explainable AI (XAI)** to make predictions transparent, trustworthy, and actionable.

At its core, OptimaCare uses:
- **XGBoost** models for high-accuracy risk prediction across 3 conditions
- **SHAP (SHapley Additive exPlanations)** to highlight which clinical indicators drive each prediction
- **Anthropic Claude API** to convert raw SHAP outputs into human-readable clinical narratives
- **BioBERT + OpenFDA** for AI deep analysis with live evidence synthesis from clinical trials
- A **React + Tailwind CSS** full CDSS dashboard with Diagnostic Hub, Patient Portal, Analytics, Clinical Rules, and Telehealth modules

Built as a **Hackathon Project** to demonstrate responsible, explainable AI in a critical healthcare context.

---

## ✨ Key Features

| Feature | Description |
|---|---|
| 🔬 Multi-Condition Engine | Predicts risk for **Diabetes**, **Heart Disease**, and **Hypertension** simultaneously |
| 📊 SHAP Explainability | Highlights exact clinical indicators (e.g., glucose, blood pressure, age) driving each risk score |
| 🤖 Claude NLP Summaries | Generates plain-English clinical summaries and actionable recommendations via Anthropic Claude |
| 🧬 AI Deep Analysis Engine | Live synthesis using **BioBERT + OpenFDA** from 4 clinical trials per patient |
| 📈 Biomarker Trend Charts | Longitudinal analysis for glucose, eGFR, and other biomarkers plotted over time |
| 🏥 Population Intelligence | Real-time aggregate analytics — health index, high-risk cases, clinician efficiency, demographics |
| 🧑‍⚕️ Patient Onboarding | Initialize clinical profiles with photo and PDF medical report upload |
| 📱 Responsive Dashboard | Mobile-first React UI with Diagnostic Hub, Patient Portal, Analytics, Clinical Rules, Telehealth |
| 🗃️ Audit Trail | Every diagnostic session is persisted to a local SQLite database for clinical review and compliance |

---

## 📸 Screenshots

### 🧪 Diagnostic Hub
> Patient profile card with real-time biomarker trend charts (longitudinal glucose & eGFR analysis) and an AI Deep Analysis Engine powered by live BioBERT + OpenFDA synthesis.


<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/2384f867-ee5c-45d7-bb4e-612be45486c9" />


---

### 📊 Analytics Dashboard — Population Intelligence
> Real-time aggregate analytics across the entire clinical database. Displays total managed patients, average health index, high-risk cases, clinician efficiency score, condition-wise risk distribution, and patient demographics breakdown.

<img width="1880" height="1077" alt="Image" src="https://github.com/user-attachments/assets/d905c452-28fe-4bf3-91bf-ab78425a15c8" />

---

### 🧑‍⚕️ Patient Onboarding
> Initialize a new clinical profile by entering patient details — full name, age, gender, height, weight, patient photo, and medical report (PDF upload).


<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/5cd5d8b4-fba8-42ca-bf70-a1d67e4138d0" />
---

## 🏗️ System Architecture

```
┌──────────────────────────────────────────────────────────────┐
│                      Clinical Frontend                       │
│              (React + Vite + Tailwind CSS)                   │
│                                                              │
│  ┌─────────────┐  ┌───────────────┐  ┌──────────────────┐  │
│  │ Diagnostic  │  │    Patient    │  │    Analytics /   │  │
│  │    Hub      │  │    Portal     │  │  Population Intel│  │
│  └─────────────┘  └───────────────┘  └──────────────────┘  │
└──────────────────────────────┬───────────────────────────────┘
                               │ REST API (HTTP/JSON)
┌──────────────────────────────▼───────────────────────────────┐
│                       FastAPI Backend                        │
│                                                              │
│  ┌─────────────┐   ┌──────────┐   ┌────────────────────┐   │
│  │  XGBoost    │   │   SHAP   │   │   Anthropic Claude  │   │
│  │  ML Models  │──►│  Engine  │──►│   NLP Summaries     │   │
│  │ (3 models)  │   │          │   │                    │   │
│  └─────────────┘   └──────────┘   └────────────────────┘   │
│                                                              │
│  ┌──────────────────────────────────────────────────────┐   │
│  │           SQLAlchemy ORM  ──  SQLite DB               │   │
│  └──────────────────────────────────────────────────────┘   │
└──────────────────────────────────────────────────────────────┘
```

---

## 🛠️ Tech Stack

### Backend
| Technology | Role |
|---|---|
| **FastAPI** | High-performance REST API framework |
| **XGBoost** | Gradient boosting ML models for risk prediction |
| **SHAP** | Explainable AI — feature importance per prediction |
| **SQLAlchemy** | ORM for database interactions |
| **SQLite** | Lightweight persistent audit database |
| **Anthropic Claude API** | NLP clinical summary generation |
| **BioBERT + OpenFDA** | AI deep analysis & clinical trial evidence synthesis |
| **Uvicorn** | ASGI server |

### Frontend
| Technology | Role |
|---|---|
| **React (Vite)** | Component-based UI framework with fast HMR |
| **Tailwind CSS** | Utility-first responsive styling |
| **Headless UI** | Accessible, unstyled UI components |

### ML & Data
| Technology | Role |
|---|---|
| **XGBoost** | Trained models for Diabetes, Heart Disease, Hypertension |
| **SHAP** | Per-prediction explainability |
| **Scikit-learn** | Data preprocessing and model evaluation |

---

## 📊 Model Performance

The three XGBoost models were trained and evaluated using **AUC** (Area Under the ROC Curve):

| Condition | AUC Score | Status |
|---|---|---|
| 🩺 Diabetes | **0.816** | ✅ Good |
| ❤️ Heart Disease | **0.927** | ✅ Excellent |
| 🩸 Hypertension | **0.964** | ✅ Excellent |

> Higher AUC indicates stronger discriminative ability between positive and negative cases.

---

## 📁 Project Structure

This is a **monorepo** — frontend and backend live together in the same repository.

```
OptimaCare/
├── .env                       ← Single env file for the whole project (never commit)
├── .env.example               ← Safe to commit — shows required keys
├── .gitignore
│
├── backend/
│   ├── app/
│   │   ├── main.py            # FastAPI application & API routes
│   │   ├── models/            # XGBoost model loading & inference
│   │   ├── shap_engine/       # SHAP explainability logic
│   │   ├── claude_summary/    # Anthropic Claude integration
│   │   └── database/          # SQLAlchemy models & DB setup
│   └── requirements.txt
│
├── clinical-frontend/
│   ├── src/
│   │   ├── components/        # React UI components
│   │   ├── pages/             # Diagnostic Hub, Patient Portal, Analytics
│   │   └── App.jsx            # Root application component
│   ├── .env                   # Vite env (VITE_ prefix required)
│   ├── package.json
│   └── vite.config.js
│
├── trained_models/            # Serialized XGBoost .pkl model files
├── models.py                  # Model definitions / schemas
├── train_models.py            # ML training pipeline script
├── start_backend.py           # Backend launcher utility
├── test_integration.py        # Integration test suite
└── package.json
```

---

## 🚀 Getting Started

### Prerequisites

Make sure you have the following installed:

- **Python 3.10+**
- **Node.js 18+**
- **Anthropic API Key** — [Get one here](https://console.anthropic.com/)

---

### Backend Setup

1. **Navigate to the backend directory:**
   ```bash
   cd backend
   ```

2. **Create and activate a virtual environment:**
   ```bash
   python -m venv venv

   # macOS / Linux
   source venv/bin/activate

   # Windows
   venv\Scripts\activate
   ```

3. **Install Python dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Create a `.env` file** in the project root (see [Configuration](#-configuration)):
   ```bash
   cp .env.example .env
   # Then fill in your values
   ```

5. **Start the backend server:**
   ```bash
   python -m uvicorn app.main:app --host 0.0.0.0 --port 8000 --reload
   ```

   - API live at → `http://localhost:8000`
   - Interactive Swagger docs → `http://localhost:8000/docs`

---

### Frontend Setup

1. **Navigate to the frontend directory:**
   ```bash
   cd clinical-frontend
   ```

2. **Install Node.js dependencies:**
   ```bash
   npm install
   ```

3. **Start the development server:**
   ```bash
   npm run dev
   ```

   - App live at → `http://localhost:3000`

---

## ⚙️ Configuration

OptimaCare uses a single root `.env` file for all configuration. Copy `.env.example` and fill in your values:

```bash
cp .env.example .env
```

### Environment Variables

| Variable | Required | Default | Description |
|---|---|---|---|
| `ANTHROPIC_API_KEY` | ✅ Yes | — | Your Anthropic API key |
| `CLAUDE_MODEL` | ❌ No | `claude-opus-4-6` | Claude model version |
| `DATABASE_URL` | ❌ No | `sqlite:///./optimacare.db` | DB connection string |
| `HOST` | ❌ No | `0.0.0.0` | Backend host |
| `PORT` | ❌ No | `8000` | Backend port |
| `DEBUG` | ❌ No | `False` | Enable debug mode |
| `VITE_API_BASE_URL` | ✅ Yes | — | Backend URL for the React frontend |

### `.env.example`

```env
# Anthropic Claude
ANTHROPIC_API_KEY=
CLAUDE_MODEL=claude-opus-4-6

# Database
DATABASE_URL=sqlite:///./optimacare.db

# Server
HOST=0.0.0.0
PORT=8000
DEBUG=False

# Frontend (Vite)
VITE_API_BASE_URL=http://localhost:8000
```

> ⚠️ **Never commit your `.env` file.** It is already included in `.gitignore`.

---

## ⚙️ How It Works

1. **Patient Onboarding** — Clinician registers a new patient with vitals, photo, and medical report via the onboarding form.

2. **Diagnostic Input** — Clinical parameters (glucose, BMI, blood pressure, age, etc.) are submitted through the Diagnostic Hub.

3. **ML Inference** — The FastAPI backend runs all three XGBoost models simultaneously, returning risk probabilities for Diabetes, Heart Disease, and Hypertension.

4. **SHAP Explainability** — The SHAP engine calculates feature importance values for each prediction, pinpointing which clinical indicators contributed most.

5. **Claude NLP Summary** — The SHAP values and risk scores are sent to Anthropic Claude, which generates a structured plain-English clinical summary with actionable recommendations.

6. **AI Deep Analysis** — BioBERT + OpenFDA synthesizes evidence from clinical trials to provide deeper context alongside the prediction.

7. **Biomarker Trends** — Longitudinal charts track patient biomarkers (glucose, eGFR, etc.) over time to reveal trends.

8. **Audit & Analytics** — Every session is saved to SQLite. The Analytics dashboard aggregates population-level insights across all patients.

---

## 🔌 API Overview

Interactive Swagger docs available at `http://localhost:8000/docs` once the backend is running.

| Endpoint | Method | Description |
|---|---|---|
| `/predict` | `POST` | Run risk prediction for all 3 conditions |
| `/history` | `GET` | Retrieve past diagnostic sessions from the DB |
| `/health` | `GET` | Server health check |

**Example Request Body — `/predict`:**
```json
{
  "age": 52,
  "glucose": 148,
  "bmi": 31.2,
  "blood_pressure": 90,
  "cholesterol": 220,
  "smoking": 0,
  "family_history": 1
}
```

**Example Response:**
```json
{
  "diabetes_risk": 0.74,
  "heart_disease_risk": 0.31,
  "hypertension_risk": 0.88,
  "shap_values": { "glucose": 0.42, "bmi": 0.21, "age": 0.18 },
  "clinical_summary": "Patient presents elevated glucose and hypertension risk..."
}
```

---

## 🗺️ Roadmap

- [ ] Support for additional conditions (e.g., CKD, COPD, Stroke)
- [ ] OAuth2-based clinician authentication
- [ ] Export diagnostic reports as PDF
- [ ] FHIR-compliant patient data input format
- [ ] Docker containerization for easy cloud deployment
- [ ] Expanded unit and integration test coverage

---

## ⚠️ Disclaimer

> This system is built for **educational and hackathon purposes only**.
> It must **not** be used for actual clinical diagnosis or medical decision-making without rigorous validation and oversight by licensed medical professionals.
> All predictions are probabilistic estimates and do not constitute medical advice.

---

## 🙌 Acknowledgements

- [Anthropic Claude](https://www.anthropic.com/) — NLP clinical summary generation
- [SHAP Library](https://github.com/slundberg/shap) — Model explainability
- [XGBoost](https://xgboost.readthedocs.io/) — High-performance gradient boosting
- [FastAPI](https://fastapi.tiangolo.com/) — Elegant Python API framework
- [Tailwind CSS](https://tailwindcss.com/) — Rapid, responsive UI design
- [BioBERT](https://github.com/dmis-lab/biobert) — Biomedical NLP model
- [OpenFDA](https://open.fda.gov/) — Clinical trial & drug data API

---

<p align="center">Made with ❤️ for Hackathon 2026</p>
