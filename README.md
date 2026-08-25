# ConnectaTel: Exploratory Data Analysis

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/DebbieJara/connectatel-customer-segmentation-analysis/blob/main/Project_ConnectaTel.ipynb)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-150458?style=flat&logo=pandas&logoColor=white)

**Business question:** Exploratory data analysis for ConnectaTel, a Latin American telecommunications company. The project identifies usage patterns, detects anomalous behavior, and segments customers to optimize the commercial offering and improve user experience.

## Context

The analysis covers three datasets: available plans (prices, minutes, GB included), customer demographic and plan data, and actual usage records (calls and messages), based on data recorded through 2024.

## Process

Initial exploration of structure and data types, data quality assessment (nulls, sentinels, and impossible dates), cleaning (sentinel correction, imputation, and invalid date flagging), aggregation of behavior metrics per user, visualization by plan type, outlier detection using boxplots and IQR limits, customer segmentation by age and usage level, and an executive summary with recommendations.

## Key findings

### Data quality

Sentinels were detected and corrected in `age` (-999, 55 records) and `city` ('?', 96 records), plus 469 null values in `city` (565 total missing, 14.12%). 40 impossible dates (year 2026) were found in `reg_date` and marked as null.

Nulls in `duration` and `length` were confirmed as MNAR (Missing Not At Random): they depend on the event type (call or text) and were kept as-is rather than imputed.

### Customer segmentation

- By age: 50.44% Adults, 30.56% Older Adults, 19% Young.
- By usage level: 73.59% Medium usage, 19.45% Low usage, 6.95% High usage.
- Older Adults (70-80 years) show a higher proportion of Premium plan subscribers, suggesting greater purchasing power.

### Usage patterns

Premium users send more messages and make more calls than Basic users. Call duration is similar between both plans: the plan influences frequency of use, not duration per call. Right-side outliers were detected in message count, call count, and call minutes, representing high-value users.

## Visualizations

![Message count distribution by plan](images/histograma_cant_mensajes.png)

![Call minutes distribution by plan](images/histograma_cant_minutos_llamada.png)

![Outlier boxplots](images/boxplots.png)

## Recommendations

- Upgrade campaign for Basic users with high usage volume, offering a discount on their first Premium month.
- Loyalty promotions for Older Adults on the Premium plan.
- Additional data offers for young users on the Basic plan, to build long-term engagement.
- Loyalty program for high-usage outlier users.
- Reactivation campaigns for Low usage users.

## Technical details

### Dataset

| File | Description |
|---|---|
| users_latam.csv | Demographic and plan information for 4,000 users |
| usage.csv | 40,000 usage records (calls and messages) |
| plans.csv | Description of the Basic and Premium plans |

## Tools

Python · pandas · NumPy · Seaborn · Matplotlib

## Repository structure

```text
connectatel-customer-segmentation-analysis/
├── README.md
├── Project_ConnectaTel.ipynb
├── plans.csv
├── usage.csv
├── users_latam.csv
└── images/
    ├── boxplots.png
    ├── histograma_cant_mensajes.png
    └── histograma_cant_minutos_llamada.png
```

---

By Deborah Jara | Business Intelligence · Data Analytics | Mexico
[LinkedIn](https://www.linkedin.com/in/deborahjara) · [GitHub](https://github.com/DebbieJara)
