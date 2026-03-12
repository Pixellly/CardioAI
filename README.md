# 🫀 CardioAI — Agentic Heart Disease Risk Assessment

![Status](https://img.shields.io/badge/status-research%20prototype-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Domain](https://img.shields.io/badge/domain-cardiology%20%7C%20AI-red)

> An agentic AI system that predicts cardiovascular disease risk from patient clinical data and automatically generates two tailored reports — one for physicians, one for patients.

---
## 🌐 Live demo:
[cardioai.github.io/YOUR_REPO_NAME](https://YOUR_USERNAME.github.io/YOUR_REPO_NAME)

---

## 📌 Overview

CardioAI demonstrates the role of **agentic AI in the heart disease domain**, as explored in our accompanying research paper. Given a patient's clinical measurements and medical history, the system:

1. **Predicts 10-year CVD risk** using a machine learning model trained on established cardiovascular risk factors
2. **Generates a clinical report** for physicians — with SHAP-based model explainability, factor-by-factor analysis, and evidence-based recommendations
3. **Generates a patient report** — in plain, accessible language with personalised action steps the patient can act on

This dual-report architecture reflects the paper's core argument: that agentic AI can bridge the gap between clinical decision support and patient health literacy simultaneously.

---

## ✨ Features

| Feature | Description |
|---|---|
| Patient intake form | Full clinical data entry: demographics, lab values, risk factors, medications |
| AI risk prediction | 10-year CVD risk score with confidence estimate |
| Physician report | SHAP explainability, risk factor panel, clinical recommendations |
| Patient report | Plain-language explanations and numbered action steps |
| Patient history log | Session-based history table of all assessments |
| Print / PDF export | One-click browser print for both reports |
| Standalone HTML | Runs entirely in the browser — no server, no dependencies |

---

## 🚀 Getting Started

### Option 1 — Open directly (no setup)

Download `cardiac_risk_ai.html` and open it in any modern browser. That's it.

```bash
# Or clone the repo
git clone https://github.com/YOUR_USERNAME/cardioai.git
cd cardioai
open cardiac_risk_ai.html   # macOS
start cardiac_risk_ai.html  # Windows
```

### Option 2 — GitHub Pages (live web URL)

1. Fork or push this repo to your GitHub account
2. Go to **Settings → Pages**
3. Set source to `main` branch, root folder
4. Your app will be live at: `https://YOUR_USERNAME.github.io/cardioai`

---

## 🗂️ Repository Structure

```
cardioai/
│
├── cardiac_risk_ai.html     # Main application (self-contained)
│
├── README.md                
├── LICENSE                   
│
└── paper/
    └── cardioai_paper.pdf 
       
```

---

## 🧠 How It Works

```
Patient Data Input
       │
       ▼
  Risk Scoring Model
  (Clinical features → 10-yr CVD risk %)
       │
       ├──────────────────────┐
       ▼                      ▼
 Physician Report         Patient Report
 ─────────────────         ──────────────
 • SHAP feature           • Plain-language
   attribution              explanations
 • Factor panel           • Personalised
 • Clinical recs            action steps
 • EHR export             • Print summary
```

The current implementation uses a validated heuristic risk model based on Framingham risk score methodology. **To connect your own ML model**, replace the `generateReport()` function in the HTML with an API call to your model backend.

---

## 🔬 Research Context

This tool accompanies our paper:

> **"Agentic AI in Cardiovascular Medicine: Automated Risk Stratification and Dual-Audience Report Generation"**
> *(Add full citation once published)*

The paper argues that agentic AI systems — those capable of perceiving patient data, reasoning over it, and generating targeted outputs — represent a significant opportunity in preventive cardiology, particularly for improving health literacy in high-risk populations.

---

## 🛠️ Connecting Your ML Model

The app is architected so the risk model is cleanly separable. To plug in your own model:

```javascript
// In cardiac_risk_ai.html, replace the scoring block inside generateReport()
// with a fetch call to your model API:

async function generateReport() {
  const patientData = collectFormData();  // collects all form fields

  const response = await fetch('https://your-model-api.com/predict', {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify(patientData)
  });

  const result = await response.json();
  // result = { score: 24, confidence: 0.91, shap_values: {...} }

  renderResults(result);
}
```

---

## 📋 Input Variables

| Variable | Type | Description |
|---|---|---|
| Age | Integer | Patient age in years |
| Biological sex | Categorical | Male / Female |
| Systolic BP | mmHg | Resting systolic blood pressure |
| Total cholesterol | mg/dL | Fasting total cholesterol |
| HDL cholesterol | mg/dL | High-density lipoprotein |
| LDL cholesterol | mg/dL | Low-density lipoprotein |
| Fasting glucose | mg/dL | Fasting blood glucose |
| BMI | kg/m² | Body mass index |
| Smoking status | Boolean | Current / former / never |
| Diabetes | Boolean | Type 1 or Type 2 diagnosis |
| Hypertension | Boolean | Diagnosed hypertension |
| Family history CVD | Boolean | First-degree relative with CVD |
| Previous cardiac event | Boolean | Prior MI, stroke, or angina |
| Physical inactivity | Boolean | Less than 150 min/week activity |

---

## ⚠️ Disclaimer

CardioAI is a **research prototype** and is not approved for clinical use. Risk scores are estimates based on population-level data and should not replace clinical judgment. All outputs must be reviewed by a qualified healthcare professional before informing patient care decisions.

---

## 📄 License

This project is licensed under the MIT License — see [LICENSE](LICENSE) for details.

---

## 👥 Authors

*Add your names, institution, and contact here.*

---

## 🙏 Acknowledgements

- Framingham Heart Study for risk factor methodology
- ACC/AHA cardiovascular risk guidelines
- SHAP (SHapley Additive exPlanations) for model interpretability framework
