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

This project builds predictive models and analytical tools to identify risk and improve transparency in organ allocation patterns.

Organizations want better insights into:
- Who is at highest risk while waiting 
- Expected wait times 
- Factors influencing successful transplants 


### Success Criteria

Success will be measured across three dimensions: model performance, deliverable quality, and insight value. 

[Challenge Advisor to add 3-5 bullets to expound on this]

### Project Milestones
Use these milestones to guide your work. Your team will create a GitHub Projects board to track tasks within each milestone.

| Weeks | Milestone | Key Activities |
|---|---|---|
| Weeks 1–2 | Business Understanding & Scoping | • Define use cases:<br>&nbsp;&nbsp;&nbsp;&nbsp;◦ "Which patients are at highest risk?"<br>&nbsp;&nbsp;&nbsp;&nbsp;◦ "What factors drive longer waits?"<br>• Create problem framing doc |
| Weeks 3–5 | Data Preparation | • Clean and merge datasets<br>• Handle missing values<br>• Feature engineering:<br>&nbsp;&nbsp;&nbsp;&nbsp;◦ Wait time duration<br>&nbsp;&nbsp;&nbsp;&nbsp;◦ Medical urgency scores<br>&nbsp;&nbsp;&nbsp;&nbsp;◦ Regional indicators |
| Weeks 6–8 | Modeling | • Build baseline models<br>• Evaluate:<br>&nbsp;&nbsp;&nbsp;&nbsp;◦ ROC-AUC (classification)<br>&nbsp;&nbsp;&nbsp;&nbsp;◦ Concordance index (survival models)<br>• Compare simple vs. advanced models |
| Weeks 9–10 | Evaluation & Insights | • Interpret models using SHAP<br>• Identify key drivers:<br>&nbsp;&nbsp;&nbsp;&nbsp;◦ Blood type mismatch delays<br>&nbsp;&nbsp;&nbsp;&nbsp;◦ Regional disparities<br>• Validate findings against domain knowledge |
| Weeks 11–12 | Deliverables | • GitHub repo (clean, reproducible pipeline)<br>• Jupyter notebooks<br>• Insight report (business-focused)<br>• Optional dashboard (Streamlit) |

---

## 📊 Dataset
**Name and Source:** OPTN National Transplant Data (STAR files)  
**Format:** CSV / Structured Data and Unstructured Text  
**Size:** Less than 1 GB  
**Location:** https://optn.transplant.hrsa.gov/data/view-data-reports/national-data/

### Key Details
- [Brief description of what's in the data]
- [Any known limitations or preprocessing needed]
- [Link to data dictionary or documentation, if available]
  
---

## 🛠️ Suggested Approach

**ML Problem Type:** Classification & Survival Analysis

**Recommended Libraries:**
- [e.g., pandas, scikit-learn, TensorFlow, Hugging Face]

**Evaluation Metrics:**
- [e.g., Accuracy, Precision/Recall, RMSE, BLEU score]

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

**Official check-ins:** During our biweekly 45-minute AI Studio Lab Section meeting block (2nd and 4th week of every month)

 **Other ways to reach out to me with questions:** 
* [e.g., Your team's channel within Break Through Tech’s Discord space]
* [e.g., Email; please copy your teammates and AI Studio Coach]
* [e.g., Request a team check-in on Zoom]
* [Note: I will aim to respond within 48 hours. Please reach out to your AI Studio Coach with urgent questions.]

> 💡 **Challenge Advisor: Please update the above based on your availability and preference. If you are not able to answer questions or meet with fellows outside of the biweekly Lab Section check-ins, simply write in "N/A (only available during the official check-in times)"**

**Recommended free coding / collaboration tools**
* […]
* […]

---

## 🚀 Getting Started

1. **Review this overview document** and note any questions for our first meeting
2. **Begin reviewing the dataset** using the link above
3. **Read the GitHub Projects documentation** [here](https://docs.github.com/en/issues/planning-and-tracking-with-projects/learning-about-projects/about-projects)

I’m excited to work with you!

---

## ❓ Questions?

Please bring any questions to our first meeting during the week of August 24th (Break Through Tech’s Bridge to Studio - Session C). 
