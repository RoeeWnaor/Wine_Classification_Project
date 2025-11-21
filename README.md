# 🍷 Wine Quality Multi-Class Classifier

[![Python](https://img.shields.io/badge/Python-3.x-blue.svg)](https://www.python.org/)
[![Scikit-Learn](https://img.shields.io/badge/Scikit--learn-v1.4-orange.svg)](https://scikit-learn.org/)
[![Status](https://img.shields.io/badge/Status-Completed-success.svg)]()

This project focuses on building an interpretable Machine Learning model to predict the quality score (3-8) of Portuguese Red "Vinho Verde" wine based on physicochemical tests.

---

## 🎯 Goal and Core Challenge

The primary goal was to successfully perform **Multi-Class Classification** despite severe **Class Imbalance** (where scores 5 and 6 dominate the data, and scores 7/8 are rare).

Our strategy centered on **Feature Engineering** to solve this imbalance, rather than relying solely on complex algorithms.

---

## 🚀 Key Strategy: Feature Engineering Success

Based on Exploratory Data Analysis (EDA) and correlation heatmaps, we engineered two critical binary features that became the model's most important predictors:

1.  **`Alcohol_High` (Threshold $\ge 11.5\%$):** A flag indicating the necessary potential for high quality.
2.  **`VA_Low` (Threshold $< 0.55$):** A flag acting as a warning sign against low quality.

### 🥇 Feature Importance Validation

The final Random Forest Model confirmed this strategy, with the engineered features dominating the predictive power:
- **$\mathbf{Alcohol\_High}$**: Accounted for $\mathbf{\approx 30\%}$ of the model's predictive power.
- **$\mathbf{VA\_Low}$**: Accounted for $\mathbf{\approx 13\%}$ of the model's predictive power.

**Together, the two flags provided over 42% of the total decision-making capacity.**

---

## 📊 Model Performance and Limitations

| Metric / Class | Overall Accuracy | F1-Score (Class 7 - Good Wine) | F1-Score (Classes 5 & 6 - Average) |
| :--- | :--- | :--- | :--- |
| **Result** | $\mathbf{75\%}$ | $\mathbf{0.68}$ | $\mathbf{\approx 0.80}$ |

### Constraints:

The model is highly effective for average and good wines but is fundamentally limited: it showed **zero recall** (0.00) for the extremely rare classes (scores 3 and 8) due to insufficient data samples in the testing set. The model should not be used for predicting these extreme endpoints.

---

## 🛠️ Technologies and Dependencies

The project uses the following key libraries:

* **Python 3.x**
* **Pandas** (Data loading and manipulation)
* **NumPy** (Numerical operations)
* **Scikit-learn** (StandardScaler, RandomForestClassifier, Train/Test Split)
* **Matplotlib & Seaborn** (Visualizations)
