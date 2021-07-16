# Cryptocurrencies

For this analysis we use a K-means algorithm to cluster tradable cryptocurrencies. This involed the following steps: preprocessing the data for PCA, reducing data dimensions using PCA, clustering cryptocurrencies using K-means, and visualizing the cryptocurrencies results.

# Preprocessing the Data for PCA
For preprocessing, we loaded the data into a Pandas DataFrame. We then kept only the cryptos such that `crypto_df.IsTrading == True`. We dropped all rows where coins we not mined and used Pandas `get_dummies()` function to numericize the `Algorithm` and `ProofType` columns. Finally, we scaled the data using `StandardScaler().fit_transform()`.

# Reducing Data Dimensions Using PCA
Using the scaled data, we used PCA with `n_components=3` to reduce the dimension of the data to three principal components, and placed these in a new dataframe with the name of the cryptocurrencies as the index.

# Clustering Cryptocurrencies Using K-Means
To determine the k value for our K-Means algorithm, we created an elbow curve to determine k=4 would work best. We then fed our data into our `KMeans()` function to get the predictions for which class each crypto belonged to. We then created a new dataframe with all of the original information, including the principal components and the class.

# Visualizing Cryptocurrencies Results
Now that we have our principal components and class for each cryptocurrency, we created a 3D-scatter plot containing each cryptos principal component values, their name, and which algorithm is used. Using hvPlot, we created a sortable table containing the name, algorithm, prooftype, total coin supply, coins mined and their class. Finally, we used `MinMaxScaler().fit_transform()` to scale the `TotalCoinsMined` and `TotalCoinSupply` columns and created a new dataframe with these scaled values. Using this dataframe we created a 2D scatter plot where `x = 'TotalCoinsMined'`, `y = 'TotalCoinSupply'`, `hover_cols = 'CoinName'`, and colored `by = 'Class'`.