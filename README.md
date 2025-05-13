# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm

1. Import pandas and matplotlib.pyplot

2. Read the dataset and transform it

3. Import KMeans and fit the data in the model

4. Plot the Cluster graph

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.

Developed by: Rohit GP
RegisterNumber:  212224220082
*/

import pandas as pd
import matplotlib.pyplot as plt

data = pd.read_csv(r"C:\Users\admin\Downloads\Mall_Customers.csv")
data.head()
data.info()
data.isnull().sum()

from sklearn.cluster import KMeans
wcss = []

for i in range(1,11):
    kmeans = KMeans(n_clusters=i, init = "k-means++")
    kmeans.fit(data.iloc[:,3:])
    wcss.append(kmeans.inertia_)

plt.plot(range(1,11),wcss)
plt.xlabel("No. of clusters")
plt.ylabel("wcss")
plt.title("Elbow method")

km = KMeans(n_clusters=5)
km.fit(data.iloc[:,3:])

y_pred = km.predict(data.iloc[:,3:])
y_pred

data["cluster"] = y_pred

df0 = data[data["cluster"]==0]
df1 = data[data["cluster"]==1]
df2 = data[data["cluster"]==2]
df3 = data[data["cluster"]==3]
df4 = data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster 0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster 1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster 2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster 3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="cluster 4")

plt.legend()
plt.title("customer segmentation")
```

## Output:

![image](https://github.com/user-attachments/assets/996c6152-aaf3-483d-96ec-e882210be916)

![image](https://github.com/user-attachments/assets/194da1ce-07ff-41ec-9800-fb1282da325c)

![image](https://github.com/user-attachments/assets/f19b9b34-adab-4694-8ac3-1508905b520f)

![image](https://github.com/user-attachments/assets/7bbb638c-441d-4a9e-9036-ae0d7935dd82)

![image](https://github.com/user-attachments/assets/93cf9092-40da-426a-b25f-41f9684765b4)

![image](https://github.com/user-attachments/assets/99cc693a-c4c5-4547-a4a6-49bdd21254ac)

![image](https://github.com/user-attachments/assets/9c731ed8-132a-4d30-a79e-ee48b7d218d8)


## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
