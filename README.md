# 📉 MTN Customer Churn Prediction
> A machine learning solution to identify at-risk customers before they leave — enabling data-driven retention at scale.

---

## 📌 Project Overview

Customer churn is one of the most costly and preventable problems in the telecom industry. This project builds an end-to-end churn prediction pipeline for MTN, using historical customer data to flag customers who are likely to cancel their subscription in the upcoming billing cycle.

The model outputs a **churn probability score** for every active customer, enabling the retention team to prioritise outreach, personalise offers, and protect revenue — before customers are lost.

---

## 🎯 Business Objective

> *"Which customers are most at risk of leaving MTN, and what does acting on that signal save us?"*

| Without This Model | With This Model |
|---|---|
| Churn discovered after the fact | Churn predicted before it happens |
| Untargeted retention campaigns | Risk-tiered, personalised outreach |
| No visibility into at-risk segments | Segment-level churn rates surfaced |
| Revenue lost silently | Revenue protected proactively |

---

## 📁 Project Structure

```
mtn-churn-prediction/
│
├── mtn_churn_improved.ipynb        # Main analysis & model notebook
├── mtn_customer_churn.csv          # Source dataset (not included — see Data section)
├── mtn_churn_model_v1.pkl          # Trained model (generated on run)
├── mtn_churn_model_v1_metadata.json # Model performance metadata (generated on run)
└── README.md                       # This file
```

---

## 🗂️ Notebook Structure

The notebook is organised into five sections:

| Section | Description |
|---|---|
| **1. Data Loading & Cleaning** | Load raw data, fix data types, standardise categoricals |
| **2. Exploratory Analysis** | Churn rate baseline, segment-level analysis, correlation heatmap |
| **3. Churn Predictor** | Model training, cross-validation, threshold tuning, evaluation |
| **4. Business Impact** | Revenue model, ROI calculation, threshold sensitivity analysis |
| **5. Future Improvements** | Prioritised roadmap for production deployment |

---

## 🧰 Tech Stack

| Tool | Purpose |
|---|---|
| `Python 3.10+` | Core language |
| `pandas` / `numpy` | Data manipulation |
| `scikit-learn` | Model training & evaluation |
| `matplotlib` / `seaborn` | Visualisation |
| `joblib` | Model serialisation |

---

## ⚙️ Setup & Installation

**1. Clone the repository**
```bash
git clone https://github.com/your-username/mtn-churn-prediction.git
cd mtn-churn-prediction
```

**2. Install dependencies**
```bash
pip install pandas numpy scikit-learn matplotlib seaborn joblib jupyter
```

**3. Add your dataset**

Place your `mtn_customer_churn.csv` file in the project root. The dataset should contain the following columns:

| Column | Description |
|---|---|
| `Customer ID` | Unique customer identifier |
| `Full Name` | Customer name |
| `State` | Customer location |
| `Gender` | Customer gender |
| `MTN Device` | Device type used |
| `Subscription Plan` | Active plan |
| `Date of Purchase` | Subscription start date |
| `Customer Reviews` | Free-text review (optional) |
| `Reason for Churn` | Why customer left (available for churned customers) |
| `Customer Churn Status` | Target variable — `Yes` / `No` |

**4. Run the notebook**
```bash
jupyter notebook mtn_churn_improved.ipynb
```

---

## 🤖 Model Details

| Property | Value |
|---|---|
| Algorithm | Random Forest Classifier |
| Class imbalance handling | `class_weight='balanced'` |
| Validation strategy | 5-fold Stratified Cross-Validation |
| Decision threshold | Optimised via Youden's J statistic |
| Primary metric | Recall (churners correctly identified) |
| Output | Churn probability score per customer + binary flag |

### Why Random Forest?
- Handles mixed data types (numeric + categorical) well
- Resistant to overfitting on tabular data
- Produces interpretable feature importance scores
- Strong baseline for churn prediction before more complex models are explored

---

## 📊 Key Outputs

### Churn Risk Tiers

| Tier | Probability | Recommended Action |
|---|---|---|
| 🔴 Critical | > 70% | Direct call within 24 hours |
| 🟡 At Risk | 40% – 70% | Targeted SMS / email offer this week |
| 🟢 Healthy | < 40% | Monitor monthly, no immediate action |

### Metrics Reported
- Accuracy, Precision, Recall, F1-Score
- ROC-AUC with optimal threshold marker
- Confusion matrix with business cost interpretation
- Permutation feature importance (top 15 features)
- Cross-validation scores with confidence intervals

### Business Impact Output
The notebook calculates:
- Revenue at risk from predicted churners
- Estimated revenue saved from successful interventions
- Total campaign cost
- Net benefit and ROI percentage

> Edit the financial assumptions in **Section 4** to match MTN's actual figures.

---

## 💡 Business Insights Summary

1. **Churn is segment-driven** — certain subscription plans, regions, and device types show disproportionately high churn rates, pointing to specific product or service issues.

2. **Tenure is a strong signal** — newer customers churn faster. Early onboarding and engagement programs are critical retention levers.

3. **Recall matters more than accuracy** — on imbalanced churn data, a model that looks 90% accurate can still miss most churners. This project prioritises catching churners (Recall) over raw accuracy.

4. **The model pays for itself** — even a 35% retention success rate on flagged customers generates significantly more revenue than the cost of outreach campaigns.

5. **Threshold is a business decision** — the notebook includes a sensitivity analysis showing how ROI changes at different decision thresholds, letting the business tune the trade-off between catching more churners vs. wasting intervention budget.

---

## 🚀 Roadmap

### Short-term
- [ ] Add NLP sentiment scoring on `Customer Reviews` column
- [ ] Benchmark XGBoost / LightGBM against Random Forest
- [ ] Hyperparameter tuning with `Optuna`

### Medium-term
- [ ] Weekly automated scoring pipeline
- [ ] CRM integration to push at-risk customers to retention queue
- [ ] A/B test: measure real-world impact of model-driven interventions

### Long-term
- [ ] Customer Lifetime Value (CLV) weighted scoring
- [ ] Churn *reason* prediction (multi-class)
- [ ] Geographic churn heat maps by region
- [ ] Monthly executive dashboard (automated PDF)

---

## 📄 License

This project is for internal business use. All customer data is subject to MTN's data privacy and compliance policies.

---

## 🙋 Author

**Soham Joshi**
Data Analyst / Data Scientist

---

*Built with the goal of turning customer data into proactive retention — not reactive reporting.*
