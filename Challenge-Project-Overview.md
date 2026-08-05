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

| Check | Status | Notes |
|-------|--------|-------|
| Python Compatibility | 🟢 | The project uses Python-based tools (XGBoost, Jupyter, Streamlit) and is compliant with institutional ML engineering standards. |
| Data Readiness | 🟡 | The data is publicly available; however, without a specified size, there is a risk of encountering large data that may require excessive preprocessing work. |
| Resource Check | 🟢 | The project primarily utilizes accessible, free-tier tools, eliminating barriers to entry for students. |

**Student Fit Score:** 7/10  
**Technical Depth Score:** 8/10  
**Overall Recommendation:** REVISE

**Advisor Feedback Draft:**
The project demonstrates a clear understanding of how to address a socially relevant issue and leverage advanced modeling techniques. However, focus should be placed on ensuring data accessibility and management for students' success. Comprehensive onboarding and clear guidelines on handling data complexity will be crucial.

---

# Predicting Organ Transplant Waitlist Outcomes & Optimizing Allocation

**Company / Org:** Other  
**Challenge Advisor:** Deepti Bahel, baheldeepti@gmail.com  
**AI Studio Coach: ** Nagalakshmi Pulivarthi, nagalakshmi.pulivarthi@breakthroughtech.org
**Program:** Break Through Tech AI Studio - Fall 2026

---

## 🏢 About Other

Other is dedicated to improving healthcare outcomes through advanced analytics and predictive modeling. Our focus is on transparency and risk assessment in the organ allocation process.

---

## 🎯 The Challenge

### Project Summary
This project builds predictive models and analytical tools to identify risk and improve transparency in organ allocation patterns. The goal is to provide insights into which patients are at highest risk while waiting, expected wait times, and geographic or systemic factors influencing transplant success.

### Success Criteria
Model performance targets: ROC-AUC >= 0.78, PR-AUC >= 0.65, Brier score <= 0.18, Lift in top decile >= 2.5x, and C-index >= 0.72. Success is also measured by fairness (subgroup performance within 0.05 AUC) and deliverable quality.

### Project Milestones

Use these milestones to guide your work. Your team will create a **GitHub Projects board** to track tasks within each milestone.

| Month      | Milestone          | Key Activities                                                  |
|------------|--------------------|----------------------------------------------------------------|
| **September**  | Data Understanding | Explore dataset, handle missing values, document findings       |
| **October**    | Model Development  | Train baseline model, experiment with approaches, iterate      |
| **November**   | Evaluation & Presentation | Finalize model, prepare presentation, document results        |

> **Note for the team:** Please create a GitHub Projects board in this repository to break these milestones into weekly tasks. Go to the **Projects** tab → **New project** → Choose **Board** → Add columns for each month.

---

## 📊 Dataset

**Name and Source:** OPTN national transplant data  
**Format:** Structured and unstructured data (e.g., STAR files)  
**Size:** unknown  
**Location:** [Insert link to dataset or instructions for accessing it]

### Key Details
- Publicly available OPTN national transplant data, including STAR files with structured patient data (blood type, region, age, sex, race/ethnicity, medical urgency scores) and unstructured free-text fields for cause of death narratives and comorbidity notes.
- [Any known limitations or preprocessing needed]
- [Link to data dictionary or documentation, if available]

---

## 🛠️ Suggested Approach

**ML Problem Type:** Classification

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

**Evaluation Metrics:**
- ROC-AUC
- PR-AUC
- Brier score
- Lift in top decile
- C-index

---

## 📚 Resources to Get Started

The following resources will help your team understand the problem space and potential technical approaches for this project:

**Background Reading:**
- [e.g., Link to an article or blog post about the problem domain]
- [e.g., Link to an industry report or case study]

**Technical Tutorials:**
- [e.g., Link to a free tutorial on the ML technique(s) involved]
- [e.g., Link to documentation for a key library or tool]

**Code Examples:**
- [e.g., Link to a relevant GitHub repo]
- [e.g., Link to a sample implementation or starter code]

**Other:**
- [Links to any additional resources — e.g., papers, videos, podcasts, etc.]

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

1. **Review this overview document** and note any questions for our first meeting
2. **Begin reviewing the dataset** using the link above
3. **Read the GitHub Projects documentation** [here](https://docs.github.com/en/issues/planning-and-tracking-with-projects/learning-about-projects/about-projects)

I'm excited to work with you!

---

## ❓ Questions?

Please bring any questions to our first meeting during the week of August 24th (Break Through Tech's Bridge to Studio - Session B).


---
