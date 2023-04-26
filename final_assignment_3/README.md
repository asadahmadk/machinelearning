## Machine Learning Assignment 3

### [Starter Code](https://github.com/visualizedata/ml/tree/master/final_assignment_3/option_3)

I worked with data on food contamination **to cluster incident descriptions into broader categories**. This assignment uses an unsupervised learning method to cluster FDA food recalls based on the text description of the item and the recall. A bag of words feature set is used to build the initial feature matrix to pass to the k-means model. I made many changes to the feature representation as it seemed to be the best way to affect change on the results. 

I tested the following approaches:

1. Removing all numbers
2. Shortening the strings to be the first 100 characters
3. Switching from CountVectorizer to HashingVectorizer

The final feature set uses HashingVectorizer, removes all "common" words (from NLTK package) and some words that were common in the data set, but not included in the default "common" words list. The additional common words were identified using the Counter() function in the collections package and the final list is below:

common=['oz','lb','lbs','product','packaged','code','brand','upc','packed','sold','distributed','net','wt','g','inc','item','labeled','label','ca','llc','date','bag','bags','weight','case','container','plastic','per','size','individually','containers','kg','film']


For the k-means model, I initially used the elbow plot to try to identify the number of clusters. This proved to be unhelpful, with no clear elbow appearing during any iterations (see example output below).
![KMeans](https://user-images.githubusercontent.com/109235609/234432755-fd990afe-ddb5-4281-ac81-0fbb34b65ee4.png)


I chose to use silhouette plots to assist me in determining the optimal number of clusters to use and to gain insight into the relationship between cluster size and specificity. The larger clusters generally had lower coefficient values. I generated silhouette plots for various numbers of clusters and found that although the average coefficient value increased with the number of clusters, having too many clusters could be overwhelming for users. I also recognized that this could result in some clusters being accurate while others were not, leading to inconsistent results. Please refer to some example silhouette plots provided.

## Number of Cluster=5
<img width="627" alt="silhouette n=5" src="https://user-images.githubusercontent.com/109235609/234433669-3f5f165e-3c6e-4d90-9cf1-3400ddc4b97b.png">

## Number of Cluster=25
<img width="637" alt="silhouette n=25" src="https://user-images.githubusercontent.com/109235609/234433704-870eefb6-0118-40a6-b905-e8331218afbc.png">

## Number of Cluster=15
![silhouette n=15](https://user-images.githubusercontent.com/109235609/234435008-3c80ced6-a01d-406f-8a3c-2bb46a6a88b3.png)


I gave up on the idea of using 5 clusters because the results did not make any sense. After that, I considered using 10 to 15 clusters to replicate the number of aisles found in an average supermarket. Eventually, I settled on 15 clusters since it yielded a slightly higher average coefficient without being too complicated. As for the content of the clusters, I choose to look at the most common words for each, while also making sure to scan the actual content as well. There were very specific clusters for prepared salads, ice cream, fish and nut butters.
