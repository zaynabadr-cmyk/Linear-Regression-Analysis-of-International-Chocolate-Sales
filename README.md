# Modeling Global Chocolate Sales Using Linear Regression Techniques

STAT 423 final project, University of Washington.
Team: Fiona Vo, Srinidhi Muralidharan, Zayna Badr

## Overview
This project analyzes 3,013 global chocolate sales transactions (2022-2024) to identify which factors drive revenue per sale, and builds a multivariable linear regression model in R to explain and predict it.

## Data
- Source: Kaggle global chocolate sales dataset [add link]
- 3,013 transactions, 5 variables: Date, Product (22 types), Country (6 countries), Boxes Shipped, Amount (USD)
- Response: square root of Amount, which fixed the right skew
- The raw `chocolate.csv` is not included. Download it from Kaggle and place it in the same folder as the Rmd file.

## Methods
- Exploratory analysis of sales by year, month, country, and product
- Single-predictor models, then forward, backward, and bidirectional stepwise selection (AIC)
- Interaction terms tested with ANOVA, final model chosen using adjusted R², AIC, and BIC
- Diagnostics: residual plots, QQ plot, VIF, Cook's distance
- `price_per_box` was excluded from the final model because it is calculated from the response (Amount / Boxes.Shipped)

## Key Findings
- Product and Year were the significant individual predictors. Country and Boxes.Shipped became significant only through interactions, especially with Product.
- Final model: sqrt(Amount) ~ Product + Year + Product:Boxes.Shipped + Product:Country + Product:Year + Country:Boxes.Shipped
- Explanatory power is low (adjusted R² of about 0.072), so variables not in the dataset likely influence sales.
- Model assumptions looked reasonable: no clear pattern in residuals, approximately normal QQ plot, VIF near 1, and no highly influential points.
- A model fit only to Australian transactions had a higher adjusted R² (0.103), suggesting country-specific models are worth exploring.

## Limitations
The data cover only January-August in 2024, only one numeric predictor is available, and explanatory power is low.

## Files
- `Final_Project.pdf`: final report
- `Final_Project.Rmd`: R Markdown source

## How to Reproduce
1. Download `chocolate.csv` from Kaggle into the repo folder
2. Install packages: `install.packages(c("ggplot2", "car", "dplyr"))`
3. Open the Rmd in RStudio and click **Knit**

## Author
Zayna Badr, University of Washington
