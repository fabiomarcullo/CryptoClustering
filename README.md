#  Clustering Cryptocurrencies - Module 19 Challenge

In this challenge, you’ll use your Python and unsupervised learning knowledge to predict if cryptocurrencies are affected by 24-hour or 7-day price changes.

### Data Used
[Crypto_market_data](/Resources/crypto_market_data.csv) - market data of different cryptocurrencies during different time periods 

### Jupyter notebook

The Jupyter notebook [Crypto_Clustering](/Crypto_Clustering.ipynb) will provide all steps of the data collection, preparation, and analysis. Data visualizations are shown inline and accompanying analysis responses are provided.

### Summary

I start by using the elbow curve method, using normalized data, to find the optimal k value for the K-Means model that will use all of the original features of the dataset. 

![Elbow curve line plot showing a value of 4 for k to be optimal for the dataset with all features](/Resources/Images/elbow_curve.png)

Then, using the optimal k value I train and predict the K-Means model to generate 4 clusters of cryptocurrencies. The inertia of each cluster was significant enough to consider reducing the number of features. 

![A scatter plot showing 4 clusters with heavy inertia](/Resources/Images/all_features_scatter.png)

To reduce the number of features used, I applied Principal Component Analysis to create 3 primary clusters. 

![DataFrame holding 3 primary clusters as columns and cryptocurrency as index](/Resources/Images/pca.png)

I then used the PCA data to again calculate the optimal k value for the K-Means model. 

![Elbow curve line plot from the PCA data that shows 4 to be the optimal k value](/Resources/Images/pca_elbow_curve.png)

Finally, with the optimal k value for the PCA features, I plot the new clusters. 

![Scatter plot showing 4 low inertia clusters generated using the PCA dataframe](/Resources/Images/pca_scatter.png)

---

### Questions and Answers

#### Answer the following question: 

**Question:** What is the best value for `k`?

  * **Answer:** The best value for `k` would be 4 since the elbow shape starts there. 

**Question:** What is the total explained variance of the three principal components?

  * **Answer:** The total explained variance adds up to about 89.50% of the original data. 

* **Question:** What is the best value for `k` when using the PCA data?

  * **Answer:** The best value for `k` would be 4 because the elbow shape starts there. 


* **Question:** Does it differ from the best k value found using the original data?

  * **Answer:** No, even though the elbow curves are slightly different the k value of 4 is still the best with the PCA data. 

* **Question:** After visually analyzing the cluster analysis results, what is the impact of using fewer features to cluster the data using K-Means?

  * **Answer:** The inertia for the clusters with the PCA features is way lower than that of the original features. The values within each cluster are much closer together and easier to distinguish compared to the ones in the original data. The PCA plot also better separated the two outliers celsius-degree-token and ethlend. In general it seems that the clusters held the same coins even though coins like tezos and iota were much closer to the other cluster, so it seems that even with the loss of 10% data that the accuracy was still good. 
