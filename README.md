# Cryptocurrencies

## Overview and Purpose

In this exercise, an investment bank is interested in offering a new cryptocurrency investment portfolio for its customers. I have been asked to discover trends and create a report that illustrates what cryptocurrencies are on the trading market and how they could be grouped to create a classification system for this new investment. My assignment is to process the data using an unsupervised learning model and clustering algorithm, and then present the findings using data visualization.

## Results

### Deliverable 1: Preprocessing the Data for PCA

- First, I imported the dataset, which originally contained 1,252 records:

![1 Del 1 imported file](https://user-images.githubusercontent.com/97558998/175300746-65b59611-9b00-4402-8f3d-71f8b5aa1515.png)

- I then explored the dataset:

<img width="883" alt="explore dataset" src="https://user-images.githubusercontent.com/97558998/175301558-809391cc-6c34-4699-bea3-c152eb7642e3.png">

- I renamed the "Unnamed" column and set it as the index (6 columns):

![2 Renamed Unnamed col and set index](https://user-images.githubusercontent.com/97558998/175301722-034bee0a-c3ed-4c13-a16f-4be976627546.png)

- I kept all cryptocurrencies that were being traded and had a working algorithm, which reduced the dataset to 1,144 rows, and removed the "IsTrading" columns, reducing the dataset to 5 columns.

- I then removed rows with null values, which reduced the dataset to 685 rows:

<img width="656" alt="remove null values" src="https://user-images.githubusercontent.com/97558998/175302559-13b1c552-86ef-4047-be14-51a91adfff92.png">

- I kept the rows where coins are mined [["TotalCoinsMined"] > 0], which left 532 rows:

![6 coins mined](https://user-images.githubusercontent.com/97558998/175302822-bb4130f2-032d-49d6-b5d9-7bdc3bfe1e66.png)

- I then dropped the 'CoinName' column since it would not be used on the clustering algorithm, created a new DatFrame that stored all cryptocurrency names from the *CoinName* column and retained the index from the original DataFrame, used *get-dummies()* to create variables for text features, and standardized the data with *StandardScaler().fit_transform(X)*.

### Deliverable 2: Reducing Data Dimensions Using PCA (Principal Component Analysis)

- I used the PCA model to reduce the dimension to three principal components and create a new dataframe:

<img width="357" alt="three components" src="https://user-images.githubusercontent.com/97558998/175303381-66b48cf3-d438-467e-be92-1846fb465956.png">

### Deliverable 3: Clustering Cryptocurrencies Using K-Means

- I found the best value for *k* using the elbow curve:

<img width="914" alt="elbow curve" src="https://user-images.githubusercontent.com/97558998/175304115-026cf567-f280-4522-b4c3-ee90c9440da2.png">

- I initialized K-Means model using k=4 and predicted clusters, created a new DataFrame including the predicted clusters and cryptocurrency features, added new a column “CoinName” to hold names of the cryptocurrencies, and added a new column "Class" to the DataFrame to hold the predictions:

<img width="975" alt="predictions" src="https://user-images.githubusercontent.com/97558998/175304731-9584e1f1-41f1-4b97-a305-bc3f6a81b9a1.png">

### Deliverable 4: Visualizing Cryptocurrencies Results

- To visualize the results, I created a 3D-scatter plot with clusters, using *hover_name* and *hover_data* parameters for the *CoinName* and *Algorithm* columns, respectively:

![15 3D scatter plot](https://user-images.githubusercontent.com/97558998/175305146-21d14c77-7e7a-4a39-9223-fcbad99260c1.png)

![3Dscatter](https://user-images.githubusercontent.com/97558998/175310012-15910341-8ee2-44e5-aea5-b1f96fa9cee4.png)

- I created a table with tradable cryptocurrencies:

![13 table with 532 stmt](https://user-images.githubusercontent.com/97558998/175305343-75aa8a17-93b3-4b98-8d08-4e4075fc3099.png)

- Scaled data to create a scatter plot, created a new dataframe for scaled data, and added “CoinName” and “Class” columns to the new dataframe:

![13 table with 532 stmt](https://user-images.githubusercontent.com/97558998/175305515-205c11c6-eda3-4b97-8ca0-1f4a93317b2e.png)

- Finally, I created a scatterplot:

![scatter_plot](https://user-images.githubusercontent.com/97558998/175305588-8f1b6b81-616b-4b13-bd8a-dfbd6716bc22.png)

