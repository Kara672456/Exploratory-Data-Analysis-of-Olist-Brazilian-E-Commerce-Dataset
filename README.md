<div align="center">

# 🛒 Inside Olist
## A Data-Driven Exploration of Brazilian E-Commerce (2016–2018)

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![Pandas](https://img.shields.io/badge/Pandas-1.5+-150458?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org)
[![Seaborn](https://img.shields.io/badge/Seaborn-0.12+-4C72B0?style=for-the-badge&logo=python&logoColor=white)](https://seaborn.pydata.org)
[![Scipy](https://img.shields.io/badge/Scipy-1.9+-8CAAE6?style=for-the-badge&logo=scipy&logoColor=white)](https://scipy.org)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)](https://jupyter.org)

<br/>

> **Exploratory Data Analysis (EDA)** of the Olist Brazilian E-Commerce Dataset  
> Uncovering customer behaviour, operational patterns and business insights  
> through statistical analysis, data visualisation and hypothesis testing.

<br/>

---

### 📊 115,600 Orders &nbsp;|&nbsp; 37 Columns &nbsp;|&nbsp; 27 States &nbsp;|&nbsp; 2016 – 2018

---

</div>

<br/>

## 📋 Table of Contents

| # | Section |
|---|---------|
| 1 | [Project Overview](#-project-overview) |
| 2 | [Dataset Description](#-dataset-description) |
| 3 | [Project Structure](#-project-structure) |
| 4 | [Technologies Used](#-technologies-used) |
| 5 | [Installation & Setup](#-installation--setup) |
| 6 | [Analysis Workflow](#-analysis-workflow) |
| 7 | [Key Findings](#-key-findings) |
| 8 | [Hypothesis Testing](#-hypothesis-testing-results) |
| 9 | [Visualisations](#-visualisations) |
| 10 | [Business Recommendations](#-business-recommendations) |
| 11 | [Deliverables](#-deliverables) |
| 12 | [Acknowledgements](#-acknowledgements) |

<br/>

---

## 🔍 Project Overview

This project performs a comprehensive **Exploratory Data Analysis** on the Olist Brazilian E-Commerce Dataset, covering **115,600 orders** placed between **October 2016 and August 2018** across all 27 Brazilian states.

<br/>

### 🗺️ Analysis Phases

```
╔══════════════════════════════════════════════════════════════════╗
║                     ANALYSIS PIPELINE                           ║
╠══════════════════════════════════════════════════════════════════╣
║                                                                  ║
║  📦 Phase 1        📊 Phase 2        🔗 Phase 3       🧪 Phase 4 ║
║  ─────────         ─────────         ─────────        ─────────  ║
║  Univariate   →   Bivariate    →   Multivariate  →  Hypothesis  ║
║  Analysis         Analysis         Analysis          Testing     ║
║                                                                  ║
║  Distributions    Correlations      Heatmaps         Mann-       ║
║  Outliers         Scatter plots     Grouped bars     Whitney U   ║
║  Skewness         Box plots         Pivot tables     Pearson r   ║
║  Frequencies      Category vs       Category ×       Kruskal-    ║
║  Time patterns    Numerical         Month × Value    Wallis      ║
╚══════════════════════════════════════════════════════════════════╝
```

<br/>

### 🎯 Objectives

- 🔢 Understand distribution and characteristics of all numerical, categorical and datetime variables
- 📈 Identify seasonal trends, geographic patterns and ordering behaviour
- 💬 Perform sentiment analysis on **48,613 Portuguese-language** customer reviews
- ✅ Validate statistical hypotheses derived from observed data patterns
- 💡 Derive actionable business recommendations from the findings

<br/>

---

## 📦 Dataset Description

> **Source:** [Kaggle — Brazilian E-Commerce Public Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)

<br/>

### 📐 Dataset at a Glance

| Attribute | Detail |
|-----------|--------|
| 📊 **Total Rows** | 115,600 |
| 📋 **Total Columns** | 37 |
| 📅 **Date Range** | October 2016 – August 2018 |
| 🗺️ **Geographic Coverage** | Brazil (27 states) |
| 🗂️ **Source Tables** | 8 individual Olist CSV files |
| 🌐 **Language** | Portuguese (reviews) · English (categories) |

<br/>

### 🗂️ Source Tables

| Table | Records | Description |
|-------|---------|-------------|
| `olist_orders_dataset.csv` | ~99K | Core order info and status |
| `olist_customers_dataset.csv` | ~99K | Customer location and ID |
| `olist_order_items_dataset.csv` | ~112K | Products, sellers and pricing |
| `olist_products_dataset.csv` | ~33K | Dimensions, weight and category |
| `olist_product_category_name_translation.csv` | 71 | Category names in English |
| `olist_order_payments_dataset.csv` | ~104K | Payment type, value and instalments |
| `olist_order_reviews_dataset.csv` | ~99K | Review scores and comment text |
| `olist_sellers_dataset.csv` | ~3K | Seller location data |

<br/>

### 📊 Column Types Breakdown

```
┌─────────────────────────────────────────────────────────────────┐
│                    37 COLUMNS OVERVIEW                          │
├──────────────┬──────────┬────────────────────────────────────── │
│     TYPE     │  COUNT   │  KEY COLUMNS                          │
├──────────────┼──────────┼────────────────────────────────────── │
│ 🔢 Numerical │    7     │  price · freight_value · payment_value │
│              │          │  product_weight_g · review_score       │
├──────────────┼──────────┼────────────────────────────────────── │
│ 🏷️ Categoric │    5     │  order_status · payment_type          │
│              │          │  product_category · customer_state    │
├──────────────┼──────────┼────────────────────────────────────── │
│ 📅 Datetime  │    6     │  order_purchase_timestamp             │
│              │          │  order_delivered_customer_date        │
├──────────────┼──────────┼────────────────────────────────────── │
│ 💬 Text/NLP  │    2     │  review_comment_message               │
│              │          │  review_comment_title                 │
└──────────────┴──────────┴────────────────────────────────────── │
```

<br/>

---

## 🗂️ Project Structure

```
📁 olist-eda/
│
├── 📓 notebooks/
│   └── olist_eda.ipynb                   # Main analysis notebook
│
├── 📊 data/
│   ├── raw/                              # Original Olist CSV files
│   │   ├── olist_orders_dataset.csv
│   │   ├── olist_customers_dataset.csv
│   │   ├── olist_order_items_dataset.csv
│   │   ├── olist_products_dataset.csv
│   │   ├── olist_product_category_name_translation.csv
│   │   ├── olist_order_payments_dataset.csv
│   │   ├── olist_order_reviews_dataset.csv
│   │   └── olist_sellers_dataset.csv
│   └── processed/
│       └── master.csv                    # Merged master dataframe
│
├── 📈 outputs/
│   ├── plots/                            # All generated visualisation PNGs
│   ├── Olist_EDA_Report_Final.pdf        # Detailed written report (22 pages)
│   ├── Olist_EDA_BlueWhite.pptx          # Project presentation (17 slides)
│   └── README.md                         # This file
│
└── 📄 requirements.txt                   # Python dependencies
```

<br/>

---

## 🛠️ Technologies Used

<div align="center">

| Tool | Badge | Purpose |
|------|-------|---------|
| **Python 3.10+** | ![Python](https://img.shields.io/badge/-Python-3776AB?logo=python&logoColor=white) | Core programming language |
| **Pandas** | ![Pandas](https://img.shields.io/badge/-Pandas-150458?logo=pandas&logoColor=white) | Data manipulation and aggregation |
| **NumPy** | ![NumPy](https://img.shields.io/badge/-NumPy-013243?logo=numpy&logoColor=white) | Numerical ops and log transformation |
| **Matplotlib** | ![Matplotlib](https://img.shields.io/badge/-Matplotlib-11557C?logo=python&logoColor=white) | Base plotting library |
| **Seaborn** | ![Seaborn](https://img.shields.io/badge/-Seaborn-4C72B0?logo=python&logoColor=white) | Statistical visualisation |
| **Scipy** | ![Scipy](https://img.shields.io/badge/-Scipy-8CAAE6?logo=scipy&logoColor=white) | Statistical hypothesis tests |
| **pysentimiento** | ![NLP](https://img.shields.io/badge/-pysentimiento-FF6F00?logo=python&logoColor=white) | Portuguese sentiment analysis |
| **Jupyter** | ![Jupyter](https://img.shields.io/badge/-Jupyter-F37626?logo=jupyter&logoColor=white) | Interactive analysis environment |

</div>

<br/>

---

## ⚙️ Installation & Setup

### Step 1 — Clone the Repository
```bash
git clone https://github.com/yourusername/olist-eda.git
cd olist-eda
```

### Step 2 — Create a Virtual Environment
```bash
# Mac / Linux
python -m venv venv
source venv/bin/activate

# Windows
python -m venv venv
venv\Scripts\activate
```

### Step 3 — Install Dependencies
```bash
pip install -r requirements.txt
```

### Step 4 — Download the Dataset
Download all 8 CSV files from [Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) and place them inside `data/raw/`

### Step 5 — Run the Notebook
```bash
jupyter notebook notebooks/olist_eda.ipynb
```

<br/>

### 📄 requirements.txt
```text
pandas>=1.5.0
numpy>=1.23.0
matplotlib>=3.6.0
seaborn>=0.12.0
scipy>=1.9.0
pysentimiento>=0.6.0
jupyter>=1.0.0
```

<br/>

---

## 📊 Analysis Workflow

### 🔗 Step 1 — Data Loading & Merging
```python
import pandas as pd

orders    = pd.read_csv("data/raw/olist_orders_dataset.csv")
customers = pd.read_csv("data/raw/olist_customers_dataset.csv")
items     = pd.read_csv("data/raw/olist_order_items_dataset.csv")
products  = pd.read_csv("data/raw/olist_products_dataset.csv")
translate = pd.read_csv("data/raw/olist_product_category_name_translation.csv")
payments  = pd.read_csv("data/raw/olist_order_payments_dataset.csv")
reviews   = pd.read_csv("data/raw/olist_order_reviews_dataset.csv")

# Merge all tables into single master dataframe
master = (orders
          .merge(customers, on="customer_id")
          .merge(items,     on="order_id")
          .merge(products,  on="product_id")
          .merge(translate, on="product_category_name")
          .merge(payments,  on="order_id")
          .merge(reviews,   on="order_id"))

print(f"Master shape: {master.shape}")   # (115600, 37)
```

### 🧹 Step 2 — Data Cleaning
```python
# Convert datetime columns
datetime_cols = [
    "order_purchase_timestamp",
    "order_approved_at",
    "order_delivered_carrier_date",
    "order_delivered_customer_date",
    "order_estimated_delivery_date",
    "review_creation_date"
]
for col in datetime_cols:
    master[col] = pd.to_datetime(master[col])

# Remove 2016 partial year (only 381 orders = 0.33%)
master = master[master["order_purchase_timestamp"].dt.year != 2016]
print(f"Rows after removing 2016: {len(master)}")   # 115,219
```

### 📉 Step 3 — Outlier Treatment
```python
import numpy as np

cols = ["price", "freight_value", "payment_value"]

for col in cols:
    # Cap at 95th percentile (Winsorization)
    cap_value = master[col].quantile(0.95)
    master[col + "_capped"] = master[col].clip(upper=cap_value)

    # Log transformation using log1p (handles zero values safely)
    master[col + "_log"] = np.log1p(master[col + "_capped"])

    before = master[col].skew()
    after  = master[col + "_log"].skew()
    print(f"{col:<20} Skew before: {before:.2f}  →  After: {after:.2f}")
```

### 📊 Step 4 — Univariate Plots
```python
import matplotlib.pyplot as plt
import seaborn as sns

log_cols = ["price_log", "freight_value_log", "payment_value_log"]
colors   = ["steelblue", "lightcoral", "mediumseagreen"]

fig, axes = plt.subplots(3, 3, figsize=(18, 15))

for i, (col, color) in enumerate(zip(log_cols, colors)):
    # Histogram
    sns.histplot(master[col].dropna(), bins=50, ax=axes[i][0], color=color)
    axes[i][0].set_title(f"Histogram of {col}")

    # Box Plot
    sns.boxplot(y=master[col].dropna(), ax=axes[i][1], color=color)
    axes[i][1].set_title(f"Boxplot of {col}")

    # KDE Plot
    sns.kdeplot(master[col].dropna(), ax=axes[i][2], color=color, fill=True)
    axes[i][2].axvline(master[col].mean(),   color="red",   linestyle="--", label="Mean")
    axes[i][2].axvline(master[col].median(), color="black", linestyle="--", label="Median")
    axes[i][2].set_title(f"KDE of {col}")
    axes[i][2].legend()

plt.suptitle("Univariate Analysis — After Log Transformation", fontsize=15, fontweight="bold")
plt.tight_layout()
plt.show()
```

### 💬 Step 5 — Sentiment Analysis
```python
from pysentimiento import create_analyzer

# Load Portuguese sentiment model
analyzer = create_analyzer(task="sentiment", lang="pt")

# Sample 5000 reviews (full 48,613 would take ~30 min)
reviews_df = (master[master["review_comment_message"].notna()]
              .sample(5000, random_state=42)
              .copy())

def get_sentiment(text):
    try:
        return analyzer.predict(text).output   # POS / NEU / NEG
    except:
        return "NEU"

reviews_df["sentiment"] = reviews_df["review_comment_message"].apply(get_sentiment)
print(reviews_df["sentiment"].value_counts())
# POS    2212  (44.2%)
# NEU    1783  (35.7%)
# NEG    1005  (20.1%)
```

### 🧪 Step 6 — Hypothesis Testing
```python
from scipy import stats
import numpy as np

# ── H3: Delivery Delay vs Review Score ────────────────────────
master["delivery_status"] = np.where(
    master["order_delivered_customer_date"] <= master["order_estimated_delivery_date"],
    "On Time", "Delayed"
)

on_time = master[master["delivery_status"] == "On Time"]["review_score"]
delayed = master[master["delivery_status"] == "Delayed"]["review_score"]

u_stat, p_value = stats.mannwhitneyu(on_time, delayed, alternative="greater")

print(f"On-time avg score : {on_time.mean():.2f}")   # 4.50
print(f"Delayed avg score : {delayed.mean():.2f}")   # 2.00
print(f"p-value           : {p_value:.6f}")          # 0.000000
```

<br/>

---

## 🔑 Key Findings

```
╔══════════════════════════════════════════════════════════════════════════╗
║                        TOP 8 KEY FINDINGS                               ║
╠════╦═════════════════════════════════════════════╦════════════════════════╣
║ 01 ║ 98% delivery success rate                   ║ 113,201 / 115,600 ✅  ║
╠════╬═════════════════════════════════════════════╬════════════════════════╣
║ 02 ║ Credit card dominates at 73%                ║ 85,270 orders          ║
╠════╬═════════════════════════════════════════════╬════════════════════════╣
║ 03 ║ Delivery delay = −2.5 star rating ⚠️        ║ 4.5★ vs 2.0★          ║
╠════╬═════════════════════════════════════════════╬════════════════════════╣
║ 04 ║ North Brazil 3.4× slower delivery           ║ RR: 28.3d vs SP: 8.2d ║
╠════╬═════════════════════════════════════════════╬════════════════════════╣
║ 05 ║ Sep–Oct revenue drops 60% from peak         ║ 5,018 vs 12,479 orders ║
╠════╬═════════════════════════════════════════════╬════════════════════════╣
║ 06 ║ Weight drives freight more than price       ║ r=0.61 vs r=0.41      ║
╠════╬═════════════════════════════════════════════╬════════════════════════╣
║ 07 ║ Security services worst rated (2.50★) ❌    ║ 2.14pt gap to best    ║
╠════╬═════════════════════════════════════════════╬════════════════════════╣
║ 08 ║ Higher EMI = higher spend (r=0.27)          ║ R$247 vs R$143 avg    ║
╚════╩═════════════════════════════════════════════╩════════════════════════╝
```

<br/>

---

## 🧪 Hypothesis Testing Results

### ✅ H3 — Delivery Delay vs Review Score

```
┌─────────────────────────────────────────────────────────┐
│  HYPOTHESIS 3 RESULT                                    │
│                                                         │
│  Test Used  :  Mann-Whitney U Test                      │
│  p-value    :  0.000000  (< 0.0001)                    │
│  Result     :  ✅ REJECT H₀                            │
│                                                         │
│  On-time avg review   →   4.5 ★                        │
│  Delayed avg review   →   2.0 ★                        │
│  Difference           →   2.5 points                   │
│                                                         │
│  ⚡ Delivery timeliness is the #1 satisfaction driver  │
└─────────────────────────────────────────────────────────┘
```

### ✅ H6 — Instalments vs Payment Value

```
┌─────────────────────────────────────────────────────────┐
│  HYPOTHESIS 6 RESULT                                    │
│                                                         │
│  Tests Used :  Mann-Whitney U + Pearson Correlation     │
│  p-value    :  0.000000  (< 0.0001)                    │
│  r value    :  0.27 (weak positive)                    │
│  Result     :  ✅ REJECT H₀                            │
│                                                         │
│  High instalment avg  →   R$247                        │
│  Low instalment avg   →   R$143                        │
│  Difference           →   R$104 (73% higher)           │
│                                                         │
│  ⚡ EMI promotions can meaningfully lift order value   │
└─────────────────────────────────────────────────────────┘
```

### ✅ H+ — Delivery Time Across States

```
┌─────────────────────────────────────────────────────────┐
│  FURTHER EXPLORATION RESULT                             │
│                                                         │
│  Tests Used :  Kruskal-Wallis + Pearson Correlation     │
│  KW p-value :  0.000000  (< 0.0001)                   │
│  r value    :  −0.30 (delivery days vs review score)   │
│  Result     :  ✅ REJECT H₀                            │
│                                                         │
│  Slowest: RR (Roraima)   →   28.3 days avg             │
│  Fastest: SP (Sao Paulo) →    8.2 days avg             │
│  Gap                     →   20 days (3.4× slower)     │
│                                                         │
│  ⚡ Geography is a key hidden driver of satisfaction   │
└─────────────────────────────────────────────────────────┘
```

<br/>

---

## 📈 Visualisations

| Chart Type | Purpose | Columns Used |
|------------|---------|--------------|
| 📊 **Histogram + KDE** | Distribution shape before/after transformation | `price`, `freight_value`, `payment_value` |
| 📦 **Box Plot** | Outlier detection and spread | All numerical columns |
| 📊 **Vertical Bar** | Monthly and yearly order counts | `order_purchase_timestamp` |
| 📊 **Horizontal Bar** | Category, city and state rankings | `product_category`, `customer_city` |
| 🍩 **Donut Chart** | Payment type split, sentiment distribution | `payment_type`, `sentiment` |
| 🔵 **Scatter + Regression** | Correlation with r value | `price` vs `freight_value`, `weight` vs `freight` |
| 📈 **Line Chart** | Orders by hour, revenue trends | `order_hour`, `payment_value` |
| 📊 **Grouped Bar** | Revenue by year and payment type | `order_year`, `payment_type`, `payment_value` |
| 🟥 **Heatmap (Pivot)** | Month × category × total revenue | `order_month`, `product_category`, `payment_value` |

<br/>

---

## 💼 Business Recommendations

### 🔴 Priority 1 — Critical

| # | Recommendation | Expected Impact |
|---|---------------|-----------------|
| R1 | Proactive delivery delay alerts + compensation vouchers | Recover 2.5★ review score gap |
| R2 | Expand logistics in North Brazil (RR, AP, AM states) | Reduce 20-day delivery gap |

### 🟡 Priority 2 — Revenue Growth

| # | Recommendation | Expected Impact |
|---|---------------|-----------------|
| R3 | Launch Sep–Oct promotional campaigns 3 months in advance | Address 60% seasonal revenue drop |
| R4 | Push EMI offers on computers and appliances | Lift AOV from R$143 to R$247 |

### 🟢 Priority 3 — Quality

| # | Recommendation | Expected Impact |
|---|---------------|-----------------|
| R5 | Audit and fix security_and_services category (2.50★) | Improve lowest-rated category |
| R6 | Mandate accurate product weight data entry | Fix freight estimation errors |

<br/>

---

## 📄 Deliverables

| File | Type | Description |
|------|------|-------------|
| `notebooks/olist_eda.ipynb` | 📓 Notebook | Complete analysis with code and outputs |
| `Olist_EDA_Report_Final.pdf` | 📄 Report | Detailed 10-section written report (22 pages) |
| `Olist_EDA_BlueWhite.pptx` | 📊 Slides | 17-slide project presentation |
| `README.md` | 📝 Docs | This project documentation |

<br/>

---

## 🙏 Acknowledgements

- 🏪 **Dataset** — [Olist](https://olist.com/) Brazilian E-Commerce Platform
- 📊 **Kaggle Source** — [Brazilian E-Commerce Public Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)
- 🤖 **Sentiment Model** — [pysentimiento](https://github.com/pysentimiento/pysentimiento) — Portuguese NLP Library

<br/>

---

<div align="center">

### ⭐ If you found this project useful, please give it a star!

*This project was completed as part of an Exploratory Data Analysis course.*  
*All analysis, observations and recommendations represent independent work.*

</div>
