# Predicting MBA Job Placement Outcomes

A machine learning project that predicts whether an MBA student will be **Placed** or **Not Placed** based on their academic performance, work experience, employability test scores, and interview results.

Built for **BAN 668 – Python Programming for Data Analysis**.

---

## Project Overview

MBA programs want to know early which students might struggle to land a job, so they can offer extra career support. This project builds a binary classification model that predicts placement status from a student's pre-placement profile, and points out which factors matter most.

**Best model:** A tuned Logistic Regression achieved **93% test accuracy** and an **F1 score of 0.95** on the Placed class, while still catching at-risk students (0.85 recall on the Not Placed class).

---

## Dataset

- **File:** `Job_Placement_Data_Enhanced.csv`
- **Records:** 215 MBA students
- **Predictors:** 18 (after cleaning)
- **Missing values:** none
- **Target variable:** `status` (Placed / Not Placed)
- **Class balance:** 148 Placed (68.8%) vs. 67 Not Placed (31.2%) — moderate imbalance

The features cover secondary/higher-secondary school scores, undergraduate degree, MBA percentage, work experience, an employability test score, skills-match percentage, certifications, internship completion, and an interview score.

> **Note on data leakage:** Two columns — `company_tier` and `job_competition_level` — were removed before modeling. They are only known *after* a student is placed, so keeping them would have leaked the answer into the model.

---

## What the Project Does

1. **Data cleaning** – checks for missing values, removes leakage columns.
2. **Feature engineering** – creates an ordered `AcademicLevel` (Low / Medium / High) and a combined `AcademicScore` from the three school-level percentages.
3. **Exploratory Data Analysis (EDA)** – distributions, correlation heatmap, placement rates by specialization and academic level, and more.
4. **Preprocessing** – one-hot encoding, an 80/20 stratified train/test split, and `StandardScaler` (fit on training data only).
5. **Modeling** – trains and compares Logistic Regression, Decision Tree, and K-Nearest Neighbors.
6. **Tuning** – improves the best model (Logistic Regression) with `GridSearchCV` and 5-fold cross-validation.
7. **Saving** – exports the final model and scaler with `joblib` for reuse.

---

## Results

| Model | Accuracy |
|---|---|
| Logistic Regression (baseline) | 0.88 |
| Decision Tree | 0.77 |
| K-Nearest Neighbors | 0.72 |
| **Logistic Regression (tuned)** | **0.93** |

**Tuned model report:** precision 0.94 and recall 0.97 on the Placed class; precision 0.92 and recall 0.85 on the Not Placed class.

### Key insights
- Placed students scored higher academically at every education level.
- Prior work experience is linked to a higher placement rate.
- Marketing & Finance students were placed at a higher rate than Marketing & HR students.
- Because the classes are imbalanced, F1 score and minority-class recall were used as the main metrics rather than accuracy alone.

---

## Tech Stack

- **Python**
- **pandas**, **NumPy** – data handling
- **Matplotlib**, **seaborn** – visualization
- **scikit-learn** – modeling, tuning, evaluation
- **joblib** – saving the model

---

## Repository Contents

| File | Description |
|---|---|
| `MBA_Placement_Prediction.ipynb` | Main Jupyter notebook (analysis + modeling) |
| `Job_Placement_Data_Enhanced.csv` | The dataset |
| `Predicting_MBA_Job_Placement_Outcomes.pdf` | Full written report |
| `MBA_Placement_Presentation.pptx` | Project presentation slides |
| `README.md` | This file |

---

## How to Run It

1. Clone or download this repository.
2. Install the required libraries:
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn joblib
   ```
3. Open the notebook:
   ```bash
   jupyter notebook MBA_Placement_Prediction.ipynb
   ```
4. Run the cells from top to bottom. Make sure `Job_Placement_Data_Enhanced.csv` is in the same folder as the notebook.

---

## Author

**Newton Mwirebua**
BAN 668 – Python Programming for Data Analysis
