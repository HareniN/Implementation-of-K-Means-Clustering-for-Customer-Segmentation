# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm

1.Import necessary libraries: pandas for data manipulation and matplotlib.pyplot for visualization.

2.Load the customer data from a CSV file into a pandas DataFrame

3.Perform K-means clustering using sklearn's KMeans algorithm, employing the elbow method to find the optimal number of clusters.

4.Fit a KMeans model with 5 clusters to the data.

5.Predict cluster labels for each data point and add them to the DataFrame.

6.Visualize the customer segments by plotting their annual income against spending score, coloring points by cluster membership.

## Program:

/*
Program to implement the K Means Clustering for Customer Segmentation.

Developed by: Hareni N

RegisterNumber: 212224040096
*/

```
import pandas as pd
import matplotlib.pyplot as plt
data=pd.read_csv("/content/Mall_Customers.csv")
data

data.head()

data.info()

data.isnull().sum()

from sklearn.cluster import KMeans
wcss=[]
for i in range(1,11):
  Kmeans=KMeans(n_clusters = i,init = "k-means++")
  Kmeans.fit(data.iloc[:,3:])
  wcss.append(Kmeans.inertia_)
plt.plot(range(1, 11), wcss[:10])
plt.xlabel("No. of Clusters")
plt.ylabel("WCSS")
plt.title("Elbow Method")
plt.show()

km=KMeans(n_clusters = 5)
km.fit(data.iloc[:,3:])
y_pred=km.predict(data.iloc[:,3:])
y_pred
data["cluster"]=y_pred
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

<img width="616" height="503" alt="image" src="https://github.com/user-attachments/assets/9c890ad8-7b94-43e3-bc96-c1a2cfb04e97" />
_______________________________________________________________________________________________________________________________________

<img width="606" height="262" alt="image" src="https://github.com/user-attachments/assets/72c64d7d-4e30-428a-8c44-6c9b9a6cc536" />
_______________________________________________________________________________________________________________________________________

<img width="467" height="276" alt="image" src="https://github.com/user-attachments/assets/480cb3dd-c906-4adf-af16-bb7d998f9404" />
_______________________________________________________________________________________________________________________________________

<img width="394" height="271" alt="image" src="https://github.com/user-attachments/assets/71aa6a8c-4c9b-45df-a948-32437747925b" />
_______________________________________________________________________________________________________________________________________

<img width="687" height="691" alt="Screenshot 2026-02-26 152613" src="https://github.com/user-attachments/assets/d70ad5c6-3444-4af9-b1bc-166ea44303cc" />
_______________________________________________________________________________________________________________________________________

<img width="766" height="745" alt="Screenshot 2026-02-26 152650" src="https://github.com/user-attachments/assets/a7f02b40-7a06-4e69-bdd9-0683dd9733d7" />

## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
