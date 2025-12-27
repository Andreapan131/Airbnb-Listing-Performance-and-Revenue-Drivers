# Airbnb Listing Performance and Revenue Drivers Analysis
## 📌 Project Purpose
This project aims to explore how Airbnb and its existing hosts in New York City can protect and grow revenue under Local Law 18 using listing-level data. This analysis identifies key performance drivers that inform platform strategy and host optimization decisions.

## 📊 Dataset Description
- Source: [Airbnb NYC Listings](https://insideairbnb.com/get-the-data/)
- The original dataset includes 79 columns and 36111 rows. After cleaning, we have 53 columns for analysis
  
- Data Dictionary: [Click here to see the whole column definition](https://github.com/Andreapan131/MarketingAnalysis_Aribnb-Listings-Performance/blob/main/Airbnb%20Open%20Data%20Dictionary.xlsx)
  - **Host & Listing Characteristics**  
    e.g. host_is_superhost, host_response_time, host_years_active, host_listings_count, accommodates, bedrooms, bathrooms, beds, amenities, room_type, latitude, longitude, neighbourhood...
  - **Pricing & Performance Metrics**  
    e.g. price, minimum_nights, maximum_nights, instant_bookable, estimated_revenue_l365d, estimated_occupancy_l365d
  - **Reviews & Demand Signals**  
    e.g. review_scores, number_of_reviews, reviews_per_month, number_of_reviews_ltm, number_of_reviews_l30d, *review_cluster

## 🏷 Methodology
### 1️⃣ Data Preprocessing
- Data Cleaning
  - Dropped columns and rows
  - Removed outliers and missing values
  - Transformed data type and format

### 2️⃣ K-means Clustering
- Applied K-means clustering using review-related variables
- Used the Elbow Method to determine the optimal number of clusters (k = 3)
- Merged cluster labels into the original dataset

### 3️⃣ Statistical Testing (ANOVA)
One-way ANOVA was used to evaluate if the review-based clusters represent meaningful and distinct group.
- Tested whether customer engagement (measured by review volume) differs significantly across clusters
- Examined whether pricing differs across clusters to ensure that observed performance differences are not simply driven by price

### 4️⃣ Regression Analysis
Because cluster patterns alone cannot establish a review–revenue relationship, linear regression was used as a formal modeling approach.
- Estimated revenue over the past 365 days was used as the dependent variable
- Overall review score was specified as the key independent variable
- Control variable were included to hold other factors constant

### 5️⃣ Data Visualization
- Cluster-level comparisons and distributions
- Regression relationships between review quality and revenue
- Neighborhood-level performance patterns

## 🔍 Key Findings & Insights
❶ **Review Quality Differs Meaningfully Across Listings**
- Low-quality listings underperform most on perceived value and accuracy
- Cleanliness and communication decline consistently with lower review quality
  
❷ **Host Experience and Review Volume**
- High rating clusters are associated with more experienced hosts
- Listings in higher-quality clusters receive more reviews
    
❸ **Performance Gaps Vary by Neighborhood**
- Manhattan has the highest propotion of low rating listings and the smallest share of top-rated listings
- Staten Island shows the opposite pattern, with the strongest concentration of high-quality listings
  
❹ **Demand Follows Quality, Not Price**
- Prices do not differ meaningfully across review-based clusters
- Review quality has a statistically significant positive association with revenue after controlling for price, location, and listing features

## 📊 Visualizations

### Review_Score_Segmentation
<img src="Review_Quality_Segmentation.png" width="600">

- Review quality differs meaningfully across listings  

### Demand_by_Review_Cluster
<img src="Demand_by_Review_Cluster.png" width="600">

- Higher review quality is associated with higher occupancy

### Average Price by Review Cluster
![Price_by_Review_Cluster](Price_by_Review_Cluster.png)
- Average prices do not differ meaningfully across clusters, suggesting performance gaps are not driven by pricing

### Review Quality Is a Key Revenue Driver
![OLS Coefficient Plot](regression_coefficients.png)

- Review rating shows the strongest statistically positive association with revenue
- +1 review point ≈ +$5,300 in annual revenue

## 🚀 Business & Social Implications
- Shift from supply-driven growth to quality-driven growth
- Higher review volume strengthens platform reliability by increasing transparency and guest confidence
- Pricing cannot compensate for poor quality and will not drive occupancy increases
- Target quality investments geographically for maximum impact
  
## 📂 Repository Files
- **Airbnb_MarketingAnalysis_code.py** – Script for data analysis and visualization
- **Airbnb_FinalData.xlsx** – Dataset used in the analysis
- **Airbnb Open Data Dictionary.xlsx** – Dictionary for the dataset
- **Review_Quality_Segmentation.png** – Average Rating across clusters visualization
- **Demand_by_Review_Cluster.png** – Occupancy across clusters graph
- **Price_by_Review_Cluster.png** – Price distribution across clusters plot
- **regression_coefficients.png** – Regression coefficients with revenue visual
- **README.md** – Project documentation
