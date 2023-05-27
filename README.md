# Implementation-of-K-Means-Clustering-for-Customer-Segmentation
## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Import the required libraries.
2. Read the data set and find the number of null data.
3. Import KMeans from sklearn.clusters library package.
4. Find the y_pred .
5. Plot the clusters in graph.

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Keerthika N
RegisterNumber: 212221230049
*/
```
```
import pandas as pd
import matplotlib.pyplot as plt
data=pd.read_csv("Mall_Customers.csv")
data.head()
data.info()
data.isnull().sum()

from sklearn.cluster import KMeans
wcss=[] 

for i in range(1,11):
  kmeans=KMeans(n_clusters=i,init="k-means++")
  kmeans.fit(data.iloc[:,3:])
  wcss.append(kmeans.inertia_)
  
plt.plot(range(1,11),wcss)
plt.xlabel("No of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")

km=KMeans(n_clusters = 5)
km.fit(data.iloc[:,3:])

y_pred = km.predict(data.iloc[:,3:])
y_pred

data["cluster"]= y_pred
df0=data[data["cluster"]==0]
df1=data[data["cluster"]==1]
df2=data[data["cluster"]==2]
df3=data[data["cluster"]==3]
df4=data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="cluster4")
plt.legend()
plt.title("Customer Segments")
```

## Output:
* data.head() function

![1](https://github.com/KeerthikaNagarajan/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/93427089/8d224db5-8727-4f08-b4d6-d2074f98626e)

* data.info()

![2](https://github.com/KeerthikaNagarajan/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/93427089/3ca2fec4-6d6a-41d1-9031-0da74d3dea5d)

* data.isnull().sum() function

![3](https://github.com/KeerthikaNagarajan/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/93427089/65f2dde0-ef97-4dd6-a20c-60cd0de5885c)

* Elbow method Graph

![4](https://github.com/KeerthikaNagarajan/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/93427089/2ece701c-c50e-40c7-b711-c9a48a9f290c)

* KMeans clusters

![5](https://github.com/KeerthikaNagarajan/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/93427089/0acee80e-357b-4d67-8cb8-7ccf8fbc1013)

* Customer segments Graph

![6](https://github.com/KeerthikaNagarajan/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/93427089/457b88c4-a766-4abe-99ed-1894b6a8a5c4)

## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
