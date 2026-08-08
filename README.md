# Lead Conversion Analytics — Sales Funnel Analysis for Education Sales

An end-to-end analytics project examining lead-to-enrollment conversion for a course-selling organization. The objective is to identify which acquisition channels, response behaviors, and follow-up patterns drive conversions, and to build a predictive scoring model that helps sales teams prioritize outreach.

**Live Dashboard:** [Add your deployed Streamlit link here]
**Author:** Krishna Kishore | www.linkedin.com/in/krishna-kishore-kkk | kishorekrishna943@gmail.com

---

## Business Problem

Sales teams generate a high volume of leads across multiple channels but have limited time to follow up with each one. Without a systematic way to prioritize outreach, high-potential leads can go cold while lower-value leads consume disproportionate attention.

This project addresses three questions:
1. Which lead sources deliver the highest conversion rate and revenue return?
2. How do response time and follow-up frequency influence the likelihood of conversion?
3. Can conversion likelihood be predicted in advance, to help sales representatives prioritize their pipeline?

---

## Dataset

A synthetic dataset of 8,000 leads was generated to simulate a realistic CRM export, incorporating lead source, course of interest, city tier, budget range, response time, follow-up count, and conversion outcome. Conversion probability was modeled using embedded business logic (for example, faster response times and moderate follow-up frequency increase conversion likelihood, while excessive follow-ups introduce lead fatigue) so that the dataset reflects patterns consistent with real-world sales behavior.

The data generation methodology is documented in `data/generate_dataset.py`.

---

## Key Findings

| Insight | Detail |
|---|---|
| **Top-performing channel** | Referrals convert at 30.2%, nearly double the rate of Instagram Ads (17.1%) |
| **Response speed matters** | Leads contacted within 2 hours convert at 29.4%, compared to 7.5% for leads contacted after 24 hours |
| **Follow-up fatigue point** | Conversion peaks around 3–5 follow-ups (26–27%) and declines sharply beyond 6 |
| **Strongest predictors** | Lead score and response time account for over 55% of the predictive model's decision-making |
| **Model performance** | Random Forest classifier achieves a ROC-AUC of 0.71 on held-out test data |

Full breakdown and supporting visuals are available in `visuals/` and the analysis notebooks.

---

## Repository Structure

```
lead-conversion-analytics/
├── data/
│   ├── leads_dataset.csv            # Synthetic CRM dataset (8,000 records)
│   └── generate_dataset.py          # Dataset generation script
├── notebooks/
│   ├── eda_analysis.py              # Exploratory analysis and model training (local/VS Code)
│   ├── SQL_Analysis_Colab.ipynb     # SQL analysis + visualizations, runnable in Google Colab
│   └── Colab_Dashboard.ipynb        # Interactive dashboard using ipywidgets (no server/tunnel needed)
├── sql/
│   └── queries.sql                  # Business questions answered in SQL
├── dashboard/
│   └── powerbi_guide.md             # Power BI build guide with DAX measures
├── app/
│   ├── streamlit_app.py             # Interactive Streamlit dashboard with live prediction
│   └── Streamlitapp.ipynb           # Colab notebook version, deployed via ngrok
├── visuals/                         # Exported charts
├── requirements.txt
└── README.md
```

---

## Methodology

**1. Exploratory Data Analysis (Python)**
Conversion rates were analyzed across lead source, response time buckets, follow-up count, and city/budget segments using Pandas and Seaborn. See `notebooks/eda_analysis.py`.

**2. Query-Based Analysis (SQL)**
The same business questions were independently answered using SQL to demonstrate query-based analytical fluency. See `sql/queries.sql`, and `notebooks/SQL_Analysis_Colab.ipynb` for the same queries run against an in-memory SQLite database with accompanying charts, reproducible entirely in Google Colab. Queries include channel-level conversion rates, response-time and follow-up analysis, a monthly trend, and a ranked "hot leads" list for sales prioritization.

**3. Predictive Modeling (Python / scikit-learn)**
A Random Forest classifier was trained to predict conversion probability using lead source, course, city tier, budget range, response time, follow-up count, and lead score as features. Class imbalance was addressed using balanced class weighting, and model performance was evaluated using precision, recall, and ROC-AUC.

**4. Business Intelligence Dashboard (Power BI)**
A three-page Power BI dashboard was designed to present findings to non-technical stakeholders, including an executive summary, a behavioral analysis view, and a filterable priority call-list for sales representatives. Build steps and DAX formulas are documented in `dashboard/powerbi_guide.md`.

**5. Interactive Web Application (Streamlit)**
A live dashboard was built using Streamlit, allowing users to filter by lead source and city tier, explore conversion patterns interactively, and input new lead attributes to receive a real-time conversion probability prediction. It includes defensive error handling (missing files, unexpected column names, empty filter states) so it fails gracefully with clear guidance rather than crashing. The app runs locally (`app/streamlit_app.py`) or from Google Colab via `app/Streamlitapp.ipynb`, tunneled through ngrok.

**6. Zero-Dependency Interactive Dashboard (ipywidgets)**
As an alternative to the Streamlit + tunnel setup, `notebooks/Colab_Dashboard.ipynb` renders an equivalent interactive dashboard — live filters, charts, and a lead-scoring tool — entirely inside Colab's own output cells using `ipywidgets`. This has no server, port, or tunnel dependency, trading a shareable public link for zero network-layer failure points.

---

## Tech Stack

**Languages & Libraries:** Python (Pandas, NumPy, scikit-learn, Matplotlib, Seaborn, ipywidgets), SQL
**Visualization & BI:** Power BI, Streamlit
**Environments:** Google Colab, VS Code (local)
**Version Control:** Git, GitHub

---

## Running This Project

### Option A: Locally in VS Code (recommended — no tunnels needed)

```bash
git clone https://github.com/your-username/lead-conversion-analytics.git
cd lead-conversion-analytics

python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\Activate.ps1

pip install -r requirements.txt

python notebooks/eda_analysis.py
streamlit run app/streamlit_app.py
```
Streamlit will be available directly at `http://localhost:8501` — no tunnel required, since the server and browser are on the same machine.

### Option B: Google Colab

- **SQL + visualizations:** upload `notebooks/SQL_Analysis_Colab.ipynb`, run all cells, upload `leads_dataset.csv` when prompted.
- **Zero-dependency dashboard:** upload `notebooks/Colab_Dashboard.ipynb`, run all cells — filters and the scoring tool render directly in the notebook output.
- **Streamlit dashboard:** upload `app/Streamlitapp.ipynb`, run all cells in order; it uses ngrok to expose a public link (requires a free ngrok account and authtoken).

---


## Limitations

This project uses a synthetically generated dataset designed to reflect realistic sales patterns, rather than live production data, due to data confidentiality. As such, findings are illustrative of methodology and analytical approach rather than actual business performance. The modeling techniques, query logic, and dashboard design are directly transferable to real CRM data with minimal modification.

---

## Contact

For questions about this project or my background in analytics, feel free to connect via www.linkedin.com/in/krishna-kishore-kkk or kishorekrishna943@gmail.com
