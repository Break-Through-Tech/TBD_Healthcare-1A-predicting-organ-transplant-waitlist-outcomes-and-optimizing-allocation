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
Model performance targets: ROC-AUC ≥ 0.78, PR-AUC ≥ 0.65, Brier score ≤ 0.18, lift in top decile ≥ 2.5×, and C-index ≥ 0.72. Success is also measured by **fairness** (subgroup performance within 0.05 AUC across the available demographic and regional subgroups, e.g. age, sex, blood group, and region) and by the quality of the final deliverables (model, explainability analysis, and stakeholder-facing write-up/dashboard).

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

This project works with **publicly available, openly downloadable data** — no data-use agreement, application, or wait. The working dataset is real, patient-level transplant waitlist data; U.S. national registry resources are used only as public context.

### Working dataset (public, instant download)

**Name & Source:** **Kidney Transplant Waitlist (Brazil / SP-OAS)** — a de-identified, patient-level kidney waitlist dataset from the São Paulo State Organ Allocation System, published openly on Kaggle.
- **Download:** https://www.kaggle.com/datasets/gustavomodelli/waitlist-kidney-brazil
- **Size:** ~54,000 candidate records (Jan 2000 – Dec 2017) — large enough to be real, small enough to run on Google Colab / free tiers. **Public, no DUA, no fee, no wait.**
- **Why it fits:** It's a true waitlist-outcomes dataset with exactly the structure this project needs — candidate features at registration (age, sex, blood group, panel-reactive antibody/PRA, subregion, dialysis time, etc.) and time-to-event outcomes (deceased-donor transplant vs. death/removal vs. still waiting). It supports classification **and** survival modeling (Cox PH → C-index), so the full metric suite (ROC-AUC, PR-AUC, Brier, lift, C-index) and the subgroup-fairness check all apply.
- **Provenance / data dictionary:** It's the dataset behind a peer-reviewed ML wait-time study (PLOS One, 2021 — Cox model, ~54k records). Column descriptions live on the Kaggle dataset page; the paper's variable tables serve as the data dictionary. A worked Kaggle notebook also exists (see Code Examples).
- **Scope note:** It's a Brazilian state system, so frame findings as **transferable methods**, not U.S. policy claims. The modeling approach (risk + wait-time + fairness) is identical to what you'd run on any national registry.

> *Optional additional public datasets to explore on Kaggle (verify license/columns before relying on them): `fkshaikh/organ-transplant-dataset`, `subhrajyotinath/organdonation`.*

### Public U.S. context (no download/modeling required — background only)

For grounding the problem in U.S. numbers and policy, these are freely viewable (no DUA):
- OPTN national data & dashboards → https://optn.transplant.hrsa.gov/data/
- OPTN/SRTR Annual Data Report → https://srtr.hrsa.gov/adr/
- Organ donation & transplant statistics primer → https://www.organdonor.gov/learn/organ-donation-statistics

> *The U.S. patient-level registry (OPTN "STAR" file) exists but requires a signed data-use agreement and a multi-week turnaround, so it is **out of scope** for this project. We build entirely on the public dataset above.*

### Key Details — known limitations & preprocessing
- **Censoring / time-to-event:** Many candidates are still waiting at the data cut (right-censored). Use **survival methods (Cox PH / time-to-event)** for wait-time — not plain regression — which is why C-index is a target metric.
- **Class imbalance:** Adverse outcomes (waitlist mortality/removal) are rarer than transplants. Lead with **PR-AUC and calibration (Brier)**, not ROC-AUC alone.
- **Missingness:** Document missingness patterns and pick a principled imputation strategy; don't silently drop rows. (The published study excluded a small number of records missing subregion — note any exclusions you make.)
- **Competing risks:** Transplant, death, and removal are competing outcomes. A plain Cox model can bias wait-time estimates; consider a competing-risks framing and compare.
- **Fairness & leakage:** Use the available demographic/regional fields (age, sex, blood group, subregion) for the subgroup-fairness check. Watch for proxy leakage and don't let the model simply re-learn historical allocation patterns.
- **Distribution shift:** The data spans ~18 years; allocation practice can change over that window. Consider encoding registration era or restricting the window, and check stability over time.
- **⚠️ Data handling:** Even though this dataset is public, keep raw row-level CSVs **out of this repo** (`.gitignore` them) and commit only code, aggregates, and figures — good hygiene and lighter for Git.

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
- **LLMs (Claude / GPT)** — optional support for feature ideas, code review, and documentation (the dataset is structured/tabular, so no free-text NLP is required)

**Evaluation Metrics:** ROC-AUC · PR-AUC · Brier score · lift in top decile · C-index — plus **subgroup AUC** for the fairness check.

---

## 📚 Resources to Get Started

**Background Reading**
- Reference paper for the project dataset — "A machine learning prediction model for waiting time to kidney transplant" (PLOS One, 2021; Cox model on the SP-OAS data) — https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0252069
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
- Worked Kaggle notebook on this dataset (wait-time prediction) — https://www.kaggle.com/code/rahultheogre/transplant-wait-time-prediction-phase-one
- lifelines Quickstart (Cox PH worked example) — https://lifelines.readthedocs.io/en/latest/Quickstart.html
- scikit-learn — probability calibration guide — https://scikit-learn.org/stable/modules/calibration.html
- SHAP — example notebooks (see "Example Notebooks" in the docs) — https://shap.readthedocs.io/

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
2. **Download the dataset now** (no request needed) — https://www.kaggle.com/datasets/gustavomodelli/waitlist-kidney-brazil — and start EDA + a baseline model in week 1.
3. **Skim the reference paper and worked notebook** (linked in Resources) to see an end-to-end pipeline on this exact data.
4. **Read the GitHub Projects documentation** — https://docs.github.com/en/issues/planning-and-tracking-with-projects/learning-about-projects/about-projects

I'm excited to work with you!

---

## ❓ Questions?

Please bring any questions to our first meeting during the week of **August 24th** (Break Through Tech's *Bridge to Studio* — Session B).
