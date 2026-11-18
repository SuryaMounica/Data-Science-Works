# Data Science Works

A collection of data science projects and assignments.

## Projects

| Project | Type | Folder |
|---|---|---|
| Crop Disease Detection | Supervised learning (multi-class classification) | [`Supervised`](./Supervised) |
| Red Wine Quality Analysis | Exploratory data analysis (correlation study) | [`Unsupervised`](./Unsupervised) |

---

## 1. Crop Disease Detection (Supervised Learning)

CEDLEARN capstone project that classifies a crop observation into one of four classes using environmental sensor data, soil measurements, and farm management records:

- Healthy
- Fungal
- Bacterial
- Pest Damage

### Files

- `Crop_Disease_Detection_Supervised.ipynb`: main notebook with the full analysis
- `crop_disease_dataset.csv`: input dataset (5,000 rows, 18 columns)

### Workflow

**Exploratory Data Analysis**
- Checked shape, data types, and missing values (roughly 3% to 28% per column)
- Found inconsistent capitalisation in categorical columns (e.g. `Maize` vs `maize`)
- Checked class distribution: Healthy (1531), Bacterial (1253), Fungal (1217), Pest Damage (999), so mildly imbalanced
- Found impossible values (temperature from -5°C to 120°C, humidity from -10% to 200%)
- Plotted soil pH by class and a correlation heatmap of numerical features

**Data Cleaning**
- Standardised categorical columns to Title Case
- Replaced out-of-range sensor values with NaN using domain-knowledge limits
- Imputed missing values: median for skewed columns, mean for symmetric ones, mode for categorical and binary columns

**Feature Engineering**
- `HTI`: heat-humidity stress index
- `drought_stress`: flag for long dry spells with low rainfall
- `maturity_stage`: Seedling, Vegetative or Reproductive, ordinal encoded
- One-hot encoding for nominal categorical columns

**Modeling and Evaluation**
- Stratified 80/20 train/test split
- Models: Decision Tree, K-Nearest Neighbors (k = 3, 5, 7), Random Forest
- Metrics: accuracy, per-class precision/recall/F1, macro-F1, and a confusion matrix for the best model

### Results

| Model | Train Acc | Test Acc | Macro F1 |
|---|---|---|---|
| Decision Tree | - | - | - |
| KNN | - | - | - |
| Random Forest | - | - | - |

**Key findings:**
- `Pest Damage` was the hardest class to predict because it is the minority class and overlaps with Fungal and Bacterial conditions.
- **Random Forest** is recommended for deployment. It generalises better than a single Decision Tree, is less sensitive to feature scaling than KNN, and provides feature importances that agronomists can use to understand predictions.

### Tools Used

Python, Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn, SciPy

---

## 2. Red Wine Quality Analysis (Exploratory Data Analysis)

CEDLEARN Data Analytics Lab project that investigates which chemical attributes drive red wine quality scores, so winemakers can set objective quality benchmarks, reduce spoilage risk, and fine-tune fermentation.

### Files

- `Wine Quality.ipynb`: main notebook answering Q01 to Q10
- `Wine Quality Analysis.pdf`: exported report
- `winequality-red.csv`: dataset (1,599 records, 12 attributes)

### Dataset

- 11 physicochemical features (fixed acidity, volatile acidity, citric acid, residual sugar, chlorides, free sulfur dioxide, total sulfur dioxide, density, pH, sulphates, alcohol)
- `quality`: expert score from 0 to 10 (actual values range from 3 to 8)
- No missing values, so no cleaning was needed

### Quality Tiers Used

| Tier | Score |
|---|---|
| Low | 4 or below |
| Mid | 5 to 6 |
| High | 7 or above |

### Questions Answered

| Q# | Topic | Key Finding |
|---|---|---|
| Q01 | Alcohol vs quality | Moderate positive correlation (about 0.48) |
| Q02 | Volatile acidity impact | Negative correlation (about -0.39); strongest spoilage signal |
| Q03 | Citric acid, low vs high quality | High-quality wines have higher citric acid |
| Q04 | pH across quality grades | Stable around 3.2 to 3.3; weak differentiator |
| Q05 | Residual sugar vs density | Mild positive correlation (about 0.36) |
| Q06 | Free/Total SO2 ratio vs score | Weak relationship with quality |
| Q07 | Strongest inverse relationship | Volatile acidity |
| Q08 | Sulphates, premium vs standard | Premium wines have higher sulphates |
| Q09 | Chlorides, top vs lower tier | Top-tier wines have slightly lower chlorides |
| Q10 | Best acidity combination | High fixed acidity, high citric acid, low volatile acidity |

**Conclusion:** Alcohol content and volatile acidity are the two strongest individual drivers of red wine quality in this dataset. Alcohol pushes quality up and volatile acidity pulls it down. Citric acid, sulphates, and fixed acidity are secondary factors, while pH, chlorides, and the SO2 ratio play minor roles.

### Tools Used

Python, Pandas, NumPy, Matplotlib, Seaborn

---
