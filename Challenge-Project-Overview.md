# Predicting Organ Transplant Waitlist Outcomes & Optimizing Allocation

**Company / Org:** MediMate Foundation  
**Challenge Advisor:** Deepti Bahel, baheldeepti@gmail.com  
**Program:** Break Through Tech AI Studio — Fall 2026

---

## 🏢 About MediMate Foundation

MediMate Foundation is a California nonprofit building AI-powered navigation tools for patients and caregivers in the kidney and transplant space. Grounded in lived patient experience, our work focuses on transparency, equity, and risk assessment across the organ allocation process — helping patients, clinicians, and the broader community understand who is at risk while waiting and why.

---

## 🎯 The Challenge

### Project Summary
This project builds predictive models and analytical tools to identify risk and improve transparency in organ allocation. The goal is to surface which waitlist patients are at highest risk, estimate expected wait times, and quantify the geographic and systemic factors that influence transplant outcomes — in a way that is fair across patient subgroups and explainable to non-technical stakeholders.

### Success Criteria
Model performance targets: ROC-AUC ≥ 0.78, PR-AUC ≥ 0.65, Brier score ≤ 0.18, lift in top decile ≥ 2.5×, and C-index ≥ 0.72. Success is also measured by **fairness** (subgroup performance within 0.05 AUC across race/ethnicity, sex, and region) and by the quality of the final deliverables (model, explainability analysis, and stakeholder-facing write-up/dashboard).

### Project Milestones

Use these milestones to guide your work. Your team will create a **GitHub Projects board** to track tasks within each milestone.

| Month        | Milestone                  | Key Activities                                                        |
|--------------|----------------------------|----------------------------------------------------------------------|
| **September**| Data Understanding         | Explore dataset, handle missing values, document findings            |
| **October**  | Model Development          | Train baseline model, experiment with approaches, iterate            |
| **November** | Evaluation & Presentation  | Finalize model, prepare presentation, document results               |

> **Note for the team:** Create a GitHub Projects board in this repository to break these milestones into weekly tasks. Go to the **Projects** tab → **New project** → choose **Board** → add a column for each month.

---

## 📊 Dataset

There are **two** datasets for this project: a **download-now starter dataset** (so the team is productive in week 1) and a **scale-up target** (the U.S. national registry, which requires a request). Start on the first; move to the second if/when access clears.

### ▶️ Primary — start here (instant download, no request)

**Name & Source:** **Kidney Transplant Waitlist (Brazil / SP-OAS)** — a de-identified, patient-level kidney waitlist dataset from the São Paulo State Organ Allocation System, published openly on Kaggle.
- **Download:** https://www.kaggle.com/datasets/gustavomodelli/waitlist-kidney-brazil
- **Size:** ~54,000 candidate records (Jan 2000 – Dec 2017) — large enough to be real, small enough for Google Colab / free tiers. **No DUA, no fee, no wait.**
- **Why it fits:** It's a true waitlist-outcomes dataset with the exact structure this project needs — candidate features at registration (age, blood group, panel-reactive antibody/PRA, region/subregion, dialysis time, etc.) and time-to-event outcomes (deceased-donor transplant vs. death/removal vs. still waiting). It directly supports classification **and** survival modeling (Cox PH → C-index), so the whole metric suite (ROC-AUC, PR-AUC, Brier, lift, C-index) and the fairness/subgroup check all apply.
- **Provenance:** It's the dataset behind a peer-reviewed ML wait-time study (PLOS One, 2021 — Cox model, ~54k records), so the team has a published reference pipeline to benchmark against. A worked Kaggle notebook also exists (see Code Examples).
- **Note:** It's a Brazilian state system, not the U.S. — the *methods transfer directly*, but allocation rules differ from OPTN. Treat conclusions as method demonstrations, not U.S. policy claims.

> *Optional additional starter sets to explore on Kaggle (verify license/provenance before relying on them): `fkshaikh/organ-transplant-dataset`, `subhrajyotinath/organdonation`.*

### ⬆️ Scale-up target — U.S. national data (request required)

**Name & Source:** OPTN **Standard Transplant Analysis and Research (STAR)** files — the national U.S. transplant registry, maintained by OPTN / UNOS under contract with HRSA. This is the dataset MediMate ultimately cares about; use it once the pipeline works on the starter data.

**Format:** De-identified, patient-level *limited dataset* across linked tables (waitlist candidates, deceased/living donors, transplants, waitlist history, follow-ups), in **SAS, Stata, or tab-delimited** formats. Structured fields (blood type, OPTN region, age, sex, race/ethnicity, diagnosis, medical-urgency scores) plus some free-text (cause-of-death narratives, comorbidity notes). Coverage back to **Oct 1, 1987**, updated **quarterly**.

**Size:** Scales with the organ(s) and window requested — the cumulative multi-organ file since 1987 runs into the **millions of rows**. For context, 100,000+ candidates are on the U.S. waitlist at any time (~103,000 in recent OPTN reporting, ~85–87% kidney). **Recommended scope:** kidney candidates only, ~2010 onward, to stay in the low hundreds of thousands of rows.

**Access:** Public but **not instant** — request via the OPTN Data Request page, sign a **Data Use Agreement (DUA)**, and the file is delivered **within 30 days of the signed DUA** (custom/aggregate cuts may carry a fee).

> ⏱️ **If the team wants STAR for the final model, submit the request in August** so it arrives for the September milestone. The starter dataset means students are **never blocked** in the meantime.

**Links:**
- Request the STAR file → https://optn.transplant.hrsa.gov/data/request-data/
- Instructions, DUA, and STAR Data Dictionary (XLSX) → https://optn.transplant.hrsa.gov/data/view-data-reports/request-data/data-request-instructions/
- Public **aggregate** national data, no DUA (good for context/EDA) → https://optn.transplant.hrsa.gov/data/
- OPTN/SRTR Annual Data Report, no DUA → https://srtr.hrsa.gov/adr/
- Contacts: `datarequest@unos.org` · `STARFile@unos.org`

### Key Details — known limitations & preprocessing (applies to both datasets)
- **Censoring / time-to-event:** Many candidates are still waiting at the data cut (right-censored). Use **survival methods (Cox PH / time-to-event)** for wait-time — not plain regression — which is why C-index is a target metric.
- **Class imbalance:** Adverse outcomes (waitlist mortality/removal) are rare. Lead with **PR-AUC and calibration (Brier)**, not ROC-AUC alone.
- **Missingness:** Document missingness patterns and pick a principled imputation strategy; don't silently drop rows.
- **Fairness & leakage:** Demographic and region fields are present — required for the subgroup fairness check. Watch for proxy leakage; don't let the model simply re-learn historical allocation bias.
- **Free-text fields (STAR only):** Cause-of-death / comorbidity notes need NLP. Do a **structured-fields-only baseline first**, then optionally add text features (LLM-assisted extraction is fine).
- **Policy/distribution shift (STAR):** U.S. kidney allocation rules changed (notably 2014 and 2021). Restrict the window or encode era as a feature.
- **⚠️ Data handling:** Keep raw row-level data **out of this public repo** (`.gitignore` it) — especially STAR, which is DUA-governed. Commit only code, aggregates, and figures.

---

## 🛠️ Suggested Approach

**ML Problem Type:** Classification (primary — e.g., predicting an adverse waitlist outcome within a fixed horizon), with a **time-to-event / survival** component for wait-time and risk-over-time.

**Recommended Libraries / Tools:**
- **XGBoost** — gradient-boosted baseline and main model
- **scikit-learn** — Logistic Regression baseline, calibration, metrics
- **lifelines** — Cox Proportional Hazards & survival analysis in Python
- **SHAP** — model explainability / feature attribution
- **Streamlit** — interactive risk/transparency dashboard
- **Jupyter Notebooks**, **Google Colab** — development
- **GitHub**, **Docker**, **CI/CD** — collaboration & reproducibility
- **LLMs (Claude / GPT)** — optional NLP on free-text fields, documentation support

**Evaluation Metrics:** ROC-AUC · PR-AUC · Brier score · lift in top decile · C-index — plus **subgroup AUC** for the fairness check.

---

## 📚 Resources to Get Started

**Background Reading**
- Reference paper for the starter dataset — "A machine learning prediction model for waiting time to kidney transplant" (PLOS One, 2021; Cox model on the SP-OAS data) — https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0252069
- OPTN national data & policy overview — https://optn.transplant.hrsa.gov/data/
- OPTN/SRTR Annual Data Report (methodology, risk adjustment, outcomes) — https://srtr.hrsa.gov/adr/
- Organ donation & transplant statistics primer — https://www.organdonor.gov/learn/organ-donation-statistics

**Technical Tutorials**
- XGBoost documentation — https://xgboost.readthedocs.io/
- scikit-learn (Logistic Regression, metrics, probability calibration) — https://scikit-learn.org/stable/
- lifelines — survival analysis & Cox PH in Python — https://lifelines.readthedocs.io/
- SHAP — model explainability — https://shap.readthedocs.io/
- Streamlit — building the dashboard — https://docs.streamlit.io/

**Code Examples**
- Worked Kaggle notebook on the starter dataset (wait-time prediction) — https://www.kaggle.com/code/rahultheogre/transplant-wait-time-prediction-phase-one
- lifelines Quickstart (Cox PH worked example) — https://lifelines.readthedocs.io/en/latest/Quickstart.html
- scikit-learn — probability calibration guide — https://scikit-learn.org/stable/modules/calibration.html
- SHAP — example notebooks (see "Example Notebooks" in the docs) — https://shap.readthedocs.io/

**Other**
- For the U.S. STAR file only: confirm fees and turnaround when you submit the DUA (drives the August timeline).

*Feel free to explore beyond these, and share anything interesting you find with me!*

---

## 🤝 How We'll Work Together

**Check-ins:** During our biweekly 60-min AI Studio Lab Section meeting block (2nd and 4th week of every month)  
**Communication:** Slack (Break Through Tech workspace)  
**Response time:** Within 48 hours on weekdays  

**Recommended Tools:**
- **Coding:** Google Colab, VS Code
- **Collaboration:** GitHub, Notion
- **Virtual Meetings:** Zoom, Google Meet

---

## 🚀 Getting Started

1. **Review this overview** and note any questions for our first meeting.
2. **Download the starter dataset now** (no request needed) — https://www.kaggle.com/datasets/gustavomodelli/waitlist-kidney-brazil — and start EDA + a baseline model in week 1.
3. **(Optional, for the U.S. national model) Submit the OPTN STAR request in August** so it arrives for September; the starter dataset keeps you unblocked while it processes.
4. **Read the GitHub Projects documentation** — https://docs.github.com/en/issues/planning-and-tracking-with-projects/learning-about-projects/about-projects

I'm excited to work with you!

---

## ❓ Questions?

Please bring any questions to our first meeting during the week of **August 24th** (Break Through Tech's *Bridge to Studio* — Session B).
