# 🏥 Value-Based Care Optimization: Predicting 30-Day Hospital Readmissions

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Scikit-Learn](https://img.shields.io/badge/Machine%20Learning-Scikit--Learn-orange.svg)
![Power BI](https://img.shields.io/badge/Dashboard-Power%20BI-yellow.svg)
![Business Value](https://img.shields.io/badge/Focus-Value--Based%20Healthcare-brightgreen.svg)

## 📌 The Business Problem
Under the **Value-Based Reimbursement (VBR)** model, hospitals are penalized heavily for 30-day patient readmissions. Traditional Machine Learning approaches often focus purely on predictive accuracy, ignoring the operational capacity of the hospital and the financial asymmetry between intervention costs and readmission penalties.

**The Goal:** Build an end-to-end ML pipeline and an interactive BI dashboard that doesn't just predict readmissions, but optimally allocates a limited hospital intervention budget to **maximize net financial savings.**

## 📊 Dataset & Feature Engineering
* **Data Source:** UCI Diabetes 130-US Hospitals (1999-2008)
* **Shape:** 101,766 encounters, 50 features.
* **Engineering:** 
  * Handled severe class imbalance (only ~11% readmission rate).
  * Grouped hundreds of granular ICD-9 codes into 9 primary clinical categories (Circulatory, Respiratory, Diabetes, etc.) using domain knowledge.
  * Encoded categorical variables and handled missing values systematically.

## 🤖 Machine Learning & The "Threshold Problem"
A standard Random Forest model with a default `0.5` decision threshold yielded a **Recall of 0.00** for the minority class due to the extreme class imbalance. 

Instead of discarding the model, I shifted the focus from static predictions (`.predict()`) to probabilistic risk scoring (`.predict_proba()`). By introducing a custom **Cost Matrix**:
* **Cost of False Negative (Penalty):** €10,000
* **Cost of Intervention:** €500

I identified that dynamically lowering the decision threshold to `0.05` mathematically maximized hospital savings while catching the highest-risk patients.

## 💡 The Solution: Interactive Power BI Dashboard
Instead of hardcoding the threshold, I developed a Power BI dashboard equipped with a **What-If Parameter (Risk Threshold)**. This empowers Hospital Administrators and Chief Medical Officers (CMOs) to dynamically adjust the AI's sensitivity based on their monthly intervention capacity and budget.

*(Include a GIF or Screenshot of your Power BI Dashboard here)*
![Dashboard Screenshot](path/to/your/screenshot.png) 

### Key Dashboard Metrics:
* **Net Savings:** Real-time calculation of € saved vs. the baseline (no AI) scenario.
* **Actionable Patient Roster:** An automatically sorted matrix delivering the highest-risk patients directly to the care team.

## 🛠️ Tech Stack
* **Data Engineering & ML:** Python, Pandas, NumPy, Scikit-Learn (Random Forest)
* **Business Intelligence:** Power BI, DAX (Dynamic Measures & What-If Parameters)
* **Environment:** VS Code, Jupyter Notebooks

## 👨‍💻 About the Author
**Emin Oral**
Data Science & Engineering Msc. @ Politecnico di Torino.
Passionate about bridging the gap between advanced predictive modeling and real-world business strategy.

Connect with me on [LinkedIn](https://www.linkedin.com/in/muhammedeminoral/)
