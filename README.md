# Lead Conversion Analytics Dashboard 🚀

[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

An end-to-end lead conversion analytics project designed for a sales team to understand performance, optimize the sales funnel, and predict conversion probabilities. This repository features a synthetic dataset, a fully interactive dashboard, and a machine-learning model—all packaged in multiple deployment options.

## Project Overview

This project simulates a CRM dataset for an Ed-Tech or training institute. It provides a complete toolkit for sales managers and data analysts to:

1.  **Analyze Conversion Drivers:** Identify which lead sources, response times, and follow-up frequencies yield the highest conversion rates.
2.  **Visualize Key Metrics:** Explore conversion rates, revenue, and sales cycle patterns through an interactive dashboard.
3.  **Predict Lead Scoring:** Use a trained Random Forest model to score new leads and prioritize high-potential prospects.

The core insight is that conversion is not random. It's driven by realistic business rules (fast response time, optimal follow-ups, high intent signals) enabling meaningful EDA and a high-performing machine learning model.

## Key Features

*   **📊 Interactive Dashboard:**
    *   **Filterable Views:** Filter the dashboard by lead source and city tier using an intuitive interface.
    *   **Dynamic KPIs:** View real-time metrics like total leads, conversion rate, total revenue, and average days to convert based on your filters.
    *   **Core Analytics:** Visualizes conversion rates by lead source, response time, and number of follow-ups.
*   **🤖 Predictive Lead Scoring:**
    *   A **Random Forest Classifier** is trained to predict a lead's conversion probability.
    *   **Feature Importance:** Understand what factors (e.g., lead score, budget range) are most influential in predicting conversion.
    *   **Live Scoring Tool:** Enter a new lead's details to get an instant conversion probability prediction and a recommendation on follow-up priority.
*   **🐍 Multiple Deployment Methods:**
    *   **Google Colab Dashboard:** Run the dashboard natively within a Colab notebook using `ipywidgets` for instant interaction.
    *   **Streamlit App:** A public-facing web app with a polished UI, deployable on various platforms. The repository includes a notebook to launch it via `ngrok` from Colab.
    *   **SQL Analysis:** A SQL notebook to run ad-hoc queries for deeper analysis.
*   **🧪 Synthetic Dataset:**
    *   A realistic, generated dataset (`leads_dataset.csv`) of **8,000 leads**.
    *   The data creation script (`generate_dataset.py`) ensures meaningful patterns for educational and demonstration purposes.

## How It Works

### The Data Generation Logic (`generate_dataset.py`)
The synthetic dataset is designed to mimic real-world business rules, ensuring the analytics and model provide meaningful insights. Key factors influencing conversion include:

*   **Response Time:** Faster responses (<2 hrs) significantly boost conversion.
*   **Follow-ups:** A sweet spot of 3-5 follow-ups yields the best conversion; more than 7 follow-ups shows "lead fatigue".
*   **Lead Source:** Referrals and organic traffic usually convert better than paid ads.
*   **Budget & City Tier:** Higher budgets and Tier-1 cities indicate higher intent and purchasing power.

### The Dashboard & Model
1.  **Exploratory Data Analysis (EDA):** The code explores key business questions—which sources convert best, the impact of response time, and the optimal number of follow-ups.
2.  **Predictive Model:** A **Random Forest** model is trained using features like lead source, budget range, response time, and lead score. The model's feature importance highlights what the sales team should focus on.
3.  **Interactive Dashboard:** The Colab and Streamlit versions provide a user-friendly way to explore the same data and model insights without writing code.

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/lead-conversion-analytics.git
cd lead-conversion-analytics
```

### 2. Environment Setup

Create a virtual environment (recommended) and install the dependencies.

**Linux/macOS:**
```bash
python3 -m venv venv
source venv/bin/activate
```

**Windows (Command Prompt):**
```cmd
python -m venv venv
venv\Scripts\activate
```

**Install Dependencies:**
```bash
pip install -r requirements.txt
```

### 3. Explore the Data & Run the Analysis

You can start with the Colab notebooks, which are self-contained.

1.  **Generate the dataset (optional):**
    ```bash
    python generate_dataset.py
    ```
    This will create a new `leads_dataset.csv` file.

2.  **Run the Colab Dashboard:**
    *   Open `Colab_Dashboard.ipynb` in Google Colab.
    *   Run all cells.
    *   Upload `leads_dataset.csv` when prompted.
    *   Interact with the live dashboard widgets.

3.  **Launch the Streamlit App (Locally or via Colab):**
    *   The simplest way to run the Streamlit app is to execute the `Streamlitapp (2).ipynb` notebook in Colab from start to finish. It will handle installation, authentication, and provide a public `ngrok` URL.
    *   To run the app locally:
        ```bash
        streamlit run app.py
        ```

## Repository Structure

```
├── README.md
├── requirements.txt          # Project dependencies
├── generate_dataset.py       # Script to generate the synthetic dataset
├── database.py               # SQLite-based analysis and query examples
├── leads_dataset.csv         # Synthetic dataset
├── Colab_Dashboard.ipynb     # Colab notebook with a native ipywidgets dashboard
├── Streamlitapp (2).ipynb    # Colab notebook to deploy the Streamlit app via ngrok
└── app.py                    # The core Streamlit application file
```

## Technology Stack

*   **Data Analysis:** `pandas`, `numpy`
*   **Database & SQL:** `sqlite3`
*   **Visualization:** `matplotlib`, `seaborn`, `streamlit`
*   **Machine Learning:** `scikit-learn` (Random Forest Classifier)
*   **Interactivity & UI:** `ipywidgets`, `streamlit`
*   **Deployment:** `ngrok`, `pyngrok`

## Key Insights

*   **Referral leads have the highest conversion rate**, which is a strong signal to invest in referral programs.
*   **Responding within 2 hours** dramatically improves conversion, highlighting the importance of a fast sales team.
*   **Leads with 3-5 follow-ups** have the highest conversion probability.
*   The predictive model shows that **Lead Score, Budget Range, and Response Time** are the most important features for predicting conversion.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request or open an Issue to discuss improvements or new features.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

**Built with ❤️ for the data community.**
