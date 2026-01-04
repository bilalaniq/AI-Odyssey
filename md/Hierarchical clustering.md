# Hierarchical Clustering

Hierarchical clustering organizes data into a **nested sequence of clusters**, where:

* Small clusters merge into larger ones **or**
* Large clusters split into smaller ones

The result is a **hierarchy** that shows relationships between data points at different levels of similarity.

---

## Table of Contents
- [Hierarchical Clustering](#hierarchical-clustering)
  - [Table of Contents](#table-of-contents)
  - [Types of Hierarchical Clustering](#types-of-hierarchical-clustering)
    - [**Agglomerative (Bottom-Up) Clustering**](#agglomerative-bottom-up-clustering)
    - [**Divisive (Top-Down) Clustering**](#divisive-top-down-clustering)
  - [Key Components of Hierarchical Clustering](#key-components-of-hierarchical-clustering)
  - [Agglomerative Clustering Algorithm](#agglomerative-clustering-algorithm)
  - [dendrogram](#dendrogram)
  - [Advantages](#advantages)
  - [Disadvantages](#disadvantages)
  - [Applications](#applications)
  - [When to Use Hierarchical Clustering](#when-to-use-hierarchical-clustering)




## Types of Hierarchical Clustering

### **Agglomerative (Bottom-Up) Clustering**

* Starts with **each data point as its own cluster**
* Repeatedly **merges the two closest clusters**
* Continues until only **one cluster** remains

![Agglomerative](https://cdn-images-1.medium.com/v2/resize:fit:640/1*ET8kCcPpr893vNZFs8j4xg.gif)


> **Most commonly used**

### **Divisive (Top-Down) Clustering**

* Starts with **all data points in one cluster**
* Recursively **splits clusters**
* Continues until each point is its own cluster



![Agglomerative](https://media.geeksforgeeks.org/wp-content/uploads/20250619174725747376/divisive_clustering.png)


⚠️ More computationally expensive and less common

---

## Key Components of Hierarchical Clustering

**Distance Metrics**

Distance metrics define **how similarity is measured**.

Common distance measures:

| Metric    | Formula                     | Use case                     |
| --------- | --------------------------- | ---------------------------- |
| Euclidean | Straight-line distance      | Continuous numerical data    |
| Manhattan | Sum of absolute differences | Grid-like data               |
| Cosine    | Angle between vectors       | Text / high-dimensional data |
| Minkowski | Generalized distance        | Flexible metric              |

Example (Euclidean distance):

$$
d(x,y) = \sqrt{\sum (x_i - y_i)^2}
$$

---

**Linkage Criteria**

* **Single Linkage:**
  The distance between two clusters is defined as the minimum distance between any pair of points from the two clusters. This method is simple but often leads to the formation of long, chain-like clusters.

<img src="https://media.geeksforgeeks.org/wp-content/uploads/20190718124314/single2.png" width="300">



* **Complete Linkage:**
  The distance between two clusters is taken as the maximum distance between any pair of points belonging to different clusters. It generally produces compact and well-separated clusters.

<img src="https://media.geeksforgeeks.org/wp-content/uploads/20250418122739796024/Complete-Linkage.jpg" width="300">



* **Average Linkage:**
  In average linkage, the distance between two clusters is found by taking the average of the distances between all points in one cluster and all points in the other. This approach creates balanced clusters and avoids the extreme effects of single and complete linkage.

<img src="https://media.geeksforgeeks.org/wp-content/uploads/20250422134424561127/average1.png" width="300">

---

## Agglomerative Clustering Algorithm

1. Treat each data point as a **separate cluster**
2. Compute the **distance matrix**
3. Find the **two closest clusters**
4. Merge them into a single cluster
5. Update the distance matrix
6. Repeat until only one cluster remains

---

## dendrogram

A **dendrogram** is a tree diagram that shows:

* When clusters merge
* The distance at which merges occur

**How to choose the number of clusters**

* Draw a **horizontal cut** across the dendrogram
* The number of vertical lines intersected = number of clusters

🔑 Larger vertical gaps indicate more meaningful cluster separations.

![dendrogram](https://mlkeww00jjj8.i.optimole.com/w:380/h:422/q:mauto/dpr:2.6/f:best/https://www.displayr.com/wp-content/uploads/2018/03/What-is-a-Dendrogram.png)


---



## Advantages

* No need to pre-define number of clusters
* Produces interpretable hierarchy
* Works well for small datasets
* Can use any distance metric

---

## Disadvantages

* Computationally expensive (O(n³))
* Not suitable for very large datasets
* Sensitive to noise and outliers
* Once merged/split, decisions cannot be undone

---

## Applications

* Biology (gene expression analysis)
* Document clustering
* Image segmentation
* Market segmentation
* Social network analysis

---

## When to Use Hierarchical Clustering

* Dataset is small or medium
* You want a **hierarchical relationship**
* Number of clusters is unknown
* Interpretability matters

---
