# Forecasting Real Estate Prices: Identifying the Top 5 Zip Codes for Investment Using Time Series Analysis

## BY GROUP 1 PHASE 4

Zillow Home Value Index (ZHVI): A measure of the typical home value and market changes across a given region and housing type. It reflects the typical value for homes in the 35th to 65th percentile range. ZHVI is available both as a smoothed, seasonally adjusted measure and as a raw measure.

Zillow publishes:

Top-Tier ZHVI: Typical value for homes within the 65th to 95th percentile range for a given region.
Bottom-Tier ZHVI: Typical value for homes within the 5th to 35th percentile range for a given region.
ZHVI for All Single-Family Residences: Typical value for all single-family homes in a given region.
ZHVI for Condos/Co-ops: Typical value for condos and co-ops.
ZHVI by Bedroom Count: Typical values for homes with 1, 2, 3, 4, and 5+ bedrooms.
ZHVI per Square Foot: Typical value of all homes per square foot, calculated by dividing the estimated home value by the home’s square footage.

## Problem Statement
The investment firm has posed a seemingly straightforward question: "What are the top 5 best zip codes for us to invest in?" However, defining "best" involves addressing several layers of complexity. The firm requires a comprehensive analysis that considers:

Profit Margins: Identifying areas with the highest potential for price appreciation.
Risk: Assessing the volatility and stability of the market in each zip code.
Time Horizon: Determining the appropriate period for investment, whether short-term or long-term.
Our challenge is to forecast future real estate prices accurately and synthesize this information to make well-rounded investment recommendations.

## Main Objective
The main objective of this analysis is to identify the top five zip codes for investment by forecasting future real estate prices using time series modeling. This involves assessing potential profit margins, evaluating associated risks, and determining an appropriate investment time horizon to provide well-rounded, data-driven recommendations to the real estate investment firm.

## Methodology
### Data Preprocessing
Data Cleaning
Data Transformation
### Explorative Data Analysis
Univariate, Bivariate, and Multivariate analysis
Visualization
### Statistical Analysis

### Modeling

Model Selection
Model Training and Validation
Model Evaluation
### Forecasting and Results Interpretation

Forecast Future Values
Interpret Results
### Model Deployment

Create a Deployment Pipeline
Infrastructure Setup
Monitoring and Maintenance

## Data Description
The dataset used for this project was downloaded from a GitHub repository, which originally sourced the data from Zillow housing data. The dataset spans from April 1996 to April 2018 and provides detailed monthly home value data for a wide range of regions across the United States.

The dataset has 14,723 rows and 272 columns. The information contained within the columns is as follows, as described by the data dictionary:

`RegionID` A unique identifier for the region.\
`RegionName` A numerical code representing the region (e.g., ZIP code).\
`City` The city name.\
`State` The state abbreviation.\
`Metro` The metropolitan area name.\
`CountyName` The county name.\
`SizeRank` The size rank of the region, with 1 being the largest in terms of population or housing market.\
`Monthly Home Values`: The columns labeled with dates (e.g., "1996-04", "1996-05", etc.) represent the Zillow Home Value Index for that region in those specific months. These values are typically the median home values and are given in dollars. This ranges from April 1996 to April 2018.

## STATIONARITY TESTING
### Principal Component Analysis (PCA)
PC1 explains approximately 56.14% of the total variance.
PC2 explains approximately 43.86% of the total variance.

image(PCA)
### Clustering
Cluster 0: Contains 1,833,613 data points. Cluster 1: Contains 1,765,222 data points. Cluster 2: Contains 149,205 data points. 
Interpretation: Cluster Distribution: The clustering has resulted in three distinct clusters labeled as Cluster 0, Cluster 1, and Cluster 2.

Image(Clustering)

### AD-Fuller Test
ZIP Code 1: Original Data: ADF Statistic: 1.9884 p-value: 0.9987 (Non-stationary) Log and Differenced Data: ADF Statistic: -2.8492 p-value: 0.0516 (Stationary at 5% significance level)

ZIP Code 2: Original Data: ADF Statistic: 1.0244 p-value: 0.9945 (Non-stationary) Log and Differenced Data: ADF Statistic: -2.7422 p-value: 0.0670 (Stationary at 10% significance level)

ZIP Code 3: Original Data: ADF Statistic: 0.2032 p-value: 0.9724 (Non-stationary) Log and Differenced Data: ADF Statistic: -2.2586 p-value: 0.1857 (Non-stationary)

ZIP Code 4: Original Data: ADF Statistic: -0.5499 p-value: 0.8819 (Non-stationary) Log and Differenced Data: ADF Statistic: -1.8203 p-value: 0.3704 (Non-stationary)

ZIP Code 5: Original Data: ADF Statistic: 0.4646 p-value: 0.9838 (Non-stationary) Log and Differenced Data: ADF Statistic: -2.7473 p-value: 0.0662 (Stationary at 10% significance level)

For the Dickey-Fuller test, the null hypothesis is that the time series data is non-stationary. A lower p-value (typically less than 0.05) indicates that you can reject the null hypothesis and infer stationarity. In cases where the p-value is higher, the data is likely non-stationary.

Based on these results:

ZIP Code 1 and ZIP Code 5 show evidence of stationarity after logarithmic transformation and differencing. ZIP Code 2 shows potential stationarity at a higher significance level (10%). ZIP Code 3, ZIP Code 4, and the original forms of ZIP Code 2 do not show evidence of stationarity based on the tests conducted.

## MODELLING
### ARIMA MODEL

Image(ARIMA)

Interpretation:

Model Coefficients: AR(1) and MA(1) coefficients are statistically significant (p < 0.05) across all ZIP codes, indicating they contribute significantly to the model.

Goodness of Fit: Generally, the models have high log likelihood values and low AIC/BIC values, suggesting good model fit. Accuracy Metrics:

The MAE, MSE, and RMSE provide measures of prediction accuracy, with lower values indicating better performance.

These summaries suggest that the ARIMA(1, 1, 1) models fitted to the log-transformed and differenced data provide reasonable fits for predicting housing prices in each ZIP code. Further analysis could involve diagnostic checks for residuals and potentially exploring other model variations to optimize forecasting accuracy further.

### SARIMAX
All models have statistically significant coefficients (low p-values).

Zip3 and Zip4 have the highest Log Likelihood values, suggesting they might be the best-fitting models among the five.

Zip1, Zip2, Zip4 and Zip5 have Ljung-Box tests with significant p-values, indicating a potential issue with normality of residuals.

All models show signs of heteroskedasticity based on the prob(H) values.

Zip5 has the lowest MAE and RMSE on the test set, indicating the best forecasting performance.

## Recommendations
1. EDA based recommendations:
   
   a. Focus on High-ROI States and Regions\
Recommendation: Prioritize investments in regions with historically high Annualized ROI. States like the District of Columbia (DC), and specific zip codes such as 11211 in New York (Brooklyn), have shown consistently high returns.
Action: Allocate a significant portion of your investment portfolio to properties within these high-ROI areas. Conduct further detailed analysis on these regions to identify the best-performing properties and neighborhoods.

   b. Manage Risk by Diversifying Investments\
Recommendation: Diversify your investments across multiple regions and property types to mitigate risk. While high-ROI areas are attractive, it's crucial to balance the portfolio to avoid overexposure to any single market.
Action: Create a diversified portfolio by investing in a mix of high-ROI regions and more stable markets with moderate ROI. This strategy will help in reducing the overall risk while maintaining potential for high returns.

   c. Address and Leverage Outliers\
Recommendation: Investigate and understand the characteristics of outlier properties. Properties with exceptionally high prices or ROI might indicate unique opportunities or potential risks.
Action: Conduct a detailed analysis of outlier properties to determine the factors driving their high prices or ROI. Identify whether these properties offer unique investment opportunities due to location, property features, or market trends. Consider including a few outliers in the portfolio if they align with your investment strategy and risk tolerance.

2. Based on the findings from the forecasted values:
   
   Zip code 1: 11211 (New York, Kings):
Shows a steady increase in housing prices, indicating a strong growth trend. Recommendation: This zip code appears promising for investment due to its consistent upward trajectory in housing prices.

   Zip code 2: 11222 (New York, Kings):
Also demonstrates steady growth, though slightly slower compared to 11211. Recommendation: Consider 11222 as a viable option for investment, especially for those looking for stable growth in housing prices.

   Zip code 3: 11216 (New York, Kings):
Similar to 11211 and 11222, showing a consistent increase in housing prices over time. Recommendation: This zip code presents opportunities for investment due to its favorable growth pattern.

   Zip code 4: 07302 (Jersey City, Hudson):
Displays a noticeable growth trajectory in housing prices. Recommendation: Jersey City's 07302 zip code is worth considering for investment, given its strong growth potential.

   Zip code 5: 11215 (New York, Kings):
Shows moderate and stable growth in housing prices. Recommendation: While growth is steady, investors seeking more rapid appreciation might look towards other zip codes with higher growth rates.

## Conclusions
The 5 Zip codes exhibit strong potential for investment based on their consistent and noticeable growth in housing prices. Apart from New York, Kings which offers stability but with slower growth compared to the others, making it suitable for investors preferring a more conservative approach.

## Group Members
[Caleb Kenyatta](https://github.com/CarlAK96)\
[Sonia Ojay](https://github.com/soniaojay)\
[Shuru Ebale](https://github.com/shuruebale)\
[Magdalene Ondimu](https://github.com/magdaondimu)\
[Yvonne Mwangi](https://github.com/KirigoY)\
[Joseph Karumba](https://github.com)
