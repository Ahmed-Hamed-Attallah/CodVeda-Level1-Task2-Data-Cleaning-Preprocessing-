# Retail Sales Data Cleaning & Preprocessing Pipeline

## 📌 Project Overview
This project focuses on the crucial data preparation phase for a retail store sales dataset. The initial raw data was incomplete and unusable. This pipeline processes the data through systematic cleaning, handling of missing values, outlier treatment, and feature engineering to produce a high-quality dataset ready for analysis and machine learning.

## 🎯 Objectives
- **Assess Data Quality:** Perform an initial analysis to identify missing values, inconsistencies, and potential errors.
- **Clean the Data:** Handle missing values using intelligent imputation and logical deletion.
- **Treat Outliers:** Identify and remove statistical anomalies to prevent skewed analysis.
- **Encode Categorical Variables:** Transform text-based categories into numerical representations suitable for algorithms.
- **Scale Numerical Features:** Normalize the data to ensure uniform scale for machine learning models.
- **Deliver Two Final Datasets:** One for Exploratory Data Analysis (EDA) and another for Machine Learning (ML).

## 📊 Initial Data Challenge
The originally provided dataset contained no headers, making it impossible to work with. It was replaced with a `retail_store_sales.csv` dataset from Kaggle, containing 12,575 transactions and 11 features.

**Initial Data Quality Report Revealed:**
- **High Missingness:** `Discount Applied` (33.39%) was missing significantly.
- **Moderate Missingness:** `Item` (~9.65%), `Price Per Unit`, `Quantity`, and `Total Spent` (~4.8% each).

## 🛠️ Process & Techniques

### 1. Handling Missing Data
- **KNN Imputation:** Used for `Item` and `Discount Applied` to preserve complex relationships between features (`n_neighbors=8`).
- **Row Deletion:** Applied for `Price Per Unit`, `Quantity`, and `Total Spent` as imputation was deemed illogical for financial metrics.

### 2. Outlier Treatment
- **IQR Method:** Used to detect and remove outliers from the `Total Spent` column based on statistical boundaries.

### 3. Feature Encoding
- **Label Encoding:** Applied to high-cardinality nominal variables like `Customer ID`, `Category`, and `Item`.
- **One-Hot Encoding:** Applied to nominal variables with few categories (`Payment Method`, `Location`) to avoid false ordinal relationships.

### 4. Feature Scaling
- **Standardization (Z-Score):** Applied to `Price Per Unit` and `Total Spent` to center the data around a mean of zero with a standard deviation of one.
- **No Scaling:** The `Quantity` feature was left unchanged due to its naturally small and consistent range (1-10).

## 📂 Output Datasets
The pipeline produces two final datasets:
1. **`retail_store_sales_clean.csv`:** Cleaned data with original values intact. Ideal for **EDA and visualization**.
2. **`retail_store_sales_model.csv`:** Fully processed and feature-engineered data. Ideal for **Machine Learning modeling**.

## 🚀 Technologies Used
- **Python**
- **Pandas** (Data Manipulation)
- **Scikit-learn** (Imputation: `KNNImputer`, Encoding: `LabelEncoder`, `OneHotEncoder`, Scaling: `StandardScaler`)
- **Plotly Express** (Data Visualization for Outlier Detection)

## 📈 Results
- Successfully handled all missing data and outliers.
- Reduced the dataset from **12,575** to **11,306** high-quality records.
- All categorical features were converted to numerical formats.
- Numerical features were scaled appropriately for ML algorithms.
- The data is now primed for uncovering insights and building predictive models.

## 🔮 Next Steps
- Perform Exploratory Data Analysis (EDA) on `retail_store_sales_clean.csv`.
- Use `retail_store_sales_model.csv` to build predictive models for tasks like:
  - Sales forecasting
  - Customer segmentation
  - Predicting discount effectiveness
