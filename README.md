# 🔍 E-Commerce Customer Behavior Analysis

![Header Image](https://via.placeholder.com/1200x400/ff6200/ffffff?text=E-Commerce+Analytics)

Advanced analysis of customer transactions to uncover purchasing patterns, customer loyalty, and product performance.

## 📊 Key Insights & Visualizations

### 1. Customer Segmentation (RFM Analysis)
![Customer Segments](views/customer_segments.png)
- Identified 4 distinct customer clusters based on:
  - **Recency**: Days since last purchase
  - **Frequency**: Transaction count  
  - **Monetary**: Total spending
- **Actionable Insight**: Target "High-Value Recent" cluster (purple) with loyalty programs

### 2. Top Products Analysis
![Top Purchased Items](views/top_purchased.png)
- **Loyal Customers** prefer practical items (cables, adapters)
- **One-Time Buyers** favor decorative/seasonal products  
- **Opportunity**: Bundle popular items from both groups

### 3. Sales Forecasting
![Sales Forecast](views/sales_forecast.png)
- Prophet model predicts **15% growth** over next 90 days
- Clear weekly seasonality (peaks on weekends)
- **Recommendation**: Increase weekend staffing

### 4. Customer Cohort Analysis  
![Cohort Analysis](views/cohort_analysis.png)
- January cohort shows **32% retention** after 6 months
- Summer cohorts have higher initial churn
- **Action Plan**: Improve onboarding for summer customers

### 5. Time-Based Patterns
![Hourly Sales](views/hourly_sales.png)
- **Peak Hours**: 11AM-3PM (30% of daily revenue)
- **Dead Zone**: 3AM-6AM (<2% of sales)
- **Optimization**: Schedule promotions during lulls

### 6. Product Value Concentration (ABC Analysis)
![ABC Analysis](views/abc_analysis.png)
- **20% of products (Class A)** generate **80% of revenue**
- **Class C** items may need discontinuation
- **Strategy**: Focus inventory on high-performers

## 🛠 Technical Implementation

```python
# RFM Analysis Example
rfm = df.groupby('CustomerID').agg({
    'InvoiceDate': lambda x: (current_date - x.max()).days,
    'InvoiceNo': 'nunique',
    'Total_Spend': 'sum'
})
kmeans = KMeans(n_clusters=4)
rfm['Cluster'] = kmeans.fit_predict(scaler.fit_transform(rfm))
