This project provides a complete analytics framework for identifying complaint trends, forecasting future volumes, and diagnosing root causes in consumer finance products across US states.
Leveraging cleaned CFPB complaint data, the system performs:

Multi-level data engineering

NLP-driven topic extraction

Advanced forecasting using SARIMA

Risk scoring of product–state combinations

Strategic insight dashboards for business decision-making


The solution is built to serve risk teams, compliance leaders, and operations units who require forward-looking intelligence on complaint behavior and emerging product–state risks.


---

 Project Architecture

Data Source (CFPB)  
       │
       ▼
Data Engineering Layer  
       │
       ├── Cleaning, Deduplication  
       ├── Monthly Aggregation  
       ├── Stable-Pair Derivation  
       └── NLP Topic Modeling  
       │
       ▼
Forecasting Layer  
       ├── SARIMA Modeling  
       ├── Forecast Evaluation (MAPE/MAE/MSE)  
       └── Risk Scoring  
       │
       ▼
Visualization & Insight Layer  
       ├── Python (matplotlib/seaborn)  
       ├── Tableau Dashboard  
       └── Executive PDF Reports  
       │
       ▼
Decision Intelligence  
       └── Identify rising-risk states, products & root causes


---

 Repository Structure

Customer_Complaint_Trend_Forecasting/
│
├── data/
│   ├── insights_data            # Final dataset used in Tableau & Python visuals
│   ├── stable_pairs.csv         # Final 111 stable product-state pairs
│   ├── matrics_all_pair         # forecasting matrics
│
├── notebook/
│   ├── 01_data_cleaning.ipynb
│   ├── 2.root_cause_analysis.ipynb
│   ├── 3_forecasting.ipynb
│   ├── 3_forecasting.ipynb
│
├── documents/
│   ├── Final_Project_Report
│   ├── insight_python_visuals
│   ├── Insights_visual_powerbi
│   └── ml_insights
│
├── dashboard/
│   └── Insights_dashboard.twb
│
└── README.md


---

 Raw Data Notice

The source CFPB dataset exceeds 1.6 GB, surpassing GitHub’s upload limits (100 MB per file).
Therefore, the raw data is not included in this repository.

Instead, this repo provides:

Clean, processed subsets

Aggregated versions

Stable-pair files

Visualization-ready datasets


The raw CFPB dataset can be accessed publicly at:
https://www.consumerfinance.gov/data-research/consumer-complaints/

A clarification note is included in /data/NOTE.txt.


---

 Technologies & Tools Used

Data Engineering & Processing

Python, Pandas, NumPy

PySpark (for handling very large files efficiently)

Google Colab (GPU/TPU compute & scalable storage)

Regex, string normalization, deduplication logic


NLP & Text Analytics

Scikit-learn

TF-IDF Vectorization

NMF Topic Modeling


Text preprocessing

Lemmatization

Stopword removal

Token cleaning



Forecasting & Modeling

SARIMA (statsmodels) → selected as final model

*Prophet (evaluated but rejected because of instability for short series)

Evaluation Metrics

MAPE, MAE, MSE



Visualization & Reporting

Tableau

Matplotlib & Seaborn

Executive PDF Reports


Versioning & Project Management

Git & GitHub

Repo structuring for enterprise analytics workflows



---

 Model Performance Summary

SARIMA was selected due to consistent performance across 111 stable product–state pairs.

Average forecasting performance:

MAPE: 1.46 → Excellent, highly reliable

MAE: 18.90

MSE: 7,846


Prophet was discarded because of unstable change-point behavior and consistently inferior performance across pairs.


---

 Key Insights Produced

1️ Top 10 Rising Risk (Product–State) Pairs

Identified using the formula:

risk_score = forecast_mean − historical_mean

These combinations show the strongest upward trend and represent early warning signals.


---

2️ Root Cause Analysis for Each Risky Pair

NLP modeling surfaces the highest-probability complaint drivers, enabling:

Focused investigation

Policy interventions

Prioritized customer remediation



---

3️ Historical vs Forecast Trend Visualization

Side-by-side view of:

Complaint seasonality

Trend reversals

Volatility

Forecast inflection points



---

4️ State-Level Heatmap of Complaint Volume

Highlights geographical clusters of high complaint activity.


---

5️ Stable vs Unstable Pair Segmentation

111 stable pairs were isolated using:

Time-series completeness

Monthly continuity checks

Null anomaly filtering


Only stable pairs were used for forecasting to ensure reliability.


---

 Tableau Dashboard (Executive-Ready)

The dashboard contains:

Actual vs Forecast Trend Viewer

Root Cause Distribution

State-Level Complaint Heatmap

Top Rising & Falling Product–State Pairs

Risk Scoring Matrix


This dashboard is included in:

/dashboard/Insights_dashboard.twb

---

 Conclusion

This analytics system provides a full end-to-end solution for understanding and forecasting consumer complaint behavior.
Through meticulous data engineering, NLP analysis, and SARIMA forecasting, it isolates high-risk product–state combinations with precision and explains why they are rising via topic interpretation.
The integrated Tableau dashboard transforms these outputs into clear, decision-ready insights for compliance, risk management, and regulatory teams.
The architecture is scalable, reproducible, and suitable for enterprise deployment or further integration with BI pipelines.
