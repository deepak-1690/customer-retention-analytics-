Customer Retention Analytics: Strategic Report & Interactive Dashboard

Show Image Show Image Show Image

Final-week deliverable for a data analytics project. It turns analysis results into a strategic report, a presentation storyboard, and an interactive dashboard that non-technical stakeholders can explore.

Business question

Who is leaving, why, and where should limited retention budget be spent?

Headline results (synthetic sample data)
Metric	Value
Customers analysed	5,000
12-month churn rate	24.5%
Churn: Budget vs. Premium	34.6% vs. 15.3%
Churn with 3+ support tickets	44.4% (vs. 15.8% with none)
Model performance (AUC, held-out)	0.76
Active high-risk customers	454 (about $128.5K annual revenue)

The sample data is synthetic and exists so every figure is reproducible. Replace it with your own data (see below).

Repository structure
analytics-strategy-report/
├── README.md
├── requirements.txt
├── LICENSE
├── src/
│   ├── generate_data.py   # synthetic dataset (swap for your own)
│   ├── analysis.py        # segmentation, logistic regression, risk tiers
│   ├── dashboard.py       # interactive Plotly Dash dashboard
│   └── make_charts.py     # static PNG export for slides and reports
├── data/
│   ├── raw/               # customers.csv, monthly.csv
│   └── processed/         # model outputs and summary tables
├── docs/
│   └── Strategic_Report_and_Storyboard.docx
├── notebooks/             # optional exploratory work
└── assets/                # exported charts
The report

docs/Strategic_Report_and_Storyboard.docx contains:

Executive summary
Summary of the analytics process
Key findings
Strategic recommendations
Step-by-step approach to report generation
Visualisation and dashboard plan
12-slide presentation storyboard
Strategies for communicating with different audiences
Limitations and next steps
Quick start
bash
git clone https://github.com/<your-username>/analytics-strategy-report.git
cd analytics-strategy-report
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt

python src/generate_data.py      # or add your own data/raw/customers.csv
python src/analysis.py           # builds tables and risk scores
python src/dashboard.py          # open http://127.0.0.1:8050
python src/make_charts.py        # optional: static PNG charts
Dashboard features
Region and segment filters that update every chart and KPI
Click a segment bar to drill the priority list into that segment
Revenue trend with a range slider for zooming
Churn drivers shown as red (raises churn) and green (lowers churn) bars
Sortable priority outreach list of high-risk, still-active customers
Using your own data

Provide data/raw/customers.csv with these columns:

customer_id, region, segment, tenure_months, orders_12m, avg_order_value, support_tickets, discount_share, days_since_last_order, email_open_rate, churned, revenue_12m

and data/raw/monthly.csv with month, revenue_k, active_customers. If your columns differ, edit the feature list in src/analysis.py and the labels in src/dashboard.py. Then update the figures in the report using data/processed/summary.json.

Method in brief
Segmentation: churn rate by customer tier, region, support tickets and recency
Model: standardised logistic regression, 75/25 stratified split, chosen because its coefficients are easy to explain to non-technical audiences
Risk tiers: Low (below 0.2), Medium (0.2 to 0.4), High (above 0.4)
Limitations
Findings show associations, not proven causes; run a controlled pilot before scaling.
Retrain the model regularly and monitor drift.
Review outreach for fairness and follow your organisation's data policies.
