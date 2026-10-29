# Predictive Analysis of Eye Disease Using Machine Learning

An academic machine-learning project for the INT234 Predictive Analysis course at Lovely Professional University. The project explores a tabular health dataset and compares three binary classification models for the dataset label `has_eye_disease`.

> **Important health and data limitation:** This is an academic experiment, not a medical device or diagnostic tool. The dataset's collection source and clinical validity were not documented in the supplied project files. Do not use the model for patient care or individual health decisions.

## Project overview

- **Dataset:** 20,000 records; the supplied original file had 18 columns.
- **Target:** `has_eye_disease`
- **Models:** Logistic Regression, Random Forest, Gradient Boosting
- **Workflow:** data inspection, preprocessing, exploratory data analysis (EDA), train/test split, model training, evaluation, and model comparison.
- **Tools:** Python, pandas, NumPy, Matplotlib, Seaborn, scikit-learn, Jupyter Notebook.

## Repository structure

```text
eye-disease-predictive-analysis/
├── data/
│   └── processed_dataset.csv
├── notebooks/
│   └── EyeDisease.ipynb
├── docs/
├── requirements.txt
├── .gitignore
└── README.md
```

The public CSV copy omits the original `name` and `Unnamed: 0` identifier/index columns. The notebook reads the CSV using a relative path.

## Run the project locally

### 1. Clone the repository

```bash
git clone https://github.com/YOUR-USERNAME/eye-disease-predictive-analysis.git
cd eye-disease-predictive-analysis
```

### 2. Create and activate a virtual environment

**macOS / Linux**
```bash
python3 -m venv .venv
source .venv/bin/activate
```

**Windows**
```powershell
py -m venv .venv
.venv\Scripts\activate
```

### 3. Install dependencies

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### 4. Launch Jupyter

```bash
jupyter notebook
```

Open `notebooks/EyeDisease.ipynb` and run the cells from top to bottom. The notebook expects `data/processed_dataset.csv` to be present in the repository.

## Results reported in the project report

The supplied report records the following results on one 80:20 train/test split (4,000 test records):

| Model | Accuracy | Precision | Recall | F1-score | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| Logistic Regression | 75.23% | 1.0000 | 0.5018 | 0.6682 | 0.7604 |
| Random Forest | 74.35% | 0.9454 | 0.5138 | 0.6658 | 0.7506 |
| Gradient Boosting | 75.15% | 0.9960 | 0.5023 | 0.6678 | 0.7489 |

These values are dataset- and split-specific and may vary by environment. Recall is around 50%, meaning many positive-labelled records are missed. High precision should not be mistaken for clinical reliability.

## Main steps

1. Inspect data shape, types, missing values, and descriptive statistics.
2. Remove identifier/index fields and the combined blood-pressure text column.
3. One-hot encode `obesity_group` and `bp_category`.
4. Explore distributions, potential outliers, and correlations.
5. Split data into training and testing subsets (80:20; `random_state=42`).
6. Train and compare Logistic Regression, Random Forest, and Gradient Boosting.
7. Evaluate accuracy, precision, recall, F1-score, ROC-AUC, confusion matrices, and feature importance.

## Limitations and next steps

- The dataset source, collection method, and clinical label validation are not documented in the supplied files.
- The `has_diabetic_retinopathy` feature is strongly associated with the target; potential target leakage should be investigated.
- Results use a single train/test split and mostly default model settings.
- Future work should audit leakage, use stratified cross-validation and a scikit-learn pipeline, tune decision thresholds, evaluate subgroups, and validate on an independent dataset.

## Author

**Aryan**  
B.Tech CSE (2nd Year) | Lovely Professional University  
Course: INT234 — Predictive Analysis

## Disclaimer

For educational and research purposes only. This project does not provide medical advice, diagnose disease, or replace evaluation by a qualified healthcare professional.
