# Data Science Works

A collection of data science projects and assignments.

## Projects

| Project | Type | Folder |
|---|---|---|
| Crop Disease Detection | Supervised learning (multi-class classification) | [`Supervised`](./Supervised) |

---

## Crop Disease Detection (Supervised Learning)

CEDLEARN capstone project that classifies a crop observation into one of four classes using environmental sensor data, soil measurements, and farm management records:

- Healthy
- Fungal
- Bacterial
- Pest Damage

### Files

- `Crop_Disease_Detection_Supervised.ipynb`: main notebook with the full analysis
- `crop_disease_dataset.csv`: input dataset (5,000 rows, 18 columns)

### Workflow

**1. Exploratory Data Analysis**
- Checked shape, data types, and missing values (roughly 3% to 28% per column)
- Found inconsistent capitalisation in categorical columns (e.g. `Maize` vs `maize`)
- Checked class distribution: Healthy (1531), Bacterial (1253), Fungal (1217), Pest Damage (999), so mildly imbalanced
- Found impossible values (temperature from -5°C to 120°C, humidity from -10% to 200%)
- Plotted soil pH by class and a correlation heatmap of numerical features

**2. Data Cleaning**
- Standardised categorical columns to Title Case
- Replaced out-of-range sensor values with NaN using domain-knowledge limits
- Imputed missing values: median for skewed columns, mean for symmetric ones, mode for categorical and binary columns

**3. Feature Engineering**
- `HTI`: heat-humidity stress index
- `drought_stress`: flag for long dry spells with low rainfall
- `maturity_stage`: Seedling, Vegetative or Reproductive, ordinal encoded
- One-hot encoding for nominal categorical columns

**4. Modeling and Evaluation**
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


### Author

Surya Mounica
