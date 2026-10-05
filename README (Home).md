# Predictive Insight Engine: House Price Estimation

A machine-learning project for estimating house prices in INR using property characteristics. The project compares simple linear regression, multiple linear regression, polynomial regression, and gradient-descent optimization methods.

## Project Overview

This project uses a real-estate dataset containing 4,200 property records and 12 columns. The target variable is `house_price_inr`.

### Main Questions

- How do property variables relate to house price?
- Does using multiple property features improve predictions compared with using area alone?
- Does polynomial regression improve the fit, or does it introduce overfitting?
- How do batch, stochastic, and mini-batch gradient descent compare?

## Dataset

**Dataset:** `RealEstate_HousePrice_Dataset_4200 - RealEstate_HousePrice_Dataset_4200.csv.csv`

- Rows: **4,200**
- Columns: **12**
- Target: `house_price_inr`
- Identifier: `house_id` — excluded from model features

### Features

| Feature | Description |
|---|---|
| `area_sqft` | House area in square feet |
| `bedrooms` | Number of bedrooms |
| `bathrooms` | Number of bathrooms |
| `location_score` | Location quality score |
| `age_years` | Property age in years |
| `distance_city_km` | Distance from the city in kilometres |
| `lot_size_sqft` | Lot size in square feet |
| `has_garage` | Garage indicator |
| `has_pool` | Pool indicator |
| `renovation_years_ago` | Years since renovation |
| `house_price_inr` | Target house price in INR |

`house_id` is not used as a predictor because its numeric value does not describe the property.

## Project Structure

```text
.
├── house_price_analysis.ipynb
├── RealEstate_HousePrice_Dataset_4200 - RealEstate_HousePrice_Dataset_4200.csv.csv
├── requirements.txt
└── README.md
```

## Methods Used

### 1. Exploratory Data Analysis

The notebook checks:

- Dataset dimensions and data types
- Descriptive statistics
- Missing values
- Price distribution
- Relationship between area and price
- Correlation between numerical variables

### 2. Simple Linear Regression

The first model uses only `area_sqft` to predict `house_price_inr`.

The model is:

```text
y_hat = b0 + b1 * area_sqft
```

The slope describes the expected change in predicted price for a one-unit increase in area, while the intercept is the model's predicted value when area is zero.

### 3. Multiple Linear Regression

The second model uses all property features except `house_id` and `house_price_inr`.

This allows the model to use information such as:

- Area
- Bedrooms
- Bathrooms
- Location score
- Property age
- Distance from city
- Lot size
- Garage availability
- Pool availability
- Renovation age

### 4. Polynomial Regression

Polynomial regression is tested at degrees **2 and 3** and later degrees **1 through 4** for a model-complexity check.

The polynomial models use:

- `PolynomialFeatures`
- `StandardScaler`
- `LinearRegression`

A large difference between training and test performance is treated as a warning sign for overfitting.

### 5. Gradient Descent

Gradient descent is implemented from scratch after standardizing the predictors.

Three optimization approaches are compared:

- **Batch gradient descent** — uses the complete training dataset for each update.
- **Stochastic gradient descent (SGD)** — uses one randomly selected observation per update.
- **Mini-batch gradient descent** — uses small batches of observations.

The loss function is mean squared error (MSE).

## Train/Test Split

The data is split into:

- **80% training data**
- **20% testing data**

`random_state=42` is used for reproducibility.

## Evaluation Metrics

The project evaluates regression models using:

- **MSE (Mean Squared Error):** squares prediction errors and therefore emphasizes large errors.
- **MAE (Mean Absolute Error):** average absolute prediction error, expressed in the target's units.
- **RMSE (Root Mean Squared Error):** square root of MSE and expressed in INR.
- **R² (R-squared):** proportion of target variation explained by the model.
- **Adjusted R²:** adjusts R² for the number of predictors.

The notebook also compares training and testing R² to help identify possible overfitting.

## Installation

Create and activate a Python environment, then install the required packages:

```bash
pip install -r requirements.txt
```

The project requires:

- NumPy
- Pandas
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter

## How to Run

1. Place the notebook and CSV dataset in the same directory.
2. Install the dependencies:

```bash
pip install -r requirements.txt
```

3. Start Jupyter Notebook:

```bash
jupyter notebook
```

4. Open:

```text
house_price_analysis.ipynb
```

5. Run the notebook cells from top to bottom.

## Reproducibility

The project uses `RANDOM_STATE = 42` for the train/test split and gradient-descent random operations.

The notebook expects the CSV file to have the exact filename:

```text
RealEstate_HousePrice_Dataset_4200 - RealEstate_HousePrice_Dataset_4200.csv.csv
```

## Key Concepts Demonstrated

This project demonstrates practical understanding of:

- Supervised learning
- Regression
- Exploratory data analysis
- Simple and multiple linear regression
- Polynomial regression
- Bias and variance
- Overfitting and underfitting
- Model evaluation
- Feature scaling
- Batch gradient descent
- Stochastic gradient descent
- Mini-batch gradient descent
- Training vs. testing performance

## Limitations

- The project evaluates the models using a single train/test split.
- No cross-validation or hyperparameter search is included.
- Polynomial models can become computationally expensive as degree increases because the number of generated features grows.
- A strong predictive relationship should not automatically be interpreted as a causal relationship.
- The simple linear model intentionally uses only house area, so other property differences are not controlled for.

## Files

- **`house_price_analysis.ipynb`** — complete analysis, visualizations, model training, comparison, and gradient-descent implementation.
- **`RealEstate_HousePrice_Dataset_4200 - RealEstate_HousePrice_Dataset_4200.csv.csv`** — real-estate dataset used by the notebook.
- **`requirements.txt`** — Python package requirements.
- **`README.md`** — project documentation.
