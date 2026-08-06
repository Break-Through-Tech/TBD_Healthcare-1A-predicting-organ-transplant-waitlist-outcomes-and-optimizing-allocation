---

> ## Challenge Advisor: Update & Finalize Your Project Overview
>
> > 💡 **These grey text instructions are just for you, the team's Challenge Advisor; please delete them once you have completed the steps below.**
>
> We've pre-populated this Challenge Project Overview page — which is what will be shared with your Break Through Tech student team in August — using the details from your submission form. You should have received an email inviting you to join this repo as a Collaborator, enabling you to add files and make edits.
> 
> In order for your project to be finalized and assigned to a team, please:
> 1. **Review all sections below** and update or expand any content as needed, making sure to address the SME Feedback in the section immediately below. Look for square brackets to find the places below that require additional inputs from you (e.g., "About [Company / Org Name]").
> 2. **Add your dataset** to the [data folder](data) in this repo.
> 3. **Close the Issue assigned to you in this repo** to let us know that you have made your edits and the overview page is ready for final review. You can do this by going to the _Issues_ tab in the top left section of the menu above, add a comment that says "CA review complete", and click the button to Close the Issue. 
>
> If you're unfamiliar with how to edit a page like this in GitHub, check out [this tutorial](https://ubc-lib-geo.github.io/gis-workshop-waml-template/content/handson/edit-readme.html) for a quick overview (start with step 2 and only edit this page), and [this guide](https://ubc-lib-geo.github.io/gis-workshop-waml-template/content/markdown.html) on how to use Markdown to compose text.
>
>
> ❌ Remember that this is a public repo. Do NOT include: Proprietary data, PII, API keys, credentials, or anything confidential.

---

## 📋 BTT Internal Evaluation Notes
*(This section is for BTT staff only — remove before sharing with students)*

### Technical Vetting
| Check | Status | Notes |
| :--- | :--- | :--- |
| Python Compatibility | 🟢 | The project uses Python-based tools (XGBoost, Jupyter, Streamlit) and is compliant with institutional ML engineering standards. |
| Data Readiness | 🟡 | The data is publicly available; however, without a specified size, there is a risk of encountering large data that may require excessive preprocessing work. |
| Resource Check | 🟢 | The project primarily utilizes accessible, free-tier tools, eliminating barriers to entry for students. |

### Internal Scores
- **Student Fit Score:** 7/10
- **Technical Depth Score:** 8/10
- **Overall Recommendation:** REVISE

### Advisor Feedback Draft
The project shows a clear understanding of how to address a socially relevant issue and leverage advanced modeling techniques. However, focus should be placed on ensuring data accessibility and management for students' success. Comprehensive onboarding and clear guidelines on handling data complexity will be crucial.

---

# Predicting Organ Transplant Waitlist Outcomes & Optimizing Allocation

**Company / Org:** Other  
**Challenge Advisor:** Deepti Bahel, baheldeepti@gmail.com  
**Program:** Break Through Tech AI Studio - Fall 2026  

---

## 🏢 About Other
This project operates within the public health and medical logistics sector, focusing on organ transplant allocation. The team's primary objective is to develop analytical tools that increase transparency and improve patient outcomes by identifying systemic inefficiencies in the current organ distribution infrastructure.

---

## 🎯 The Challenge
### Project Summary
The team will build predictive models and analytical dashboards to assess risk levels for patients on organ transplant waitlists and analyze geographic or systemic factors influencing transplant success. By utilizing OPTN national transplant datasets and integrating ML techniques like XGBoost and survival analysis (Cox PH), the project aims to produce actionable insights that support more equitable and efficient organ allocation decisions.

### Success Criteria
Model performance targets: ROC-AUC >= 0.78, PR-AUC >= 0.65, Brier score <= 0.18, Lift in top decile >= 2.5x, and C-index >= 0.72. Success is also measured by fairness (subgroup performance within 0.05 AUC) and deliverable quality.

### Project Milestones
Use these milestones to guide your work. Your team will create a GitHub Projects board to track tasks within each milestone.

| Month | Milestone | Key Activities |
| :--- | :--- | :--- |
| September | Business Scoping, Data Preparation & Feature Engineering | • Define key clinical use cases ("Which patients are at highest risk?", "What factors drive longer waits?") and frame problem.<br>• Clean and merge organ donation datasets; handle missing values.<br>• Engineer domain features including wait time durations, medical urgency scores, and regional indicators. |
| October | Predictive & Survival Modeling | • Build baseline and advanced machine learning models.<br>• Train classification and survival models (e.g., Cox Proportional Hazards) to predict waitlist outcomes.<br>• Evaluate performance using ROC-AUC (classification) and Concordance index ($C$-index for survival models). |
| November / December | Model Evaluation, Interpretability & Final Deliverables | • Interpret model predictions using SHAP to identify key risk drivers (e.g., blood type mismatch delays, regional disparities).<br>• Validate empirical findings against domain knowledge and literature.<br>• Develop an interactive Streamlit dashboard to visualize patient risk and allocation patterns.<br>• Finalize clean GitHub repository, Jupyter notebooks, business insight report, and final presentation. |

### Stretch Goals
* **Pipeline Containerization & CI/CD:** Containerize the data pipeline with Docker and implement CI/CD for quarterly dataset refreshes.
* **Model & Policy Drift Detection:** Implement drift monitoring to evaluate whether model accuracy degrades as organ allocation policies change.
* **Authenticated Cloud Deployment:** Deploy the Streamlit application to a secure live web server with user authentication.
> **Note for the team:** Please create a GitHub Projects board in this repository to break these milestones into weekly tasks. Go to the **Projects** tab → **New project** → Choose **Board** → Add columns for each month.

---

## 📊 Dataset
**Name and Source:** OPTN National Transplant Data (STAR files)  
**Format:** CSV / Structured Data and Unstructured Text  
**Size:** unknown  
**Location:** Publicly available via OPTN/UNOS data request portals.  

### Key Details
- Publicly available OPTN national transplant data, including STAR files with structured patient data (blood type, region, age, sex, race/ethnicity, medical urgency scores) and unstructured free-text fields for cause of death narratives and comorbidity notes.
- Data must be cleaned to address potential missingness in longitudinal follow-up records and normalized for consistency across different transplant center reporting standards.

---

## 🛠️ Suggested Approach
**ML Problem Type:** Classification & Survival Analysis  
**Recommended Libraries:**
- XGBoost
- Logistic Regression
- Cox Proportional Hazards (Cox PH)
- SHAP
- Streamlit
- GitHub
- Jupyter Notebooks
- Docker
- CI/CD
- Large Language Models (LLMs) such as Claude or GPT
- Google Colab
**Evaluation Metrics:** ROC-AUC, PR-AUC, Brier score, Lift in top decile, and C-index (with specific attention to subgroup fairness metrics).

---

## 📚 Resources to Get Started
The following resources will help your team understand the problem space and potential technical approaches for this project:
**Background Reading:**
- Official OPTN Data Policy and Organ Allocation System documentation.
**Technical Tutorials:**
- Scikit-survival documentation for Cox PH implementations and XGBoost classification guides.
**Code Examples:**
- Starter template repositories featuring standard EDA and SHAP visualization pipelines.

---

## 🤝 How We'll Work Together
**Check-ins:** During our biweekly 60-min AI Studio Lab Section meeting block (2nd and 4th week of every month)  
**Communication:** Email and scheduled lab session discussions.  
**Response time:** 48-hour response window for non-urgent project queries.  
**Recommended Tools:**
- **Coding:** Google Colab Free Tier  
- **Collaboration:** GitHub, Notion  
- **Virtual Meetings:** Zoom, Google Meet  

---

## 🚀 Getting Started
1. **Review this overview document** and note any questions for our first meeting.
2. **Begin reviewing the dataset** using the link provided in the Dataset section.
3. **Read the GitHub Projects documentation** [here](https://docs.github.com/en/issues/planning-and-tracking-with-projects/learning-about-projects/about-projects).

I'm excited to work with you!

---

## ❓ Questions?
Please bring any questions to our first meeting during the week of August 24th (Break Through Tech's Bridge to Studio - Session B).

Please bring any questions to our first meeting during the week of August 24th (Break Through Tech's Bridge to Studio - Session B).


---
