![image](https://github.com/user-attachments/assets/1e8b48ee-e610-4937-8e82-12fc89520f40)

# Amazon-Customers-Segmentation
Customer Segmentation and Analysis Project
Overview
This project involves analyzing customer data to derive actionable insights through segmentation using various clustering techniques. The main goal is to improve personalized recommendations and marketing strategies by identifying distinct customer segments based on their behaviors and characteristics.

Table of Contents
Project Description
Data Description
Preprocessing Steps
Clustering Techniques
Model Evaluation
Insights and Recommendations
Installation and Usage
License
Project Description
The project aims to segment customers based on their purchase behaviors and other relevant features using clustering techniques. By analyzing these segments, we can derive actionable insights to enhance personalized recommendations and marketing strategies.

Data Description
The dataset contains 602 entries with various features including customer demographics, purchase frequency, browsing behavior, and feedback on services. The data is preprocessed to handle missing values and normalize the features for analysis.

Key Features:
age: Customer age
Purchase_Frequency: Frequency of purchases
Browsing_Frequency: Frequency of browsing
Customer_Reviews_Importance: Importance of customer reviews
Various boolean features representing customer preferences and improvement areas
Time: Time of data entry (converted to numeric)
Preprocessing Steps
Handling Missing Values: Imputation or removal of missing values.
Standardization: Normalizing the feature scales for PCA.
Feature Transformation: Conversion of boolean columns to binary numeric values.
Time Conversion: Conversion of time data to numeric format for consistency.

Standardization: Standardized the dataset.
Explained Variance: Analyzed the explained variance ratio of each principal component to understand their significance.

Clustering Techniques
K-Means Clustering
Used to partition data into K distinct clusters.

python
Copy code
from sklearn.cluster import KMeans

kmeans = KMeans(n_clusters=4, random_state=42)
kmeans_labels = kmeans.fit_predict(df_pca)
Hierarchical Clustering
Performed using Agglomerative Clustering to create a hierarchy of clusters.

python
Copy code
from sklearn.cluster import AgglomerativeClustering

hierarchical = AgglomerativeClustering(n_clusters=4)
hierarchical_labels = hierarchical.fit_predict(df_pca)
DBSCAN
Applied DBSCAN for density-based clustering to identify clusters of varying shapes.

python
Copy code
from sklearn.cluster import DBSCAN

dbscan = DBSCAN(eps=0.5, min_samples=5)
dbscan_labels = dbscan.fit_predict(df_pca)
Gaussian Mixture Model (GMM)
Used to model data with a mixture of Gaussian distributions.

python
Copy code
from sklearn.mixture import GaussianMixture

gmm = GaussianMixture(n_components=4, random_state=42)
gmm_labels = gmm.fit_predict(df_pca)
Model Evaluation
The performance of each clustering model was evaluated using the Silhouette Score:

python
Copy code
from sklearn.metrics import silhouette_score

silhouette_kmeans = silhouette_score(df_pca, kmeans_labels)
silhouette_hierarchical = silhouette_score(df_pca, hierarchical_labels)
silhouette_dbscan = silhouette_score(df_pca, dbscan_labels) if len(set(dbscan_labels)) > 1 else "Not applicable"
silhouette_gmm = silhouette_score(df_pca, gmm_labels)
Insights and Recommendations
Based on the clustering results:

Customer Segments: Analyze each cluster's characteristics to understand demographic and behavioral differences.
Personalized Recommendations: Tailor recommendations based on segment preferences and purchase patterns.
Marketing Strategies: Design targeted marketing campaigns for each segment to improve engagement and conversion rates.
Service Improvement: Address common issues and preferences highlighted by different segments to enhance customer satisfaction.
Installation and Usage

