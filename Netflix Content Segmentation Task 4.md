# Netflix Content Segmentation: Task 4 

# Auspify Technologies Machine Learning Internship | Task 4 (Medium) | Author: Elliot Agyare



1. Project Overview
---

Objective: group Netflix titles into meaningful clusters using unsupervised machine learning techniques.

Approach in one paragraph: each title was described by its scaled release year, its type, its audience group and its genres. The K-Means algorithm then grouped similar titles together without being told any answers. The number of clusters was chosen with the elbow method and the silhouette score, the clusters were profiled by their size, type, release year, audience and top genres, and they were visualized in two dimensions with PCA.


2. Dataset
---

• File: Dataset.csv, 8,790 rows and 10 columns, reduced to 8,787 rows after removing 3 duplicates.

• Data quality: missing values are stored as the text "Not Given" and were replaced with empty values.

• No target column: clustering is unsupervised, so there is no answer to predict. Titles with no usable rating were kept in an "Unrated" group instead of being removed.




3. Tools and Libraries
---

• Python in Google Colab

• pandas and numpy for data handling

• scikit-learn for scaling, K-Means, PCA and the silhouette score

• matplotlib for charts



4. Methodology
---


Step 1: Prepare numerical and categorical features
---

• Numerical feature: release\_year, standardized with StandardScaler so it has a comparable scale to the other features.

• Type: a 0/1 column, where 1 means TV Show.

• Audience: the 14 ratings were grouped into Kids, Family, Teen and Adult, with the remaining titles marked Unrated, and then one-hot encoded.

• Genres: listed\_in was split into individual genres and converted to 0/1 columns.

• The final feature matrix has 49 columns.

• Why scaling matters: K-Means groups titles by distance. Release year runs from 1925 to 2021, while every other feature is 0 or 1, so without scaling the year dominates. A test run without scaling produced clusters that were simply blocks of release years. \[Add your own screenshot of that test and explain it in your own words.]



Step 2: Apply clustering algorithms
---

• K-Means was run for 2 to 10 clusters.

• Two measures were compared: inertia (the elbow method) and the silhouette score, calculated on a sample of 3,000 titles for speed.

• Final number of clusters: \[your k, and the reason you chose it].



Step 3: Identify content groups
---

• A profile table was built for every cluster, showing its number of titles, share of TV Shows, average release year, most common audience and top three genres.

• Five sample titles per cluster were printed to help name each group.



Step 4: Visualize clusters
---

• PCA reduced the 49 features to the 2 directions that keep the most information.

• A scatter plot colored each title by its cluster.



Step 5: Interpret cluster characteristics
---

• Each cluster was given a descriptive name based on its profile and its sample titles.


6. Challenges and How They Were Solved
---

• Features on different scales: the release year would have dominated the distance calculation. Fixed with StandardScaler.

• Choosing k: the elbow chart has no sharp bend, so the silhouette score was used as well, and the final choice was a judgement call. 
• Naming clusters: the numbers 0, 1, 2 mean nothing on their own, so profile tables and sample titles were used to give each cluster a name.




7. Limitations
---

• K-Means uses straight-line distance, which is not ideal for 0/1 genre columns.

• Silhouette scores are low, so the clusters overlap and are not sharply separated.

• The 2D PCA picture shows only part of the information in the data.

• Plot descriptions and cast are not in the dataset, so groups are based on metadata only.

• Cluster names are subjective interpretations.





## 8\. How to Run the Project

1\. Open Google Colab and create a new notebook.

2\. Upload Dataset.csv using the folder panel on the left.

3\. Run the cells from top to bottom with Shift + Enter. The cell that tests different numbers of clusters can take about a minute.



