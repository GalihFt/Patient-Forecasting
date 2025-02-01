# Inpatient Admission Analysis

This project focuses on analyzing inpatient admissions using time series methods. The dataset consists of hospital inpatient admission records from **July 3, 2022, to November 10, 2023**. To maintain institutional confidentiality, the dataset has been modified while preserving its key characteristics.

## Key Features
* **Exploratory Data Analysis (EDA)** on inpatient admissions
* **Feature extraction and statistical analysis**
* **Time Series Modeling using SARIMA**
* **Model evaluation using RMSE and MAPE**
* **Forecasting inpatient admissions**

## Steps Overview

### 1. Dataset Preparation
* The dataset contains **inpatient admissions** from **07/03/2022 to 10/11/2023**.
* The dataset is split into **train (historical data) and test (forecasting data)** subsets.

### 2. Data Preprocessing
* Data is cleaned and structured to ensure consistency.
* **Box-Cox transformation** is applied to stabilize variance.
* Data is converted into a **time series format** with a weekly seasonality factor.

### 3. Exploratory Data Analysis
* **Descriptive statistics** (mean, median, min, max) are computed.
* **Daily patient arrivals** are analyzed to observe weekday trends.
* **Time series visualization** is conducted to inspect seasonal patterns.

### 4. Stationarity Check
* **Box-Cox transformation** is applied to address variance stationarity.
* **Autocorrelation Function (ACF) and Partial Autocorrelation Function (PACF)** plots are analyzed to determine stationarity in the mean.
* **Seasonal differencing** is applied to make the data stationary.

### 5. Model Diagnostics
* **Conditional Least Squares (CLS)** method is used for parameter estimation.
* **Ljung-Box test** is performed to assess residual randomness.
* **Lilliefors test** is used to check residual normality.

### 6. Model Evaluation
* The best model is selected based on:
  * **Root Mean Square Error (RMSE)**
  * **Mean Absolute Percentage Error (MAPE)**
* The evaluation is conducted on **test data from December 11, 2023, to January 7, 2024**.

### 7. Forecasting
* Forecasts are generated using the best SARIMA model.
* The forecasted values are plotted against actual values.
* Confidence intervals are included in the visualization to measure uncertainty.

## Files in This Repository

This repository contains the following files:

- **`Data/`**: Contains the dataset used for analysis.
- **`Image/`**: Contains images used in the analysis, such as Box-Cox transformation and time series visualizations.
- **`Analysis of Inpatient Admissions.pdf`**: A PDF report summarizing the entire analysis, including methodology, results, and conclusions.
- **`Inpatient_Analysis.Rmd`**: The R Markdown file containing the complete script for data preprocessing, analysis, modeling, and forecasting.
- **`Inpatient_Analysis.html`**: The HTML output generated from the R Markdown file, providing an interactive view of the analysis.

## Conclusion
The following table summarizes the model evaluation results:

| Model          | RMSE  | MAPE  |
|--------------|------|------|
| SARIMA(0,0,2)(0,1,1)7 | 28.57020 | 22.19397 |
| SARIMA(0,0,2)(1,1,1)7 | 28.99893 | 22.02917 |
| SARIMA(0,0,[2])(0,1,1)7 | Does not satisfy white noise assumption | |

Based on the results, **SARIMA(0,0,2)(0,1,1)7 was the best-performing model**, as it had the smallest forecasting error with RMSE in the data test 28.57020 and MAPE 22%. The model effectively captures the seasonal pattern observed in inpatient admissions. The forecasting plot demonstrates that the predicted values align closely with actual values, and the confidence interval encompasses the majority of actual values, indicating a reliable uncertainty estimation.

This study highlights the importance of **time series modeling in healthcare forecasting** and provides insights into **seasonal trends in inpatient admissions**. **Future improvements will focus on enhancing model performance, testing alternative forecasting techniques, and incorporating external factors such as hospital policies and public health trends.**

