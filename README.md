[README.md](https://github.com/user-attachments/files/35306332/README.md)
# Employee-Performance
Exploratory Data Science and Workforce Analytics using Python. Analyzing 100,000 employee records to investigate performance drivers, salary relationships, productivity, job satisfaction, and workforce trends through statistical analysis and data visualization.
# Workforce Performance & Productivity Analytics

<p align="center">
  <strong>Exploratory Data Analysis · Statistical Testing · Workforce Insights</strong><br>
  A reproducible Python analysis of employee performance, compensation, workload, and retention.
</p>

<p align="center">
  <img alt="Python" src="https://img.shields.io/badge/Python-3.10%2B-3776AB?logo=python&logoColor=white">
  <img alt="Jupyter" src="https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white">
  <img alt="pandas" src="https://img.shields.io/badge/pandas-Data%20Analysis-150458?logo=pandas&logoColor=white">
  <img alt="scikit-learn" src="https://img.shields.io/badge/scikit--learn-Feature%20Analysis-F7931E?logo=scikitlearn&logoColor=white">
  <img alt="Status" src="https://img.shields.io/badge/Status-EDA%20Complete-success">
</p>

## Project overview

This project explores a workforce dataset containing **100,000 employee records and 20 columns**. It examines how employee performance scores vary alongside compensation, workload, professional development, satisfaction, job characteristics, and resignation status.

The goal is not simply to produce charts. The analysis emphasizes data quality, appropriate statistical methods, careful interpretation, and the limitations of observational employee data.

> **Current release:** Exploratory data analysis (EDA) and statistical association analysis. Predictive modeling is a planned extension. This repository does not claim validated machine-learning performance or causal findings.

## Questions explored

1. How are employee performance scores distributed?
2. How do performance scores vary across departments and job titles?
3. How does monthly salary vary across performance-score groups?
4. What relationships appear between performance and workload, training, satisfaction, and other numerical attributes?
5. How do resignation rates and workforce characteristics differ across departments?
6. What do rank-based statistical tests and mutual-information estimates reveal?
7. What can—and cannot—be concluded from these observational data?

## Dataset

The notebook expects the following CSV file:

`Extended_Employee_Performance_and_Productivity_Data.csv`

The dataset used in the analysis has the following reported structure:

| Attribute | Value |
|---|---:|
| Records | 100,000 |
| Columns | 20 |
| Missing values | 0 |
| Duplicate rows | 0 |
| Performance score | Integer scale from 1 to 5 |
| Resignation rate | Approximately 10.01% |

The dataset contains employee identifiers, department, gender, age, job title, hire date, tenure, education, performance score, salary, work hours, projects handled, overtime, sick days, remote-work frequency, team size, training hours, promotions, satisfaction score, and resignation status.

**Data access and licensing:** The CSV is not included in this repository. Obtain it from the original dataset publisher and review its license and redistribution terms before using or sharing it. Place the file in the repository root or in a `data/` folder. Do not upload data that you are not authorized to redistribute.

## Key findings from the exploratory analysis

The following observations were obtained during the initial analysis of this dataset:

### 1. Performance scores are nearly evenly distributed

| Score | Employees | Share |
|---:|---:|---:|
| 1 | 20,120 | 20.12% |
| 2 | 20,013 | 20.01% |
| 3 | 19,999 | 20.00% |
| 4 | 19,940 | 19.94% |
| 5 | 19,928 | 19.93% |

The target is highly balanced in this sample. This is useful context for a future classification experiment, although class balance alone does not establish that the target is predictable.

### 2. Salary has the strongest observed association with performance

The initial analysis reported:

- Pearson correlation: **0.5100**
- Spearman rank correlation: **0.4778**
- Kruskal–Wallis test statistic: **22,833.24**
- Kruskal–Wallis p-value: reported as effectively zero at displayed precision

Median monthly salary increased by $500 across each successive performance-score group:

| Performance score | Median monthly salary |
|---:|---:|
| 1 | $5,500 |
| 2 | $6,000 |
| 3 | $6,500 |
| 4 | $7,000 |
| 5 | $7,500 |

This pattern deserves further investigation. It may reflect a real association in the dataset, a data-generation rule, or compensation practices that encode prior performance ratings. **It must not be interpreted as evidence that higher salary causes better performance.**

### 3. Most other individual numerical correlations were close to zero

In the initial Pearson correlation analysis, the other numerical variables had correlations close to zero with `Performance_Score`. This does not rule out nonlinear relationships, interactions, subgroup patterns, or measurement issues.

### 4. Resignation status was not strongly separated by average performance

The mean performance score was approximately 2.997 among employees marked as not resigned and 2.984 among employees marked as resigned. The difference is small descriptively and does not establish a relationship or causal effect.

## Methods and tools

### Python stack

- **pandas / NumPy** — data manipulation and numerical analysis
- **Matplotlib / Seaborn** — exploratory visualization
- **SciPy** — Spearman rank correlation and Kruskal–Wallis testing
- **scikit-learn** — mutual-information feature association

### Analysis workflow

1. Load the CSV and inspect its schema.
2. Check missing values, duplicate rows, and basic value validity.
3. Profile departments, job titles, education levels, and gender categories.
4. Examine performance-score distributions.
5. Compare performance across departments and job roles.
6. Analyze salary distributions by performance score.
7. Explore numerical correlations among workforce variables.
8. Compare resignation patterns across workforce groups.
9. Inspect hire-date patterns.
10. Apply rank-based statistical tests and estimate mutual information.

## Repository structure

```text
employee-performance-analytics/
├── Performance_Analytics.ipynb
├── README.md
├── requirements.txt
└── .gitignore
```

## Run the project locally

### 1. Clone the repository

```bash
git clone https://github.com/<YOUR-GITHUB-USERNAME>/employee-performance-analytics.git
cd employee-performance-analytics
```

### 2. Create and activate a virtual environment

```bash
python -m venv .venv
```

Windows PowerShell:

```powershell
.venv\Scripts\Activate.ps1
```

macOS / Linux:

```bash
source .venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Add the dataset

Place the CSV in either location:

```text
employee-performance-analytics/
├── Extended_Employee_Performance_and_Productivity_Data.csv
```

or:

```text
employee-performance-analytics/
├── data/
│   └── Extended_Employee_Performance_and_Productivity_Data.csv
```

The notebook also contains a Kaggle input path that can be adjusted for your environment.

### 5. Launch Jupyter

```bash
jupyter notebook Performance_Analytics.ipynb
```

Run the notebook cells from top to bottom.

## Interpretation, limitations, and responsible use

- The analysis is observational and does not establish causation.
- The dataset's collection process, generation process, and representativeness have not been independently established.
- The strong salary/performance pattern may indicate target leakage or a constructed relationship. Investigate the data-generation process before predictive modeling.
- Variables such as resignation status may occur after the performance measurement. Their timing must be verified before using them as predictors.
- Correlation and mutual information are association measures, not causal explanations.
- Large samples can produce very small p-values for effects with limited practical importance.
- Performance scores may be subjective or organization-specific.
- Demographic attributes require careful, legally informed fairness analysis.

**This project is for analytical and educational purposes. It should not be used to rank, discipline, hire, promote, or terminate individual employees.**

## Planned extensions

- Establish the dataset's provenance and measurement timeline.
- Test whether salary is a leakage proxy or a direct encoding of the target.
- Build leakage-aware baseline models for the ordinal performance score.
- Compare CatBoost, LightGBM, XGBoost, and interpretable alternatives only if the data supports a meaningful prediction task.
- Evaluate ordinal errors, macro-F1, calibration, and generalization—not accuracy alone.
- Use SHAP and subgroup diagnostics to inspect model behavior.
- Develop a workforce analytics dashboard after validating the metrics.

## Author

**Data Science Portfolio Project**

Built with Python, statistical analysis, and responsible data-science practices.
