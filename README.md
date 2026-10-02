# Predictive Insight Engine

A supervised learning project for estimating residential house prices from property characteristics. The work follows the provided six-hour brief and is implemented in `house_price_analysis.ipynb`.

## What is included

- A short explanation of supervised learning, regression and classification, linear regression assumptions, bias-variance, overfitting and underfitting.
- Dataset inspection, missing-value checks, descriptive statistics and relationship plots.
- A train/test split with a fixed random seed so the results can be reproduced.
- Simple linear regression using `area_sqft`.
- Multiple linear regression using all available predictors except `house_id`.
- Polynomial regression for degree 2 and degree 3.
- MSE, MAE, RMSE, R-squared and adjusted R-squared comparisons.
- Batch, stochastic and mini-batch gradient descent implemented from scratch.
- A small learning-rate experiment and a train/test error view for model complexity.
- A final comparison table and a plain-language business interpretation.

## Dataset

The supplied file is:

`RealEstate_HousePrice_Dataset_4200 - RealEstate_HousePrice_Dataset_4200.csv.csv`

It contains 4,200 properties and these columns:

- `house_id`: record identifier, not a predictive feature
- `area_sqft`, `bedrooms`, `bathrooms`, `location_score`, `age_years`
- `distance_city_km`, `lot_size_sqft`, `has_garage`, `has_pool`, `renovation_years_ago`
- `house_price_inr`: target price in Indian rupees

The notebook loads the CSV from the same folder as itself. Keep the original filename unchanged, or update the `DATA_PATH` value in the first code section.

## Running the project

1. Open this folder in VS Code.
2. Create or select a Python 3.10+ environment.
3. Install the dependencies:

   ```bash
   python -m pip install -r requirements.txt
   ```

4. Open `house_price_analysis.ipynb` and run all cells from top to bottom.
5. Read the printed comparison table and the final notes after the plots. The exact scores are produced from the local CSV, so they should not be copied from an unrelated run.

The notebook uses `scikit-learn` for the reference regression models and metrics. The three gradient descent optimizers are written in the notebook so their update rules are visible and easy to explain in a recording.

## Notes on the modeling choices

`house_id` is removed because it is only an identifier. Binary columns are already represented as 0/1 values, so they can be used directly. Numerical predictors are standardized for polynomial regression and gradient descent; this keeps large-valued columns such as lot size from dominating the optimization steps. The final evaluation is always reported in the original price units where that is useful for interpretation.

A high training score by itself is not treated as success. The comparison focuses on the test metrics and on the gap between training and testing performance. That makes it easier to spot an unnecessarily complex polynomial model or a gradient descent run that has not converged.

## Suggested submission files

- `house_price_analysis.ipynb`
- The supplied CSV file
- `README.md`
- A PDF export of the notebook if required by the course
- Screenshots or a short recording showing the notebook being run

## Limitations

This is an educational model, not a property valuation service. The dataset may not represent every neighborhood or market condition, and correlation in this sample should not be read as proof of causation. A production system would need stronger validation, monitoring, outlier review and regularly updated market data.
