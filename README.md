# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1.Import Required Libraries

2.Load and Explore the Dataset

3.Select Features for Clustering

4.Calculate WCSS (Within-Cluster Sum of Squares)

5.Plot the Elbow Graph

6.Apply K-Means Clustering with Optimal Clusters

7.Segment Data Based on Clusters

8.Visualize the Clusters

9.Analyze and Interpret Results
## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: HARIPRASHAAAD RA
RegisterNumber:  212223040060
*/
```
```
import pandas as p
import matplotlib.pyplot as py

data = p.read_csv("Mall_Customers.csv")
data.head()


data.info()

from sklearn.cluster import KMeans
wcss = []
for i in range(1, 11):
    kmeans = KMeans(n_clusters=i, init="k-means++")
    kmeans.fit(data.iloc[:, 3:])
    wcss.append(kmeans.inertia_)



py.plot(range(1, 11), wcss)
py.xlabel("No. of cluster")
py.ylabel("wcss")
py.title("Elbow method")
py.show()



km = KMeans(n_clusters=5)
km.fit(data.iloc[:, 3:])

y_pred = km.predict(data.iloc[:, 3:])
y_pred



data["clusters"] = y_pred

df0 = data[data["clusters"] == 0]
df1 = data[data["clusters"] == 1]
df2 = data[data["clusters"] == 2]
df3 = data[data["clusters"] == 3]
df4 = data[data["clusters"] == 4]

py.scatter(df0["Annual Income (k$)"], df0["Spending Score (1-100)"], color="gold")
py.scatter(df1["Annual Income (k$)"], df1["Spending Score (1-100)"], color="pink")
py.scatter(df2["Annual Income (k$)"], df2["Spending Score (1-100)"], color="green")
py.scatter(df3["Annual Income (k$)"], df3["Spending Score (1-100)"], color="blue")
py.scatter(df4["Annual Income (k$)"], df4["Spending Score (1-100)"], color="red")
```
## Output:
![image](https://github.com/user-attachments/assets/28ac5842-f330-47ed-b69b-7794aef23bc2)
![image](https://github.com/user-attachments/assets/7bca2cd7-5c81-4ada-8ed1-d9098578b7ad)
![image](https://github.com/user-attachments/assets/f0c1af45-2b67-4523-a544-3e697ee4ea68)
![image](https://github.com/user-attachments/assets/5912269e-09f3-45d2-bf3d-092556c1b1e2)
![image](https://github.com/user-attachments/assets/cb4cb82f-6c4e-4788-a03c-6181a5f0ed89)
![image](https://github.com/user-attachments/assets/709915ee-acb9-4f50-ab9d-4caa23e388f3)


## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
