# Clustering
Implementing Clustering on Iris Dataset

#### 1.LOADING AND EXPLORING THE DATA
The Iris flower dataset is a well-known collection of data in machine learning and statistics, featuring measurements from 150 iris flowers across three species. This report looks at the dataset using clustering, which is a method for grouping data without needing pre-assigned categories. Clustering helps to identify natural patterns and groupings in the data based on the flower measurements.
###### DATA LOADING AND EXPLORATION
The dataset was loaded using the `sklearn.datasets` module. It contains 150 samples, each with the following four features: sepal length, sepal width, petal length, and petal width. There are three target classes, representing the species of the iris flowers.
#### 2. DATA PREPROCESSING
The dataset was checked for missing values, and none were found. Feature scaling was applied using the StandardScaler to normalize the feature set, which aids in improving the performance of the clustering algorithms.

#### 3. CLUSTERING ALGORITHMS
 K-MEANS CLUSTERING
Assumptions:
-	The algorithm assumes the variance of the distribution of each attribute is the same.
-	The number of clusters (K) must be specified in advance.
Advantages: 
-	Easy to understand and implement.
-	Efficient in terms of computational cost, typically fast and good for large datasets.
Disadvantages: Sensitive to outliers and initial seed placement.

#### HIERARCHICAL CLUSTERING
Assumptions: The algorithm creates a hierarchy of clusters by measuring the distance between data points, operating under the assumption that data points that are nearer to each other are more alike than those that are further apart.
Advantages: Does not require the number of clusters to be specified in advance and is more flexible than K-means.
Disadvantages: Computationally expensive and not suitable for large datasets.
#### DBSCAN
Assumptions: Clusters are identified as dense areas within the data space, surrounded by areas of lower density. The method depends on a concept of clustering based on density, which allows for more flexibility in the shapes of the clusters.
Advantages: Does not require the number of clusters to be specified, can find arbitrarily shaped clusters and is good with outliers.
Disadvantages: Not well-suited for data sets with varying densities or when the data has too much overlap.

#### 4. Experimentation and Results
K-MEANS CLUSTERING:
In the elbow plot, there is a steep decline from 1 to around 3 clusters, after which the decrease in WCSS becomes more gradual. This suggests that increasing the number of clusters beyond 3 doesn't significantly improve the model, and thus, 3 might be the appropriate number of clusters to use.

-	The first graph shows data points grouped into two clusters, as indicated by the two colors. The black dots likely represent the centroids of the clusters. The score at the 0.5817 represent a measure of the model's performance.

-	The second graph increases the number of clusters to three. The score has decreased to 0.4599, which might suggest that the model is less optimal with three clusters compared to two.

-	The third graph shows the data points grouped into four clusters. The score 0.3869 has decreased further, which might suggest that the separation between the clusters is less distinct, making the model less optimal than the previous one.


#### HIERARCHICAL CLUSTERING (AGGLOMERATIVE CLUSTERING):
-	Different Linkage methods(ward, single, average, complete) are visualized using dendograms, helping to interpret the cluster structure.

1.Single Linkage Dendrogram: Demonstrates a chaining effect where clusters are joined based on nearest points, resulting in a silhouette score of 0.58 that suggests moderate cluster separation.

2. Complete Linkage Dendrogram: Exhibits more balanced and distinct cluster formations due to the furthest point linkage criterion, with a lower silhouette score of 0.44 indicating tighter but fewer clusters.

3. Average Linkage Dendrogram: Strikes a balance between single and complete linkage, merging clusters based on average distances with a silhouette score of 0.58, hinting at reasonable cluster cohesion.

4. Ward Linkage Dendrogram: Prioritizes cluster compactness, leading to distinct, evenly-sized clusters, as shown by large distances in later merges and a silhouette score of 0.57, indicative of good cluster structure.
   
#### DBSCAN:
Different parameters for eps and min sample are experimented with and silhouette scores are calculated for each. The best DBSCAN parameter setting in terms of Silhouette score(0.538) used eps=1 and min_samples=6, indicating a fair clustering outcome, though lower than K-means and Hierarchical clustering.
-	First Graph (DBSCAN with eps=0.5, min_samples=5):
First graph displays a clustering where the eps parameter, which defines the maximum distance between two samples for them to be considered as in the same neighborhood, is set to 0.5, and min_samples, the number of samples in a neighborhood for a point to be considered as a core point, is set to 5. 

-	Second Graph (DBSCAN with eps=1, min_samples=6):
The min_samples is increased to 6, meaning a denser region is needed for a point to be considered a core point. The Silhouette Score has improved to approximately 0.538, indicating better clustering quality compared to the first graph. 
-	Third Graph (DBSCAN with eps=1, min_samples=3):
With the eps still at 1, the min_samples is decreased to 3. This results in more points being included in clusters. The Silhouette Score is approximately 0.546, suggesting a slight improvement in the clustering quality. 

#### 5. EVALUATION
###### SILHOUETTE SCORE
The silhouette score measures the main intra-cluster distance between each point and the closest cluster to which it does not belong. Higher values indicate better defined clusters.
###### INERTIA
Inertia measures the sum of squared distances of samples to their nearest cluster center. Lower inertia values indicate a model with tightly grouped clusters.

###### K-MEANS CLUSTERING
Silhouette Score for k=2 is 0.5817	
Silhouette Score for k=3 is 0.4599
Silhouette Score for k=4 is 0.3869

###### HIERARCHICAL CLUSTERING
Silhouette Score for Single Linkage is 0.5817
Silhouette Score for Complete Linkage is 0.4408
Silhouette Score for Average Linkage is 0.5817
Silhouette Score for Ward Linkage is 0.5770

 ###### DBSCAN
Silhouette Score for DBscan (eps=0.5, min_samples=5) is 0.3565.
Silhouette Score for DBscan (eps=1, min_samples=6) is 0.5382.
Silhouette Score for DBscan (eps=1, min_samples=3) is 0.5046.


#### 6. INTERPRETATION AND RESULTS

###### K-MEANS CLUSTERING
The within-cluster sum of squares (WCSS) begins to decline down at three clusters, which appears to be the optimum cluster number according to the elbow method. Higher silhouette scores indicate greater fit. The silhouette score compares each point's fit inside its cluster to the rest of the other points. This would usually imply the best clustering, assuming that the highest silhouette score given matches the earliest cluster count. The first graph with the silhouette score would be the best since it has the highest silhouette score of approximately 0.5817.

###### HIERARCHICAL CLUSTERING
Ward's method often is a good default choice as it tends to create more balanced cluster sizes, indicated by the relatively high silhouette score and the clear demarcation of clusters in the dendrogram.

###### DBSCAN:
Different parameters for eps and min sample are experimented with and silhouette scores are calculated for each. The best DBSCAN parameter setting in terms of Silhouette score(0.538) used eps=1 and min_samples=6, indicating a fair clustering outcome, though lower than K-means and Hierarchical clustering.

#### 7. VISUALIZATION

###### K-MEANS CLUSTERING
![image](https://github.com/user-attachments/assets/5f133638-e08e-4f15-970e-cc61dc5b2728)
![image](https://github.com/user-attachments/assets/85dc8672-5ee3-411a-a918-d6bf1b3f03ae)
![image](https://github.com/user-attachments/assets/d6bc19c3-8f7b-42e7-b0e3-fefb20593e25)
![image](https://github.com/user-attachments/assets/eb1e73c5-ef72-48d6-bed2-6aca989a304a)                                                                                                        

###### HIERARCHICAL CLUSTERING
![image](https://github.com/user-attachments/assets/295671e3-15e8-4ac6-9ef4-92178ed9035d)
![image](https://github.com/user-attachments/assets/b189740d-fa3c-4fb1-bb9b-a35c8eec286c)
![image](https://github.com/user-attachments/assets/91ba25af-d5f4-4a53-80bf-983bd12fa2c6)
![image](https://github.com/user-attachments/assets/fcb26c15-4780-4614-94d0-4fac8307eabb)

###### DBSCAN CLUSTERING
![image](https://github.com/user-attachments/assets/bb88aa13-d54f-4b6c-89ed-2e875029a46f)
![image](https://github.com/user-attachments/assets/aa103134-017c-4a68-a947-3e67aef9b3ef)
![image](https://github.com/user-attachments/assets/a9578220-531c-4366-b69f-a0c0999ee69f)

                                    

                                                            
 
