# Movie Gross Revenue Prediction: A Case Study in Multiple Linear Regression

## Overview

This case study explores the relationship between various film attributes and their gross revenue using a multiple linear regression (MLR) model. Given the high-risk nature of modern film production due to increasing budgets, we sought to determine whether specific characteristics of a film can significantly influence its box office performance.

The dataset contains 6,820 films released between 1986 and 2016 and includes attributes such as budget, genre, director, rating, IMDb score, votes, and more.

## Objective

To build and evaluate a multiple linear regression model that predicts a film’s gross revenue based on a variety of predictors, and to assess the model's effectiveness through statistical testing, outlier detection, and prediction intervals.

## Tools and Technologies Used

- **Language:** R  
- **Statistical Techniques:** Multiple Linear Regression, ANOVA, Partial F-tests, Cook’s Distance, Bonferroni Correction  
- **Data Analysis:** Leverage analysis, outlier detection, collinearity, normality testing

## Methodology

### 1. Data Preprocessing

- Removed highly specific categorical variables such as `name`, `director`, `writer`, and `release date` due to their high uniqueness and redundancy.
- Maintained variables with potential predictive value, including `budget`, `genre`, `country`, `rating`, `score`, `votes`, and `year`.

### 2. Model Building

- Created a full model including all predictors.
- Iteratively removed non-significant variables through partial F-tests at a significance level of α = 0.05.
- Final model retained:
  - `budget`
  - `country`
  - `genre`
  - `rating`
  - `score`
  - `votes`
  - `year`

### 3. Model Diagnostics

- **High Leverage Points:** Identified using IQR; a few data points flagged as problematic.
- **Outliers:** Detected using studentized residuals and Bonferroni correction. Multiple outliers found.
- **Influential Observations:** Assessed with Cook’s Distance. No influential points identified.
- **Assumption Checks:**
  - **Homoscedasticity:** Not satisfied; residual plot displayed a cone shape.
  - **Normality:** QQ-plot revealed non-normality.
  - **Collinearity:** High VIF (~104.79) indicated potential multicollinearity.

### 4. Prediction and Evaluation

- Generated prediction intervals for two modern films:
  - **The Batman (2022):** Actual gross ($772M) fell **outside** predicted range.
  - **Everything Everywhere All at Once (2022):** Actual gross ($141M) fell **within** predicted range.
- These results suggest that the model is more reliable for films within the 1986–2016 range and may not generalize well to newer releases due to industry changes.

## Key Findings

- Statistically significant predictors of gross revenue include: `budget`, `country`, `genre`, `rating`, `score`, `votes`, and `year`.
- Several key predictors such as `company`, `star`, and `runtime` were found to be statistically insignificant.
- The model faced issues with assumption violations and data quality (outliers and leverage), limiting its predictive accuracy.
- While useful for exploratory insights and historical trends, the model does not provide accurate point predictions for all films.

## Limitations

- Model assumptions (normality, constant variance) were not fully met.
- Dataset limited to films released between 1986 and 2016.
- External factors such as marketing, franchise status, or inflation were not accounted for.
- High multicollinearity may affect coefficient interpretation.

## Conclusion

This case study demonstrates the process of building and validating a multiple linear regression model in a real-world context. While the model can highlight significant predictors of revenue and provide broad insights, it is not suitable for precise forecasting—particularly for films outside the dataset’s temporal range.

## Future Work

- Explore nonlinear models or machine learning techniques (e.g., random forests, gradient boosting).
- Incorporate more recent data and additional predictors such as streaming metrics or franchise indicators.
- Address model assumptions using transformations or robust regression techniques.

## How to Use

1. Clone this repository to your local machine.
2. Open the R script or notebook provided.
3. Load the dataset and run the script to view model outputs, diagnostics, and prediction intervals.
