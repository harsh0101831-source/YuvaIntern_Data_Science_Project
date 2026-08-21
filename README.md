# YuvaIntern Data Science Project

This repository contains my work completed during the YuvaIntern Data Science internship, covering practical tasks in data preprocessing, exploratory data analysis, unsupervised learning, supervised learning, deep learning, and an integrated capstone project.

## Tasks

| Task | Topic | Status |
|------|-------|--------|
| Task 1 | Data Acquisition, Cleaning & Preprocessing | Completed |
| Task 2 | Exploratory Data Analysis & Visualization | In Progress |
| Task 3 | Unsupervised Learning & Clustering | Planned |
| Task 4 | Supervised Learning Model Implementation | Planned |
| Task 5 | Deep Learning Application | Planned |
| Task 6 | Integrative Capstone Project | Planned |

---

## Task 1 — Air Quality Data Cleaning & Preprocessing

### Objective

The first task focused on acquiring a publicly available air-quality dataset, understanding its structure and data-quality issues, and performing data cleaning and preprocessing using Python.

### Dataset

The project uses the Air Quality UCI dataset, containing hourly measurements of air pollutants and environmental conditions.

### Data Cleaning & Preprocessing

The following data-quality issues were investigated and addressed:

- Inspected dataset dimensions and data types
- Identified completely empty rows
- Identified duplicate rows
- Detected invalid values represented by `-200`
- Evaluated missing-value percentages
- Removed the highly incomplete `NMHC(GT)` feature
- Identified potential outliers using the IQR method
- Combined date and time information into a single `Datetime` column
- Validated the final dataset

### Final Dataset

After preprocessing:

- **Rows:** 9,357
- **Columns:** 13
- **Missing values:** 0
- **Remaining `-200` values:** 0
- **Duplicate rows:** 0
- **Invalid datetime values:** 0

### Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- Jupyter Notebook

## Repository Structure

```text
YuvaIntern_Data_Science_Project/
│
├── task1_air_quality/
│   ├── notebooks/
│   │   └── task1_air_quality.ipynb
│   └── outputs/
│       └── air_quality_cleaned.csv
├── requirements.txt
├── .gitignore
└── README.md
