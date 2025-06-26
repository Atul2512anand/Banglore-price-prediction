# 🏠 Bengaluru House Price Prediction – Linear Regression (Task 3)

This project implements **Simple and Multiple Linear Regression** using a real-world **Indian dataset** — housing data from **Bengaluru, India**. It explores relationships between house features (like size, number of bathrooms, BHK, area type) and price using visualizations and predictive modeling.

---

## 🎯 Objective

To build a **Linear Regression model** that predicts **house prices (in Lakhs INR)** based on features such as:

- Total square footage
- Number of bedrooms (BHK)
- Bathrooms
- Balcony
- Area type (Built-up, Super Built-up, etc.)

---

## 📁 Dataset

- **Source**: [Kaggle – Bengaluru House Price Data](https://www.kaggle.com/datasets/amitabhajoy/bengaluru-house-price-data)
- **File**: `Bengaluru_House_Data.csv`
- **Target**: `price` (in Lakhs)

---

## 🧰 Tools & Libraries

- `Pandas`, `NumPy` – data loading & cleaning
- `Matplotlib`, `Seaborn`, `Plotly` – visualizations
- `Scikit-learn` – regression model, evaluation

---

## 🔧 Steps Performed

### 📌 1. Data Cleaning
- Removed missing values and unimportant columns (`society`, `availability`)
- Handled inconsistent formats in `total_sqft` (converted ranges to mean)
- Extracted `BHK` from the `size` column

### 📊 2. Data Visualization

- **Price Distribution**

  ![Price Histogram](screenshots/price_distribution.png)

- **Boxplot: Price vs BHK**

  ![BHK Boxplot](screenshots/price_vs_bhk.png)

- **Scatter Plot: Actual vs Predicted Price**

  ![Actual vs Predicted](screenshots/prediction_scatter.png)

### 🧠 3. Feature Engineering

- Created `price_per_sqft` as a derived feature
- One-hot encoded `area_type`

### 📈 4. Linear Regression

- Split data into training and test sets (80/20)
- Trained a `LinearRegression()` model using `scikit-learn`
- Evaluated using:
  - MAE (Mean Absolute Error)
  - MSE (Mean Squared Error)
  - R² Score (Goodness of Fit)

---

## 📊 Model Evaluation

|
| Metric | Value |
|--------|-------|
| **R² Score** | ~0.65 |
| **MAE** | ~12 Lakhs |
| **MSE** | Moderate |
| **Target** | Continuous numeric (price in Lakhs) |

---

## 🔍 Key Inferences

- More **square footage** generally leads to higher price.
- **BHK** and **bathrooms** contribute positively, but not always linearly.
- **Area type** influences pricing (built-up and super built-up areas cost more).
- Strong multicollinearity between features like `total_sqft`, `BHK`, and `price`.

---

## 💡 Real-World Relevance

This model can help:
- Real estate businesses price homes
- Buyers assess price fairness
- Developers identify key pricing drivers

---

## 📂 Project Structure
Task-3-LinearRegression/
├── Bengaluru_House_Data.csv
├── Linear_Regression_Housing.ipynb
├── README.md
└── screenshots/
├── price_distribution.png
├── price_vs_bhk.png
├── prediction_scatter.png

yaml
Copy
Edit

---

## 🚀 How to Run

1. Upload `Bengaluru_House_Data.csv` into Google Colab.
2. Run all cells in `Linear_Regression_Housing.ipynb`.
3. View the predictions, graphs, and evaluation metrics.

---

## 📌 Status

> ✅ Task 3 Completed: Linear Regression  
> 🔜 Task 4 (Optional): Polynomial Regression or ML Classification

---

## 👨‍💻 Author

Made by **Atul Anand**  
B.Tech–M.Tech (Cyber Security), National Forensic Sciences University  