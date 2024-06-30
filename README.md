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

Data Description
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

