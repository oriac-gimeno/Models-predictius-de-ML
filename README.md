# Machine Learning Predictive Models (Olist E‑commerce Project)

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange)](https://jupyter.org/)
[![XGBoost](https://img.shields.io/badge/XGBoost-Latest-green)](https://xgboost.readthedocs.io/)
[![Prophet](https://img.shields.io/badge/Prophet-Facebook-brightgreen)](https://facebook.github.io/prophet/)
[![License](https://img.shields.io/badge/license-MIT-lightgrey)](LICENSE)

This repository contains the complete end‑to‑end **Data Science and Machine Learning project** developed as the final deliverable for the **IT Academy Data Analytics Reskilling program**. The project explores the Brazilian e‑commerce public dataset from Olist, with the main goal of **predicting product demand by category** using three different modelling approaches.

---

## 📌 Table of Contents

- [Context & Objectives](#context--objectives)
- [Dataset](#dataset)
- [Methodology – Data Pipeline](#methodology--data-pipeline)
- [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
- [Predictive Modelling](#predictive-modelling)
- [Results](#results)
- [Technologies Used](#technologies-used)
- [Project Structure](#project-structure)
- [How to Reproduce](#how-to-reproduce)
- [Conclusions & Future Work](#conclusions--future-work)
- [Contact](#contact)

---

## 🎯 Context & Objectives

The Brazilian e‑commerce market is experiencing exponential growth. To design high‑impact sales strategies, it is essential to understand **what, when, who, and how** customers buy, together with their satisfaction drivers.

**Main objectives:**
- Detect **purchase patterns** (temporal trends, consumption habits, customer behaviour).
- Identify **seasonality and influential events** (holidays, school breaks, commercial events like Black Friday).
- **Forecast demand by product category** to support commercial decisions and inventory optimisation.

---

## 📊 Dataset

**Source:** [Brazilian E‑Commerce Public Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) (Kaggle).

**Key characteristics:**
- **113,425 orders** from September 2016 to October 2018.
- **32,951 unique products** across **52 product categories** (after reduction from 71).
- **8 related tables** containing information on customers, products, payments, reviews, geolocation, etc.
- **48 variables** including price, dates, customer location, product attributes, and review scores.

---

## ⚙️ Methodology – Data Pipeline

### 1. Preprocessing & Cleaning
- **14 date columns** converted to `datetime` format.
- **Missing values** in product attributes imputed with the mode of the corresponding category.
- **Date‑related nulls** filled using existing data.
- **Category reduction:** kept only categories with more than 100 orders (from 71 to 52). For deeper analysis, the **top 15 categories** (accounting for **76.4% of total revenue**) were selected.

### 2. Feature Engineering
- **Temporal features:** extracted month, day, week, and hour from original dates.
- **Event enrichment:** added Brazilian holidays (Carnival, Mother’s Day, etc.), school breaks (summer, Christmas), and commercial events (Black Friday, Cyber Monday).

### 3. Normalisation & Optimisation
- **Price normalisation:** prices scaled to be comparable within each category.
- **DataFrame compression:** saved as **Parquet** format, reducing memory usage by **75%** and ensuring scalability.

---

## 📈 Exploratory Data Analysis (EDA)

Key insights derived from the analysis:

- **Monthly sales trend:** steady growth, with a peak in **November 2017** (~1,010K BRL).
- **Highest‑demand months:** August, May, July (all ~0.8% above annual average).
- **Category‑specific seasonality:**
  - *Computers* peak in **September** (back‑to‑school).
  - *Art* peaks in **May** (exhibition season).
  - *Technical books* also peak in **May** (professional training period).
- **Hourly sales peak:** Monday **14:00–16:00**; lowest activity Monday 04:00–06:00.
- **Price vs. demand:** strongest demand in the **50–100 BRL** range.
- **Satisfaction (review score)** does **not** correlate strongly with sales volume.
- **Delivery time** does affect customer satisfaction.
- **Number of photos** (>10) has no significant impact on sales.
- **Customer recency:** the growing number of recent customers reflects the overall sales increase.

---

## 🤖 Predictive Modelling

Three models were built and compared to forecast demand **per product category**.

### Models Used

| Model | Description | Best For |
|-------|-------------|----------|
| **Facebook Prophet** | Designed for time series with strong seasonalities; easy to use and interpret. | Data with clear seasonal patterns and holidays. |
| **SARIMA** | Classical statistical model for seasonal, stable time series. | Short‑term forecasting of regular, gap‑free series. |
| **XGBoost** | Powerful gradient boosting algorithm that captures complex, non‑linear relationships. | Datasets with many external features and hidden interactions. |

### Evaluation Metrics
- **MAE** (Mean Absolute Error) – average error in original units.
- **MAPE** (Mean Absolute Percentage Error) – relative error in percentage.
- **R²** (Coefficient of Determination) – proportion of variance explained by the model.

---

## 🏆 Results

The best performing model varied by category. Examples:

- **Prophet** – *Health & Beauty*: **MAPE = 20.4%**
- **SARIMA** – *Home Appliances*: **MAPE = 22.6%**
- **XGBoost** – *Computer Accessories*: **MAPE = 17.7%**

Detailed results, including metric comparisons for all 15 categories, are available inside the project notebooks.

---

## 🛠️ Technologies Used

- **Python 3.8+**
- **Pandas, NumPy** – data manipulation
- **Matplotlib, Seaborn** – data visualisation
- **Facebook Prophet** – time‑series forecasting
- **Statsmodels (SARIMA)** – statistical modelling
- **XGBoost** – gradient boosting
- **Scikit‑learn** – preprocessing and evaluation
- **Jupyter Notebook** – interactive development

---

## 📁 Project Structure

Machine-Learning-Predictive-Models/
├── 📜 README.md
├── 📦 Proejecte Final_ZIP.zip # Zipped folder with all notebooks and scripts
├── 📊 Projecte Final _ Presentació Olist.pptx # Final presentation (this content)
└── 📜 requirements.txt # Python dependencies (to be created)
