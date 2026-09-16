# MSBA 265 — Business Analytics Topics

## Foundational Module 1: Practical Homework Assignment

**Student:** Ritvik Genugula

**ID:** 989519424

**Instructor:** Shyla Solis

**Term:** Fall 2026

---

## Contents

* [Project Structure](#project-structure)
* [Dataset Info](#dataset-info)
* [Setup](#setup)
* [Reproduction](#reproduction)

  * [1. Download the Raw Dataset](#1-download-the-raw-dataset)
  * [2. Run the Exploratory Analysis](#2-run-the-exploratory-analysis)
  * [3. Run the Production Outlier Pipeline](#3-run-the-production-outlier-pipeline)
* [Expected Results](#expected-results)
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
msba265-module1-ritvikg/
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

### 1. Clone the Repository

From a terminal, navigate to the location where you want to store the project and run:

```powershell
git clone https://github.com/g-ritvik/msba265-module1-ritvikg.git
cd msba265-module1-ritvikg
```

### 2. Create a Virtual Environment

From the project root:

```powershell
python -m venv venv
```

**If PowerShell blocks script execution**, run the following command in the current PowerShell session:

```powershell
Set-ExecutionPolicy -ExecutionPolicy Bypass -Scope Process
```

Then activate the virtual environment:

```powershell
.\venv\Scripts\activate
```

### 3. Install Required Dependencies

With the virtual environment activated:

```powershell
pip install -r requirements.txt
```

## Reproduction

### 1. Download the Raw Dataset

Run:

```powershell
python data/download_data.py
```

This downloads the dataset and creates:

[`data/raw_business_data.csv`](data/raw_business_data.csv)

### 2. Run the Exploratory Analysis

Open:

[`notebooks/01_eda_and_data_dictionary.ipynb`](notebooks/01_eda_and_data_dictionary.ipynb)

OR Run:

```powershell
code notebooks\01_eda_and_data_dictionary.ipynb
```

Select the project's `venv` Python environment as the notebook kernel and run all cells from top to bottom.

The notebook performs the data audit, Business Data Dictionary generation, skewness diagnostics, correlation analysis, distribution analysis, and outlier audit.

The notebook generates:

* [`reports/data_dictionary.csv`](reports/data_dictionary.csv)
* [`reports/figures/correlation_heatmap.png`](reports/figures/correlation_heatmap.png)
* [`reports/figures/feature_distributions.png`](reports/figures/feature_distributions.png)

### 3. Run the Production Outlier Pipeline

Run from the project root:

```powershell
python src/clean_outliers.py
```

This applies Tukey's **1.5 × IQR** rule to the `Density` feature and creates:

[`data/cleaned_business_data.csv`](data/cleaned_business_data.csv)

## Expected Results

After successfully following the reproduction steps:

* Raw dataset: **678,013 rows × 12 columns**
* Cleaned dataset: **600,447 rows × 12 columns**
* Density outliers removed: **77,566 (11.44%)**
* Business Data Dictionary generated in `reports/data_dictionary.csv`
* Required figures generated in `reports/figures/`

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
