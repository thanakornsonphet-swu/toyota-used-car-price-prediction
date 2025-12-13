# Toyota Used Car Price Prediction Project

   

## 📄 Project Overview

**SWU Motors**, a growing used car dealership, is facing a critical business problem: **Sales have dropped by 18%** due to pricing errors committed by inexperienced junior sales staff.

This Data Science project aims to develop a **"Pricing Assistant Tool"** using Machine Learning to predict the fair market value of used Toyota cars. The goal is to standardize pricing, minimize human error, and recover lost profit margins.

### Objective

  * Build a predictive model with a Root Mean Squared Error (**RMSE**) of **less than £1,250**.
  * Identify key factors influencing used car prices to guide the purchasing team.

-----

## Dataset

The dataset contains **6,738 records** of Toyota used car sales in the UK market.

  * **Source:** `toyota.csv`
  * **Target Variable:** `price` (£)
  * **Features:**
      * `model`: Car model (e.g., GT86, Yaris, Supra)
      * `year`: Registration year
      * `transmission`: Gearbox type (Manual, Automatic, Semi-Auto)
      * `mileage`: Distance driven (miles)
      * `fuelType`: Petrol, Diesel, Hybrid, Other
      * `tax`: Road tax (£)
      * `mpg`: Miles per gallon
      * `engineSize`: Engine capacity (Litres)

-----

## Methodology

We followed an end-to-end Data Science workflow:

1.  **Data Analytics (Excel & Tableau):**

      * Discovered a **Right-Skewed Market** (Skewness 1.82), indicating most cars are budget-friendly, with a few high-value outliers (Supra, Land Cruiser).
      * Identified **High Volatility** in prices (SD \~£6,345), confirming the difficulty for humans to price manually.
      * **Key Insight:** "Engine Size" is the strongest predictor of price segmentation.

2.  **Data Preprocessing (Python):**

      * **Categorical Encoding:** `OneHotEncoder` for Model, Transmission, FuelType.
      * **Feature Scaling:** `StandardScaler` for numerical features (Mileage, Tax, MPG).
      * **Split:** 80% Training / 20% Testing.

3.  **Machine Learning Modeling:**

      * **Phase 1 (Baseline):** Tested Linear Models (Ridge, Lasso, Elastic Net).
      * **Phase 2 (Challenger):** Implemented **Random Forest Regressor** to capture non-linear depreciation patterns.

-----

## Model Performance

We compared the baseline Linear Model against the Random Forest model.

| Model | RMSE (Lower is Better) | Accuracy ($R^2$) | Result |
| :--- | :--- | :--- | :--- |
| **Linear Model (Lasso)** | £1,680.24 | 93.0% | ❌ **FAILED** (\> £1,250) |
| **Random Forest** | **£1,102.96** | **97.0%** | ✅ **PASSED** (\< £1,250) |

> **Conclusion:** The Random Forest model successfully met the business criteria, reducing the error margin by **\~34%** compared to the linear approach.

-----

## Business Recommendations

Based on the model's success, we recommend the following actions for SWU Motors:

1.  **Deploy the "Pricing Assistant":** Integrate the Random Forest model into the sales system to provide instant fair price recommendations.
2.  **Smart Buying with "Deal Analyzer":** Use the model to identify **"Undervalued"** cars (where Predicted Price \> Selling Price) to acquire high-margin inventory.
3.  **Focus on Engine Size:** Procurement teams should prioritize high-engine-capacity vehicles (SUVs/Sports) as they hold value better than standard eco-cars.
