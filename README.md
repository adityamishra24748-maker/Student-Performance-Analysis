# Student Performance Analysis

Exploratory data analysis of a 1,000-student exam performance dataset, examining how
demographic and preparation factors (parental education, test prep, lunch type, gender)
relate to math, reading, and writing scores — with an at-risk segmentation and a
principal-facing summary report.

## Dataset

`StudentsPerformance.csv` — 1,000 rows, 8 columns:

| Column | Type | Description |
|---|---|---|
| gender | categorical | male / female |
| race/ethnicity | categorical | anonymized group label (A–E) |
| parental level of education | categorical (ordinal) | highest education level attained by a parent |
| lunch | categorical | standard vs free/reduced (SES proxy) |
| test preparation course | categorical | completed vs none |
| math score | numeric (0–100) | |
| reading score | numeric (0–100) | |
| writing score | numeric (0–100) | |

No missing values or duplicate rows. Two derived columns (`total_score`, `average_score`)
are added during cleaning.

## What this project does

1. **Data exploration & cleaning** — shape, dtypes, null/duplicate checks, column
   standardization, sanity checks on score ranges.
2. **Factor analysis (5 questions)** — parental education vs scores, test prep vs scores,
   inter-subject correlation, gender vs subject performance, total score distribution.
3. **Visualizations (6 charts)** — box plot, grouped bar charts, correlation heatmap,
   histogram, scatter plot with trend line.
4. **At-risk segmentation** — flags students scoring below 50 in any subject, and breaks
   down the at-risk rate by gender, race/ethnicity, parental education, lunch type, and
   test prep.
5. **Principal's report** — one-page executive summary, 5 key findings, 3 actionable
   recommendations.

## Key findings

- **18.8% of students (188/1,000)** are at-risk (score below 50 in at least one subject).
- **Lunch type is the strongest risk driver**: 31.3% at-risk on free/reduced lunch vs
  11.9% on standard lunch.
- **Test prep works**: completers score 7.6 points higher on average and are less than
  half as likely to be at-risk (10.1% vs 23.7%).
- **Reading and writing are tightly correlated** (r = 0.955); math is more independent
  (r ≈ 0.80 with each), suggesting math needs separate instructional support.
- **Gender splits by subject**: boys score higher in math, girls score higher in reading
  and writing.

## Repo structure

```
├── data/
│   ├── StudentsPerformance.csv        # raw input
│   ├── cleaned_students.csv           # cleaned dataset
│   ├── students_with_risk.csv         # + at_risk flag
│   ├── cleaning_log.txt               # full cleaning decision log
│   ├── results.json                   # all computed metrics
│   └── at_risk_by_group.json          # at-risk % by demographic group
├── charts/                            # 7 PNG charts (6 required + at-risk breakdown)
├── outputs/                           # final PDF reports
│   ├── 1_Data_Exploration_and_Cleaning.pdf
│   ├── 2_Factor_Analysis_and_Visualizations.pdf
│   ├── 3_At_Risk_Student_Segmentation.pdf
│   └── 4_Principals_Report.pdf
├── 01_explore_clean.py
├── 02_analysis.py
├── 03_charts.py
├── 04_at_risk_chart.py
├── 05_pdf1.py
├── 06_pdf2.py
├── 07_pdf3.py
└── 08_pdf4.py
```

## How to reproduce

```bash
pip install pandas numpy matplotlib reportlab
python 01_explore_clean.py     # clean + summarize
python 02_analysis.py          # answer the 5 factor-analysis questions + at-risk stats
python 03_charts.py            # 6 required charts
python 04_at_risk_chart.py     # at-risk breakdown chart
python 05_pdf1.py              # Data Exploration & Cleaning PDF
python 06_pdf2.py              # Factor Analysis & Visualizations PDF
python 07_pdf3.py              # At-Risk Segmentation PDF
python 08_pdf4.py              # Principal's Report PDF
```

## Tech stack

Python · pandas · numpy · matplotlib · reportlab

## License

For educational/portfolio use. Dataset originally published on Kaggle as
["Students Performance in Exams"](https://www.kaggle.com/datasets/spscientist/students-performance-in-exams).
