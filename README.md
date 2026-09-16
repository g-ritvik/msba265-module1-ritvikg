# MSBA 265 — Business Analytics Topics

## Foundational Module 1: Practical Homework Assignment

**Student:** Ritvik Genugula

**Instructor:** Shyla Solis

**Term:** Fall 2026

This repository contains the complete, reproducible submission for the MSBA 265 Foundational Module 1 Practical Homework Assignment.

The project covers raw data ingestion, data quality verification, business data dictionary creation, exploratory data analysis, correlation analysis, distribution analysis, and production outlier filtering.

---

## Contents

* [Project Structure](#project-structure)
* [Dataset Info](#dataset-info)
* [Setup](#setup)
* [Reproduction](#reproduction)

  * [1. Download the Raw Dataset](#1-download-the-raw-dataset)
  * [2. Run the Production Outlier Pipeline](#2-run-the-production-outlier-pipeline)
  * [3. Run the Exploratory Analysis](#3-run-the-exploratory-analysis)
* [Project Artifacts](#project-artifacts)

  * [Analysis](#analysis)
  * [Data](#data)
  * [Production Pipeline](#production-pipeline)
  * [Figures](#figures)
  * [Final Report](#final-report)
* [Final Pipeline Result](#final-pipeline-result)
* [Requirements](#requirements)

---

## Project Structure

```text
msba265_module1/
├── .gitignore
├── README.md
├── requirements.txt
├── Module1_Homework_Report.pdf
│
├── data/
│   ├── download_data.py
│   ├── raw_business_data.csv
│   └── cleaned_business_data.csv
│
├── notebooks/
│   └── 01_eda_and_data_dictionary.ipynb
│
├── src/
│   └── clean_outliers.py
│
└── reports/
    ├── data_dictionary.csv
    └── figures/
        ├── feature_distributions.png
        ├── correlation_heatmap.png
        └── outlier_filtering_comparison.png
```

## Dataset Info

The project uses the French Motor Third Party Liability Claims (`freMTPL2freq.csv`) dataset downloaded programmatically from OpenML.

The raw dataset contains **678,013 records and 12 features**.

## Setup

From the project root, create and activate a Python virtual environment:

```text
python -m venv venv
venv\Scripts\activate
```

Install the required dependencies:

```text
pip install -r requirements.txt
```

## Reproduction

### 1. Download the Raw Dataset

Run:

```text
python data/download_data.py
```

This downloads the dataset and creates:

[`data/raw_business_data.csv`](data/raw_business_data.csv)

### 2. Run the Production Outlier Pipeline

Run:

```text
python src/clean_outliers.py
```

This applies Tukey's **1.5 × IQR** rule to the `Density` feature and creates:

[`data/cleaned_business_data.csv`](data/cleaned_business_data.csv)

### 3. Run the Exploratory Analysis

Open the Jupyter notebook:

[`notebooks/01_eda_and_data_dictionary.ipynb`](notebooks/01_eda_and_data_dictionary.ipynb)

The notebook contains the data audit, business data dictionary generation, skewness diagnostics, correlation analysis, distribution analysis, and outlier audit.

## Project Artifacts

### Analysis

* [`01_eda_and_data_dictionary.ipynb`](notebooks/01_eda_and_data_dictionary.ipynb) — EDA and data dictionary notebook
* [`data_dictionary.csv`](reports/data_dictionary.csv) — Business Data Dictionary

### Data

* [`download_data.py`](data/download_data.py) — Raw data ingestion script
* [`raw_business_data.csv`](data/raw_business_data.csv) — Original downloaded dataset
* [`cleaned_business_data.csv`](data/cleaned_business_data.csv) — Dataset after production outlier filtering

### Production Pipeline

* [`clean_outliers.py`](src/clean_outliers.py) — Tukey IQR outlier filtering script

### Figures

* [`feature_distributions.png`](reports/figures/feature_distributions.png)
* [`correlation_heatmap.png`](reports/figures/correlation_heatmap.png)
* [`outlier_filtering_comparison.png`](reports/figures/outlier_filtering_comparison.png)

### Final Report

**[Download Module 1 Homework Report (PDF)](Module1_Homework_Report.pdf)**

## Final Pipeline Result

| Metric             |  Result |
| ------------------ | ------: |
| Raw Records        | 678,013 |
| Records Removed    |  77,566 |
| Percentage Removed |  11.44% |
| Cleaned Records    | 600,447 |

The production pipeline filters statistical outliers from the `Density` feature using Tukey's 1.5 × IQR rule.

## Requirements

Python dependencies are listed in [`requirements.txt`](requirements.txt).

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge\&logo=python\&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge\&logo=pandas\&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=for-the-badge\&logo=numpy\&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=for-the-badge\&logo=matplotlib\&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-4C72B0?style=for-the-badge)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge\&logo=jupyter\&logoColor=white)
