# Bankruptcy Prediction — US Public Companies

Binary classification task: predict whether a US public company (NYSE/NASDAQ-listed) will file for bankruptcy (Chapter 7 or Chapter 11) in the following year, using annual accounting data.

## Dataset

**Source:** `american_bankruptcy.csv`
**Coverage:** US public companies, fiscal years 1999–2018
**Features:** 18 accounting-based financial ratios/metrics (X1–X18)
**Target:** `status_label` — `"failed"` (1) or `"alive"` (0)

The label is applied to the fiscal year **prior** to bankruptcy filing, making this a 1-year-ahead prediction task.

## Project Structure

```
.
├── README.md
├── requirements.txt
├── data/
│   └── american_bankruptcy.csv
└── notebooks/
    └── bankruptcy_prediction.ipynb
```

## Features

| Feature | Description |
|---------|-------------|
| X1 | Current Assets |
| X2 | Cost of Goods Sold |
| X3 | Depreciation & Amortization |
| X4 | EBITDA |
| X5 | Inventory |
| X6 | Net Income |
| X7 | Total Receivables |
| X8 | Market Value (market capitalisation) |
| X9 | Net Sales |
| X10 | Total Assets |
| X11 | Total Long-term Debt |
| X12 | EBIT |
| X13 | Gross Profit |
| X14 | Total Current Liabilities |
| X15 | Retained Earnings |
| X16 | Total Revenue |
| X17 | Total Liabilities |
| X18 | Total Operating Expenses |

## Train / Validation / Test Split

Temporal split prescribed by dataset authors — **do not use random splitting**.

| Split | Years | Purpose |
|-------|-------|---------|
| Train | 1999–2011 | Model fitting |
| Validation | 2012–2014 | Hyperparameter tuning |
| Test | 2015–2018 | Final evaluation |

## Class Imbalance

~14:1 ratio (73,462 alive vs 5,220 failed). Imbalance-aware techniques are required.

## Evaluation Metrics

- **Primary:** PR-AUC (Precision-Recall AUC)
- **Secondary:** F1-score, Precision, Recall, Confusion Matrix

## Setup

```bash
pip install -r requirements.txt
jupyter notebook notebooks/bankruptcy_prediction.ipynb
```