# Data Preprocessing & Transformation

A hands‑on demonstration of essential data preprocessing and feature engineering techniques using a messy real‑world dataset.

## 📁 Project Structure

## ☕ Cafe_Sales – Full Preprocessing Pipeline

The `Cafe_Sales` project takes a deliberately messy sales record and transforms it into a clean, machine‑learning‑ready dataset.

### Input Issues (Raw Data)
- Missing values (empty cells, `UNKNOWN`, empty strings)
- Error markers like `ERROR` in numeric columns
- Incorrect data types
- Malformed CSV rows

### Preprocessing Steps (in `cafe_sales.ipynb`)
1. **Data Cleaning**  
   - Convert columns to proper types (`Price Per Unit`, `Total Spent`)  
   - Replace invalid entries with `NaN`  
   - Impute missing values (median for numeric, mode for categorical)  
   - Drop rows with critical conversion failures

2. **Feature Engineering**  
   - One‑hot encode categorical variables (`Item`, `Payment Method`, `Location`)  
   - Parse `Transaction Date` into `Day`, `Month`, `Year`  
   - Create `PricePerUnit_group` (binned price category)

3. **Scaling & Splitting**  
   - Standardize numeric features with `StandardScaler`  
   - Split data into training and test sets using `train_test_split`

### Output
- `cleaned_data.csv` – fully numeric, scaled, no missing values, ready for modeling.

## 🌍 Life_Expectancy – Incomplete

This folder currently contains only the raw `Life_Expectancy.csv` dataset (health and economic indicators). No preprocessing notebook or output is provided at this time.

## 🚀 How to Run

1. Clone the repository:
   ```bash
   git clone https://github.com/XENZA7/Data_Preprocessing_Transformation.git
