# Data Preprocessing & Transformation

This repository demonstrates essential data preprocessing and transformation techniques using two different real‑world datasets. One is fully cleaned, the other is left raw for practice or future work.

## 🎯 What is Data Preprocessing?

Raw data is rarely ready for analysis or machine learning. It often contains:
- Missing values
- Inconsistent formatting
- Wrong data types
- Errors or placeholders
- Unscaled numeric features

This repository shows how to systematically fix these issues and transform raw data into a clean, structured, model‑ready format.

---

## 📁 Project 1: Cafe_Sales – Complete Example

**Concept:** A café records daily sales, but the data is intentionally messy. This project walks through every step of cleaning and transforming it.

### What the raw data contains:
- Missing values (empty cells, `UNKNOWN` strings)
- Error markers (`ERROR` in price columns)
- Mixed data types
- Malformed CSV rows

### What you learn from this notebook:
| Technique | Why it matters |
|-----------|----------------|
| **Handling missing values** | Filling numeric gaps with median, categorical with mode |
| **Data type conversion** | Turning strings into numbers, dates into datetime |
| **Error detection** | Replacing `ERROR` placeholders with `NaN` |
| **One‑hot encoding** | Converting categories (Item, Payment Method) into binary columns |
| **Date parsing** | Extracting day, month, year from a single date column |
| **Feature binning** | Creating a price group column ("cheap", "affordable", etc.) |
| **Scaling (StandardScaler)** | Bringing numeric features to a common scale (mean 0, variance 1) |
| **Train‑test split** | Preparing data for machine learning evaluation |

**Output:** `cleaned_data.csv` – fully numeric, scaled, no missing values.

---

## 📁 Project 2: Life_Expectancy – Raw Data for Practice

**Concept:** A global health dataset from WHO, containing life expectancy, GDP, mortality rates, schooling, and more for many countries over multiple years.

### This dataset is intentionally **unprocessed** – it’s provided as‑is for you to practice your own preprocessing.

### What makes it a good challenge:
- Missing values in several columns
- Numeric and categorical columns (Country, Status – Developed/Developing)
- Different scales (GDP in thousands, schooling in years, alcohol consumption)
- Time‑series structure (multiple years per country)

### Suggested preprocessing tasks you can try:
1. Handle missing values (drop or impute)
2. Convert `Status` into a binary numeric column (Developed=1, Developing=0)
3. Scale the numeric features (GDP, Life expectancy, Adult Mortality, etc.)
4. Create features like "life expectancy change over 5 years"
5. Split into train/test for predictive modeling

**No notebook is included for this dataset** – that’s intentional. You can create your own using the same techniques shown in `Cafe_Sales`.

---

## 🧠 Why Two Different Examples?

| | Cafe_Sales | Life_Expectancy |
|--|------------|------------------|
| **Type of data** | Transaction logs | Country health indicators |
| **Common issues** | Placeholders, error strings, malformed rows | Missing values, mixed scales, time‑series structure |
| **Goal** | Teach the full pipeline step‑by‑step | Provide raw material for independent practice |
| **Readiness** | ✅ Complete with explanation | 📦 Raw data only |

Together, they cover the most common real‑world data problems you’ll encounter.

---

## 🚀 How to Run the Cafe_Sales Notebook

```bash
git clone https://github.com/XENZA7/Data_Preprocessing_Transformation.git
cd Data_Preprocessing_Transformation
pip install pandas numpy scikit-learn
jupyter notebook Cafe_Sales/cafe_sales.ipynb
