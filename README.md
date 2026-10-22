# Bengaluru House Price Prediction

![Python](https://img.shields.io/badge/Python-3-3776AB?logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Notebook-Jupyter-F37626?logo=jupyter&logoColor=white)
![scikit-learn](https://img.shields.io/badge/ML-scikit--learn-F7931E?logo=scikitlearn&logoColor=white)
![pandas](https://img.shields.io/badge/Data-pandas-150458?logo=pandas&logoColor=white)

A multiple linear regression project that predicts residential property prices in Bengaluru from area, room count, bathrooms, balconies, and area type.

## Overview

The notebook uses a real Kaggle housing dataset for Bengaluru and walks through cleaning, feature engineering, visualisation, model training, and evaluation. It is an introductory regression exercise: the goal is to understand the workflow and the limits of a simple linear model on noisy property data, not to produce a valuation product.

## Dataset

| Item | Value |
|---|---|
| Source | [Kaggle — Bengaluru House Price Data](https://www.kaggle.com/datasets/amitabhajoy/bengaluru-house-price-data) |
| File | `Bengaluru_House_Data.csv` |
| Rows | 13,320 |
| Columns | 9 |
| Target | `price` (in lakhs of INR) |
| Raw features | `area_type`, `availability`, `location`, `size`, `society`, `total_sqft`, `bath`, `balcony` |

## Method

The notebook has seven cells:

1. **Load and inspect** the CSV in Colab; preview the first rows.
2. **Clean**
   - Drop `society` and `availability` (sparse/low-value for this exercise).
   - Fill missing `bath` with the median and `balcony` with `0`.
   - Drop remaining rows with nulls.
3. **Feature engineering**
   - Extract the numeric BHK value from `size` (for example, `"2 BHK"` → `2`).
   - Convert `total_sqft` ranges such as `"1200-1500"` to their mean; convert non-numeric values to `NaN` and drop them.
4. **Visualise**
   - price distribution
   - price-per-square-foot distribution
   - price variation by BHK
5. **Encode** `area_type` with one-hot encoding (`drop_first=True`).
6. **Model** with `LinearRegression` on an 80/20 train/test split (`random_state=1`).
7. **Evaluate** with R², MAE, and MSE, then plot actual vs predicted prices.

### Feature Set

```text
total_sqft, bath, balcony, bhk, area_type dummies
```

## Results

| Metric | Value |
|---|---:|
| Test R² | **0.47** |
| MAE | **45.06 lakhs** |
| MSE | **12,035.51** |

An R² of 0.47 means the linear model explains roughly 47% of the variance in the held-out prices. The large MAE reflects strong outliers, location effects that are not represented in the feature set, and the simplicity of the model.

## Getting Started

### Google Colab

1. Open `banglore_house_price_.ipynb` in Colab.
2. Run the first cell and upload `Bengaluru_House_Data.csv`.
3. Run the remaining cells to reproduce the charts and metrics.

### Local Jupyter

```bash
python -m venv .venv
# Windows
.venv\Scripts\activate
# Linux/macOS
source .venv/bin/activate

pip install pandas numpy matplotlib seaborn plotly scikit-learn jupyter
jupyter notebook banglore_house_price_.ipynb
```

Skip the `google.colab.files.upload()` cell and ensure the CSV filename in `pd.read_csv()` matches the local file.

## Project Structure

```text
Banglore-price-prediction/
├── banglore_house_price_.ipynb     # 7-cell notebook
├── Bengaluru_House_Data.csv        # Raw dataset (13,320 × 9)
├── screenshots/                    # Exported notebook figures
└── README.md
```

## Notes and Limitations

- **Location is not used.** `location` is high-cardinality and was not encoded; this is a major source of unexplained price variation.
- **Outliers remain.** No price-per-square-foot outlier filtering or luxury-property handling is applied.
- **`price_per_sqft` is not correct as written.** The notebook computes `df["price_per_sqft"] = df["price"] * 100000`, which omits division by `total_sqft`. The column is used only for a distribution plot and is not part of the model.
- **Random train/test split:** appropriate for a first look, but spatial or grouped splits would better test generalisation across locations.
- **Linear assumptions:** the model cannot capture non-linear effects or interactions between area, BHK, and location.
- **No cross-validation or hyperparameter tuning.**
- The metrics are specific to this split (`random_state=1`) and should not be read as production accuracy.

## Data Credit

Dataset published on Kaggle by **Amitabh Ajoy**. Refer to the Kaggle page for licensing and usage terms.

## Author

**Atul Anand**  
B.Tech–M.Tech (Cyber Security), National Forensic Sciences University  
GitHub: [@Atul2512anand](https://github.com/Atul2512anand)
