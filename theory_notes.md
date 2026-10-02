# Supervised Learning Theory Notes

## Supervised learning

Supervised learning uses examples that contain both input variables and a known output. A model learns a mapping from the inputs to the output and is then tested on examples it did not see during training. In this project the inputs describe a house and the output is its recorded price.

## Regression and classification

Regression predicts a numeric value, such as a house price, temperature or sales amount. Classification predicts a label or class, such as whether a house is likely to sell quickly. Since price is numeric, this project is a regression problem.

## Simple linear regression

Simple linear regression describes one input with a straight line:

`y_hat = b0 + b1 x`

`b0` is the intercept and `b1` is the slope. Here, the slope estimates the average change in price associated with one extra square foot of area, while the other property differences remain part of the unexplained error.

## Assumptions of linear regression

1. The relationship between predictors and the target is approximately linear.
2. Each observation is independent of the others.
3. The error spread is reasonably constant across the prediction range.
4. The data does not contain a small number of extreme outliers that controls the fitted line.
5. Predictors in a multiple model are not so redundant that the coefficients become unstable.
6. Residual normality is mainly important when making statistical inference, rather than simply producing predictions.

## Bias and variance

Bias is error caused by a model being too simple to represent the real pattern. Variance is error caused by a model reacting too strongly to the particular training sample. A good model balances both: it captures the useful signal while still generalizing to new houses.

## Overfitting and underfitting

A polynomial model that has a very low training error but a much higher testing error is overfitting. It has learned details that do not transfer to unseen properties. A model with poor training and testing scores is underfitting because it is not flexible enough to capture the relationship. Comparing train and test results helps distinguish these cases.

## Evaluation metrics

- **MSE:** average squared error. Large mistakes receive extra weight.
- **MAE:** average absolute error. It is easy to explain as a typical error in rupees.
- **RMSE:** square root of MSE. It is also expressed in rupees and emphasizes larger misses.
- **R-squared:** proportion of target variation explained by the model.
- **Adjusted R-squared:** an R-squared variant that penalizes adding predictors that do not provide enough improvement.

No single metric tells the whole story. In this project, test RMSE, test MAE, R-squared, and the train/test gap are considered together.

## Gradient descent

Gradient descent starts with parameter values and repeatedly moves them in the direction that reduces the loss. The learning rate controls the size of each update. Batch gradient descent uses every training row per update, stochastic gradient descent uses one row, and mini-batch gradient descent uses a small group of rows. Standardizing the predictors makes these updates more stable because one large-valued feature cannot dominate the gradient only because of its units.
