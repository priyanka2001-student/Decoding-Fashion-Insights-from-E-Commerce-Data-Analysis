# Decoding Fashion: Insights from E-commerce Data Analysis

## Table of Contents
1. [Overview](#overview)
2. [Dataset Details](#dataset-details)
3. [Analysis Overview](#analysis-overview)
   - [1. Data Cleaning and Preprocessing](#1-data-cleaning-and-preprocessing)
   - [2. Funnel Analysis](#2-funnel-analysis)
   - [3. Exploratory Data Analysis (EDA)](#3-exploratory-data-analysis-eda)
   - [4. Feature Engineering](#4-feature-engineering)
   - [5. Statistical Analysis](#5-statistical-analysis)
   - [6. Clustering and Segmentation Analysis](#6-clustering-and-segmentation-analysis)
   - [7. Market Basket Analysis](#7-market-basket-analysis)
   - [8. Cohort Analysis](#8-cohort-analysis)
4. [Conclusion](#conclusion)


## Overview

Analyzed e-commerce fashion data to enhance customer engagement. Performed data cleaning, exploratory analysis, and funnel analysis to track customer journeys. Used statistical tests and clustering for segmentation, along with market basket analysis to identify purchasing patterns and cohort analysis for retention insights.

## Dataset Details
- **Size**: 1000 columns, 50 rows
- **The dataset `FASHION_DATA.xlsx` contains the following columns**:
  - **ID**: Unique identifier for each entry
  - **Consumer ID**: Unique identifier for each consumer
  - **Gender**: Gender of the consumer (e.g., Male, Female)
  - **Age Group**: Age range of the consumer (e.g., 18-24, 25-34)
  - **Income ($)**: Annual income of the consumer
  - **Occupation**: Job title of the consumer (e.g., Student, Engineer)
  - **Preferred Style**: Preferred clothing style (e.g., Casual, Smart Casual)
  - **Favorite Brand**: Brand that the consumer prefers (e.g., Nike, Zara)
  - **Purchase Frequency (per month)**: Number of purchases made by the consumer each month
  - **Avg Spend per Purchase ($)**: Average amount spent per purchase
  - **Preferred Material**: Material of the preferred clothing item (e.g., Cotton, Wool)
  - **Size**: Size of the clothing item (e.g., S, M, L)
  - **Color Preference**: Preferred color of clothing (e.g., Blue, Black)
  - **Online Shopping Frequency**: How often the consumer shops online (e.g., Weekly, Monthly)
  - **Return Rate (%)**: Percentage of purchases returned by the consumer
  - **Satisfaction Rating (1-5)**: Consumer's satisfaction rating with purchases
  - **Influencer Follow (Yes/No)**: Whether the consumer follows influencers
  - **Discounts Effectiveness (1-5)**: Effectiveness of discounts as rated by the consumer
  - **Sustainable Preference (Yes/No)**: Preference for sustainable products
  - **Last Purchase Category**: Category of the last purchased item
  - **Last Purchase Date**: Date of the last purchase
  - **Review Written (Yes/No)**: Whether the consumer wrote a review for the last purchase

## Analysis Overview
The following analyses were performed:

### 1. Data Cleaning and Preprocessing
- **Steps Taken**:
  - **Loading Data**: Imported the dataset using pandas.
  - **Missing Values**: Checked for missing values; none were found.
  - **Outlier Detection**: 
    - Used Z-score to identify outliers in numerical columns (Income, Purchase Frequency, Avg Spend, Return Rate, Satisfaction Rating).
    - **Results**: Identified 11 outliers in Return Rate and 13 in Satisfaction Rating.
    - **Action**: Removed all outlier entries.
  - **Normalization**: 
    - Applied StandardScaler to Income ($), Avg Spend per Purchase ($), and Purchase Frequency (per month).
    - Ensured features are on a similar scale for further analysis.
    - **Results**: Cleaned dataset reduced from 1000 to 976 entries after removing outliers. Data is now normalized, making it suitable for modeling.

### 2. Funnel Analysis
- **Overview**: Funnel analysis tracks customer behavior through various stages of a conversion process, helping identify drop-off points and optimize marketing strategies.
  
- **Stages Defined**:
  1. **Visited Site**: Total number of consumers (976).
  2. **Added to Cart**: Consumers who made a purchase (436).
  3. **Initiated Checkout**: Consumers who spent a certain amount (526).
  4. **Completed Purchase**: Consumers who made a purchase (436).

- **Conversion Rates Calculated**:
  - **Visited Site to Added to Cart**: 446.72%
  - **Added to Cart to Initiated Checkout**: 120.63%
  - **Initiated Checkout to Completed Purchase**: 82.79%

- **Visualization**: A bar chart was created to visualize the number of users at each stage, indicating a significant drop-off from "Visited Site" to "Added to Cart."

- **Deeper Analysis by Gender**:
  - **Counts per Gender**:
    - Female: 486 visited, 258 added to cart, 486 initiated checkout, 258 completed purchase.
    - Male: 490 visited, 178 added to cart, 490 initiated checkout, 178 completed purchase.
  - **Conversion Rates**:
    - Female:
      - Added to Cart: 53.1%
      - Initiated Checkout: 100%
      - Completed Purchase: 53.1%
    - Male:
      - Added to Cart: 36.3%
      - Initiated Checkout: 100%
      - Completed Purchase: 36.3%

- **Visualizations**:
  - **Funnel Chart**: Displayed conversion rates for each gender.
   <div align="center">
      <img style="width:1000px; height:auto;" src="https://github.com/user-attachments/assets/fa8636d0-ab9d-44fe-8d6e-80f5fa9a56dd">
      <img style="width:1000px; height:auto;" src="https://github.com/user-attachments/assets/0a4f55fa-09cd-4c35-92a5-b5e1b5058fd3">
    </div>

  - **Pie Charts**: Illustrated conversion rates for "Added to Cart," "Initiated Checkout," and "Completed Purchase" by gender.

- **Insights**: A significant drop-off occurs from "Visited Site" to "Added to Cart," especially among males, suggesting targeted strategies may be necessary to improve engagement in that stage.

### 3. Exploratory Data Analysis (EDA)
- **Overview**: EDA is a crucial step in data analysis that helps summarize the main characteristics of the dataset using visual and quantitative methods.

- **Key Goals**:
  1. **Gain Insights**: Identify patterns and trends.
  2. **Detect Anomalies**: Spot outliers and data quality issues.
  3. **Understand Data Structure**: Assess distributions and relationships.
  4. **Formulate Hypotheses**: Generate ideas for further analysis.

- **Components of EDA Conducted**:
  1. **Descriptive Statistics**:
     - Summary statistics were calculated for numerical features such as income, purchase frequency, average spend, return rate, and satisfaction rating.
  2. **Data Visualization**:
     - **Univariate Analysis**:
       - **Histograms**: Distribution of numerical variables (e.g., Income, Avg Spend).
       - **Count Plots**: Frequency of categorical variables.
     - **Bivariate Analysis**:
       - **Scatter Plots**: Relationships between pairs of numerical variables.
       - **Box Plots**: Distribution of numerical variables across categorical groups.
  3. **Multivariate Analysis**:
     - **Pairplot**: Visual relationships among all numerical features.
       <<div align="center">
         <img style="width:600px; height:auto;" src="https://github.com/user-attachments/assets/dbd8bf00-d5e1-4480-a726-d982247203d4">
       </div>
              
     - **Correlation Heatmap**: Correlation coefficients among numerical variables.
      <div align="center">
         <img style="width:1000px; height:auto;" src="https://github.com/user-attachments/assets/4b57b2c1-286d-4f47-a43c-f18a50169972">
       </div>

- **Key Results**:
  - **Summary Statistics**:
    - **Income ($)**: Range from -1.78 to 1.23, with a mean close to zero.
    - **Purchase Frequency**: Average around 1.27 with a range indicating variability in consumer behavior.
    - **Avg Spend per Purchase**: Indicates a mean close to zero, suggesting variability in spending.
    - **Satisfaction Rating**: Average rating of 4.52, indicating generally high consumer satisfaction.
  - **Visual Insights**:
    - Histograms revealed distributions that can guide hypothesis generation.
    - Correlation heatmap highlighted relationships, such as positive correlations between **Satisfaction Rating** and **Avg Spend**.

- **Insights** EDA provided valuable insights into the dataset's structure, trends, and potential anomalies. This understanding is foundational for further statistical modeling or predictive analysis.

### 4. Feature Engineering
- **Overview**: Feature engineering involves creating, transforming, and selecting variables to enhance the performance of machine learning models.

- **Key Steps Taken**:
  1. **Feature Creation**:
     - **High Spender**: Created a binary feature indicating whether a consumer is a high spender based on their average spend compared to the median.
     - **Total Income**: Derived by multiplying income by purchase frequency to reflect overall spending potential.
  2. **Encoding Categorical Features**: Used one-hot encoding to convert categorical variables into numerical format.
  3. **Feature Scaling**: Scaled numerical features using StandardScaler to standardize the data.
  4. **Model Training and Evaluation**: 
     - Split the dataset into training and test sets (70-30%).
     - Built a Random Forest Classifier to predict the **High Spender** feature.

- **Key Results**:
  - **Model Evaluation**:
    - **Confusion Matrix**:
      - True Negatives (0): 156
      - False Positives (0): 0
      - False Negatives (1): 2
      - True Positives (1): 135
    - **Accuracy Score**: 99.3%
    - **Classification Report**: 
      - Precision for class 1: 1.00, Recall for class 1: 0.99
      - Overall F1-score: 0.99
  - **Top Feature Importances**:
    - The most significant features for predicting high spenders included:
      1. **Avg Spend per Purchase ($)**
      2. **Income ($)**
      3. **Satisfaction Rating (1-5)**
      4. **Total Income**
      5. **Purchase Frequency (per month)**
         <div align="center">
           <img style="width:1200px; height:auto;" src="https://github.com/user-attachments/assets/18137ddb-bc57-4591-bfe9-14d4dee4ff02">
         </div>


-  **Insights** The feature engineering process significantly improved the model's predictive capabilities, providing meaningful insights into consumer spending behavior.

### 5. Statistical Analysis
- **Overview**: Statistical analysis is the process of collecting, examining, and interpreting data to reveal patterns and insights.

- **Key Steps Taken**:
  1. **Chi-Square Test**: Assessed the independence between two categorical variables, specifically examining the relationship between **Gender** and **Favorite Brand**.
  2. **ANOVA Test**: Evaluated significant differences in means across multiple groups, focusing on **Avg Spend** based on **Occupation**.
  3. **T-Test**: Compared the means of **Avg Spend** between two groups: **Male** and **Female**.
  4. **Mann-Whitney U Test**: Conducted to compare differences in a continuous variable (e.g., **Satisfaction Rating**) between two independent groups.
  5. **Correlation Tests**: Performed Pearson and Spearman correlations.
  6. **Confidence Interval**: Calculated the confidence interval for the mean of **Avg Spend per Purchase**.
  7. **Descriptive Statistics**: Key statistics for numerical features.
  8. **Correlation Analysis**: Generated a correlation matrix to identify relationships between variables.
  9. **Regression Analysis**: Conducted Ordinary Least Squares (OLS) regression.
 10. **Multivariate Analysis**: PCA and K-Means clustering were performed.  
  11. **Visualization**: Plotted PCA results and K-Means clusters.
  12. **Time Series Analysis**: Analyzed trends over time.
  13. **Survival Analysis**: Conducted using Kaplan-Meier estimation.

- **Key Results**:
  - **Chi-Square Test**: Significant association between gender and brand preference.
  - **ANOVA Test**: Significant differences in average spending across occupations.
  - **T-Test**: No significant difference in average spending between males and females.
  - **Mann-Whitney U Test**: Significant difference in satisfaction ratings based on influencer follow status.
  - **Correlation Tests**: Strong positive correlation between income and average spending.
  - **Descriptive Statistics**: Indicated variability among customer income levels.
  - **Regression Analysis**: Provided insights into how well independent variables explain the target variable.
  - **Multivariate Analysis**: PCA visualized relationships among features, while K-Means revealed distinct customer segments.
    <div align="center">
      <img style="width:700px; height:auto;" src="https://github.com/user-attachments/assets/8281fac0-4851-43c4-9e2a-1f00476736c7">
    </div>

- **Insights**: The statistical analysis provided valuable insights into consumer behavior, revealing significant relationships and differences. Gender and occupation significantly influence spending, while income shows a strong correlation with spending patterns.

### 6. Clustering and Segmentation Analysis
- **Methods Used**:
  1. **K-Means Clustering**: Implemented to group customers based on spending behaviors.
  2. **Elbow Method**: Used to determine the optimal number of clusters by analyzing inertia values.

- **Results**:
  - **K-Means Clustering**: Successfully identified distinct customer segments for targeted marketing strategies.
  - **Elbow Method**: Indicated the optimal number of clusters, providing a balance between model complexity and explained variance.
    <div align="center">
      <img style="width:750px; height:auto;" src="https://github.com/user-attachments/assets/a306cc90-54be-4942-890e-36d0ccb0deca">
    </div>

### 7. Market Basket Analysis
- **Methods Used**:
  1. **Frequent Itemset Generation**: Used the Apriori Algorithm to identify frequent itemsets.
  2. **Association Rule Generation**: Generated association rules from frequent itemsets.
  3. **Data Visualization**: Plotted a heatmap to visualize the one-hot encoded data.

- **Results**:
  - **Frequent Itemsets**: Identified 490 frequent itemsets with significant single items like **Blouse** and **Chinos**.
  - **Association Rules**: Generated 2063 association rules, highlighting potential strategies for targeted marketing.

- **Insights**: Customer preferences and strong association rules suggest effective cross-selling opportunities and highlight the importance of understanding customer clusters for inventory management.

### 8. Cohort Analysis
- **Methods Used**:
  1. **Cohort Definition**: Created income cohorts based on specified income ranges.
  2. **Cohort Count Calculation**: Counted the number of customers in each income cohort.
  3. **Retention Rate Mapping**: Simulated retention rates for each income cohort.
  4. **Data Visualization**: Created bar plots to visualize customer counts and retention rates by income cohorts.
     <div align="center">
       <img style="width:750px; height:auto;" src="https://github.com/user-attachments/assets/0d9d6cc9-4913-4f79-96c7-8c33640d8d22">
     </div>

  - **Results**:
  - Defined four income cohorts with varying customer counts and retention rates, showing higher loyalty among higher income groups.

- **Insights**: The analysis suggests targeted strategies could enhance loyalty among lower income segments, highlighting opportunities for engagement initiatives.

## Conclusion

This analysis of e-commerce fashion data revealed critical insights into consumer behavior, highlighting significant drop-offs in the conversion funnel, particularly among male shoppers. The strong correlations between income and spending, along with distinct customer segments identified through clustering, underscore the need for targeted marketing strategies. Additionally, market basket and cohort analyses provided actionable opportunities for cross-selling and enhancing customer loyalty. Overall, these findings offer a solid foundation for optimizing marketing efforts and improving customer engagement in the competitive fashion landscape.

