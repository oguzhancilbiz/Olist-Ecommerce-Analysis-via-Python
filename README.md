# 📊 Olist E-Commerce: Independent Market Analysis & Statistical Hypothesis Testing

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/19lvdNpYpPzosgSalKS1LvtG3gltiP2tO)

## 🎯 Project Overview
This project delivers a comprehensive, data-driven evaluation of the **Olist Brazilian E-Commerce Open Dataset (2016–2018)**. Simulating a real-world scenario as an independent Data Scientist reporting directly to executive stakeholders, the objective was to transform raw, disconnected relational tables into high-impact business insights using exploratory data analysis (EDA), advanced interactive visualizations, and rigorous **statistical hypothesis testing (A/B Testing, ANOVA, Chi-Square)**.

---
## 💾 Dataset Access & Local Setup
Due to GitHub file size limitations, the raw relational datasets are not hosted directly in this repository. To replicate or run this notebook locally:
1. Download the official archive from Kaggle: [Olist Brazilian E-Commerce Dataset](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)
2. Extract the ZIP file and place all CSV files into a local folder named `data/` within your root directory.

    olist-ecommerce-analytics/
    ├── data/                       # Raw CSV datasets (Git ignored)
    ├── notebooks/                  # Jupyter Notebook (.ipynb)
    └── README.md                   # Project documentation


## 🛠️ Tech Stack & Python Ecosystem
- **Data Engine:** Pandas, NumPy (Relational mapping via unique IDs, automated type casting, custom handling of data gaps, and data deduplication).
- **Statistical Analytics:** Scipy.stats (Parametric and non-parametric hypothesis testing).
- **Interactive Visualizations:** Plotly Express & Plotly Graph Objects (Production-ready, interactive analytical plotting).

---

## 🔍 Data Pipeline & Data Preprocessing
An automated pipeline was developed to tackle raw e-commerce data challenges:
- **Automated Datetime Transformer:** Dynamically scanned all tables to cast implicit strings into proper `datetime` structures.
- **Custom Missing-Value Strategy:** Handled categorical nulls intelligently (e.g., categorizing missing products as `'diger'` and missing review messages as `'mesaj_yok'`) to prevent algorithmic bias while maintaining data integrity.
- **Duplicate Sweeper:** Cleansed repetitive entries across all entities to ensure lean operations.

---

## 🧪 Statistical Testing & Deep Insights (A/B Testing Framework)

### 1. Delivery Latency vs. Customer Satisfaction (Independent T-Test)
- **Hypothesis:** Testing whether a delivery threshold of 7 days statistically influences customer review scores.
- **Methodology:** Split data into a Control Group (Fast Delivery $\le$ 7 days) and a Test Group (Slow Delivery > 7 days) using `stats.ttest_ind` (Welch's T-Test for unequal variances).
- **Result:** **$p < 0.05$ (H0 Rejected).** Delivery speed directly dictates customer retention and happiness; fast deliveries yielded statistically higher satisfaction rates.

### 2. Product Category vs. Order Value / AOV (ANOVA Test)
- **Hypothesis:** Assessing if different top-performing product categories show significant variations in Average Order Value (AOV).
- **Methodology:** Grouped the top 5 most frequent product categories and applied a One-Way ANOVA test (`stats.f_oneway`).
- **Result:** **$p < 0.05$ (H0 Rejected).** Cart value shifts drastically based on category domain (Electronics/Luxury vs. Daily Consumables), proving that marketing spend should be strategically allocated based on domain revenue margins rather than just order volume.

### 3. Payment Method vs. Order Completion Rate (Chi-Square Contingency Test)
- **Hypothesis:** Evaluating if cash-based payment methods (Boleto) experience significantly higher drop-out/cancellation rates compared to credit card transactions.
- **Methodology:** Created a cross-tabulation of payment methods against delivery status (`order_status`) and applied `stats.chi2_contingency`.
- **Result:** **$p < 0.05$ (H0 Rejected).** Payment infrastructure deeply impacts completion pipelines. Boleto represents a severe bottleneck with statistically higher cancellation risks.

---

## 📈 Executive Key Takeaways & Recommendations
- **Operational Priority:** Logistics must be optimized to push delivery times below the 7-day critical threshold to secure higher retention scores.
- **Risk Mitigation:** Financial/checkout workflows should mitigate the "Boleto Risk" by offering credit card incentives, minimizing unfulfilled inventory locks.
- **Strategic Categorization:** Higher-AOV categories identified by ANOVA should receive tailored upselling and cross-selling campaigns to optimize revenue generation.

---

## ⚠️ Limitations & Future Roadmap
- **Geographical Constraints:** The dataset reflects Brazilian logistics (with latency outliers spanning up to 100+ days) and cannot be directly generalized to tighter logistical markets like Europe or Turkey.
- **Next Steps (Predictive Modeling):** Transitioning this descriptive analysis into a **Machine Learning Classification Pipeline** to predict customer review scores at the exact moment of checkout.
- **Next Steps (NLP):** Engineering a **Text Mining Pipeline** via Natural Language Processing (NLP) on `review_comment_message` to extract automated sentiment tags.
