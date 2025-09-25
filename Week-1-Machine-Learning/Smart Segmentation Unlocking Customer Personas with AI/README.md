# Customer Segmentation with Clustering

##  Project Overview
This project applies **unsupervised machine learning (clustering)** to segment customers based on their demographic and behavioral data.  
The dataset comes from a Mall Customers dataset, which includes features such as **Gender, Age, Annual Income, and Spending Score**.  

The goal is to:  
1. Explore whether **gender affects spending behavior**.  
2. Apply **feature engineering** to create new insights for clustering.  
3. Perform **clustering analysis** to identify distinct customer groups.  
4. Interpret the clusters and provide actionable insights.  

---

## 🗂 Dataset
The dataset contains 200 customer records with the following features:

- **Gender**: Male or Female  
- **Age**: Age of the customer (years)  
- **Annual Income (k$)**: Income of the customer (in $1000s)  
- **Spending Score (1-100)**: Score assigned based on purchasing behavior  
- **Engineered Features**:  
  - `Income_Cluster`: Cluster labels based on income levels  
  - `Age_Cluster`: Cluster labels based on age levels  
  - `Affinity_Index`: A combined score of standardized income and spending (created using feature engineering)  

---

## 🔍 Exploratory Analysis
1. **Gender vs Spending Score**  
   - Both genders showed **similar distributions** of spending.  
   - Welch t-test (p=0.422) and Mann–Whitney test (p=0.571) confirmed that **gender is not a significant factor** in spending behavior.  

2. **Feature Engineering**  
   - Created an **Affinity Index** by combining standardized income and spending.  
   - This new feature improved the clustering by better separating groups with similar income–spending patterns.  

---

## 🤖 Clustering Approach
1. **Standardization**: Used `StandardScaler` to normalize features (income and spending).  
2. **Elbow Method**: The optimal number of clusters was found to be **k=5**.  
3. **K-Means Clustering**: Applied on Income, Spending, and Affinity Index.  
4. **Validation**: Silhouette Score = **0.541**, showing a reasonable cluster structure.  

---

## 📊 Cluster Insights
### Identified 5 Customer Segments:
- **Cluster 0**:  
  - Mid-income, mid-spending (avg. income: 55k, spend: 50)  
  - Older (avg. age: 43), balanced gender mix  
  - Represents the **largest group** of customers.  

- **Cluster 1**:  
  - High-income, high-spending (avg. income: 87k, spend: 82)  
  - Younger (avg. age: 33)  
  - Premium **loyal customers**.  

- **Cluster 2**:  
  - Low-income but **high-spending** (avg. income: 26k, spend: 79)  
  - Very young (avg. age: 25), more female customers  
  - Could be **aspirational or trend-driven buyers**.  

- **Cluster 3**:  
  - High-income but **low-spending** (avg. income: 88k, spend: 17)  
  - Middle-aged (avg. age: 41), slight male majority  
  - Represents **wealthy but disengaged customers**.  

- **Cluster 4**:  
  - Low-income, low-spending (avg. income: 26k, spend: 21)  
  - Older (avg. age: 45), mostly female  
  - **Budget-conscious customers**.  

---

## ✅ Conclusions
- **Gender does not significantly affect spending scores**.  
- Clustering reveals **five distinct customer personas** that can help businesses target marketing strategies more effectively:  
  - Loyal high-value customers  
  - Aspirational young spenders  
  - Budget-conscious older customers  
  - Wealthy but disengaged customers  
  - The balanced mid-market majority  

This segmentation can be directly used for **personalized marketing, customer retention, and targeted campaigns**.  

---

## 🛠 Tools & Libraries
- Python (Pandas, NumPy)  
- Scikit-learn (KMeans, StandardScaler, Silhouette Score)  
- Seaborn & Matplotlib (Visualization)  
- Scipy (Statistical tests)  

---

## 📂 Dataset Source
[Kaggle: Mall Customer Segmentation Dataset](https://www.kaggle.com/vjchoudhary7/customer-segmentation-tutorial-in-python)

