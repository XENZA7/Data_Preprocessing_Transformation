# Data Preprocessing & Transformation

This repository contains two projects that demonstrate how to clean, transform, and prepare raw data for machine learning. One project is a complete walkthrough; the other is a raw dataset with a full preprocessing script.

---

##  Project 1: Cafe_Sales – Complete Preprocessing Pipeline

### Concept
A café records daily sales, but the data is messy (missing values, error strings, wrong data types). The goal is to turn it into a clean, numeric, scaled dataset ready for any ML model.

### What the Code Does (`cafe_sales.ipynb`)

| Step | What the code does | Why |
|------|-------------------|------|
| **Load & inspect** | Reads `dirty_cafe_sales .csv`, checks shape, info, missing values. | Understand the problems. |
| **Clean data types** | Converts `Price Per Unit` and `Total Spent` to numbers; replaces `ERROR` with `NaN`. | Models need numeric input. |
| **Handle missing values** | Fills numeric gaps with median, categorical with mode. | Avoids losing rows. |
| **Feature engineering** | One‑hot encodes `Item`, `Payment Method`, `Location`. Extracts day/month/year from `Transaction Date`. Creates `PricePerUnit_group` (binned prices). | Turns text into numbers; creates new signals. |
| **Scale features** | Applies `StandardScaler` to numeric columns. | Prevents large‑range features from dominating. |
| **Split data** | Uses `train_test_split`. | Needed for honest evaluation. |
| **Save output** | Writes `cleaned_data.csv`. | Final ready‑to‑use dataset. |

**Key concept:** Real data is never clean – you must systematically fix types, missing values, and encode categories before modeling.

---

##  Project 2: Life_Expectancy – Full Preprocessing Script

### Concept
A WHO dataset with life expectancy, GDP, mortality, immunization, etc. for many countries over multiple years. The code below (which you can run as a Python script or notebook) performs a complete preprocessing + modeling workflow.

### What the Code Does (the long script provided)

#### 1. Exploratory Data Analysis (EDA)
- **Histograms** – see distribution of each numeric feature.
- **Boxplots** – detect outliers.
- **Scatter plots** – check relationship with `Life expectancy`.
- **Heatmap** – see correlations between all numeric variables.

#### 2. Handling Missing Values
- First, manual median imputation for `BMI`, `Polio`, `Income composition`.
- Then **KNN Imputer** – fills missing values using similar rows (based on other numeric features).  
  *Concept:* KNN looks at neighbours to estimate missing values – more accurate than mean/median for structured data.

#### 3. Outlier Treatment (Winsorization)
- Defines `wisker(col)` function that computes 1.5×IQR bounds.
- Caps outliers in `GDP`, `Total expenditure`, and thinness columns to the lower/upper whisker.  
  *Concept:* replace extreme values with the nearest “normal” value instead of deleting them.

#### 4. Feature Engineering
- **`Life_Class`** – bins life expectancy into Low (<55), Medium (55‑70), High (>70).  
- **`Immunization_avg`** – average of Hepatitis B, Polio, Diphtheria.  
- **`log_GDP`** – natural log of GDP (handles huge range).  
- **`Alcohol_Level`** – bins alcohol consumption into Low/Moderate/High.

#### 5. Categorical Encoding
- **Label encoding** for `Life_Class` (0,1,2).  
- **Binary mapping** for `Status` (Developing→0, Developed→1).  
- **One‑hot encoding** for `Alcohol_Level` (drop first to avoid multicollinearity).  
- Drops `Country` (too many unique values).

#### 6. Feature Selection
- **SelectKBest (f_regression)** – picks top 12 features based on linear correlation with target.  
- **Random Forest importance** – picks top 12 based on non‑linear importance.  
- **Union** of both sets – captures linear + non‑linear relationships.  
- **Remove highly correlated (>0.8)** – drops redundant features.  
  *Concept:* fewer, independent features reduce overfitting and improve interpretability.

#### 7. Model Training & Comparison
- Splits data 80/20, scales with `StandardScaler`.  
- Trains **Linear Regression** and **Random Forest**.  
- Compares MAE, RMSE, R².  
- Plots actual vs predicted and feature importance (if Random Forest wins).

#### 8. Hyperparameter Tuning (Random Forest)
- Uses `RandomizedSearchCV` to try different `n_estimators`, `max_depth`, `min_samples_split`, etc.  
- Finds best parameters, then evaluates on test set.

**Key concepts demonstrated:**
- KNN imputation, outlier capping, log transformation, binning.
- Combined feature selection (linear + tree‑based).
- Scaling, model comparison, and hyperparameter tuning.

---

##  How to Run

### Cafe_Sales (Jupyter Notebook)
```bash
pip install pandas numpy scikit-learn
jupyter notebook Cafe_Sales/cafe_sales.ipynb
