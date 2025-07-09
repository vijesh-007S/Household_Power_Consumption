# 🔌 Household Power Consumption Forecasting using Random Forest

This project aims to forecast **household power consumption** using the **Random Forest Regressor**, leveraging temporal and lag-based features. It uses the UCI Household Power Consumption Dataset to model and predict electricity usage at a fine-grained level, which can be crucial for optimizing energy management and conservation.

---

## 📂 Dataset

- **Source:** [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/individual+household+electric+power+consumption)
- **File Used:** `household_power_consumption.txt`
- **Time Period:** December 2006 to November 2010
- **Format:** Semicolon (`;`) separated text
- **Total Observations:** ~2 million
- **Important Columns:**
  - `Global_active_power` (Target)
  - `Global_reactive_power`
  - `Voltage`
  - `Global_intensity`
  - `Sub_metering_1`, `Sub_metering_2`, `Sub_metering_3`

---

## ⚙️ Technologies Used

- **Language:** Python 3
- **Libraries:** Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn
- **Model:** RandomForestRegressor (from `sklearn.ensemble`)

---

## 📊 Feature Engineering

The following features were created to enhance model performance:

### 🕒 Temporal Features
These are derived from the datetime index:
- `hour` – Hour of the day (0–23)
- `day` – Day of the month (1–31)
- `dayofweek` – Day of the week (0 = Monday)
- `month` – Month number (1–12)

### ⏱️ Lag Features
Lagged values of the target variable `Global_active_power` were added:
- `lag_1` – Power consumption 1 hour before
- `lag_24` – Power consumption 24 hours before (same hour previous day)

---

## 🧠 Model

### 🎯 Target Variable
- `Global_active_power`

### 🧮 Final Feature Set
- `hour`, `day`, `dayofweek`, `month`, `lag_1`, `lag_24`

### 🔍 Train-Test Split
- Data was split into training and testing sets to evaluate model performance.

### 🏗️ Model Used
```python
from sklearn.ensemble import RandomForestRegressor
model = RandomForestRegressor(n_estimators=100, random_state=42)
