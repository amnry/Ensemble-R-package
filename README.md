# simpleEnsemble

> **An R Package for Robust Machine Learning Workflows with Regularized Regression, Bagging, and Ensemble Modeling**  
> Developed as part of a graduate-level course project by Aman Arya and team @ Stony Brook University

![R](https://img.shields.io/badge/Language-R-blue)
![Machine Learning](https://img.shields.io/badge/Focus-Machine%20Learning-brightgreen)
![Status](https://img.shields.io/badge/Stage-Academic%20Project-lightgrey)

---

## 🚀 Overview

**`simpleEnsembleGroup22`** is a comprehensive R package that implements a suite of machine learning models — including **linear, ridge, lasso, and elastic net regressions**, **random forest**, **bagging**, and a **custom ensemble framework** — aimed at solving both regression and classification problems efficiently. It also integrates **feature screening**, **cross-validation**, and **model stacking** to streamline predictive workflows.

Designed with reproducibility and scalability in mind, this package showcases hands-on experience with building production-style ML tools using base R, `glmnet`, and `randomForest`, while embedding statistical reasoning into model choices and preprocessing.

---

## 🔍 Key Features

- 📈 **Regression Models**: Linear, Ridge, Lasso, Elastic Net (with CV and regularization tuning)
- 🌳 **Tree-Based Models**: Random Forest and Bagging with custom sampling controls
- 🧠 **Ensemble Learning**: Combines Elastic Net and Random Forest predictions using a hybrid averaging strategy
- 🔎 **Feature Screening**: Statistical univariate filtering using ANOVA, correlation, Chi-square, Fisher’s test
- ⚙️ **Unified Pipeline**: `simple_ensemble_group_22()` for flexible model + feature selection + ensemble in one call

---

## 📦 Package Structure

| Function Name              | Description                                                                 |
|---------------------------|-----------------------------------------------------------------------------|
| `linear_model()`          | Fits linear or logistic regression depending on the outcome type           |
| `ridge_model()`           | Ridge regression with 10-fold CV to select optimal λ                       |
| `lasso_model()`           | Lasso regression with automated tuning via `glmnet`                        |
| `elastic_net_regression()`| Elastic Net with CV for both α and λ selection                             |
| `rf_model()`              | Random Forest with default mtry and ntree parameters                       |
| `bagged_model()`          | Bootstrapped bagging on base learners                                      |
| `ensemble_predict()`      | Combines Elastic Net and RF predictions via weighted ensemble              |
| `variable_pre_screening()`| Selects top K predictors via univariate filtering/statistical tests        |
| `simple_ensemble_group_22()` | Main entry point: feature selection + bagging + ensemble modeling      |

---

## 📊 Example Use Case

```r
library(MASS)
data(Boston)
X <- Boston[, 2:14]
y <- Boston[, 1]

# Run end-to-end ensemble with feature selection and bagging
results <- simple_ensemble_group_22(
  X, y,
  models = c("elastic_net", "random_forest"),
  r.bagging = 50,
  is.ensemble = TRUE
)
print(results)
