| Feature              | **Hierarchical Clustering**                      | **K-Means Clustering**                   |
| -------------------- | ------------------------------------------------ | ---------------------------------------- |
| Type                 | Unsupervised learning                            | Unsupervised learning                    |
| Basic Idea           | Builds a hierarchy of clusters                   | Partitions data into K clusters          |
| Cluster Structure    | Tree-like (hierarchical)                         | Flat (no hierarchy)                      |
| Number of Clusters   | Not required in advance                          | Must be specified beforehand             |
| Output               | Dendrogram + clusters                            | Only final clusters                      |
| Approach             | Agglomerative (bottom-up) or Divisive (top-down) | Iterative centroid-based                 |
| Distance Calculation | Uses distance metrics + linkage criteria         | Uses distance to centroids               |
| Cluster Shape        | Can find irregular shapes                        | Best for spherical clusters              |
| Interpretability     | High (due to dendrogram)                         | Moderate                                 |
| Scalability          | Poor for large datasets                          | Very good for large datasets             |
| Time Complexity      | High (O(n³))                                     | Lower (O(n × k × iterations))            |
| Sensitivity to Noise | Sensitive to outliers                            | Sensitive to outliers                    |
| Reversibility        | Once merged, cannot be undone                    | Can reassign points during iterations    |
| Initialization       | No random initialization                         | Random centroid initialization           |
| Stability            | Deterministic (same result every time)           | Can vary due to random start             |
| Memory Usage         | High                                             | Low                                      |
| Preferred Data Size  | Small to medium datasets                         | Large datasets                           |
| Distance Metrics     | Flexible (Euclidean, Manhattan, etc.)            | Mostly Euclidean                         |
| Real-world Uses      | Gene analysis, document clustering               | Image compression, customer segmentation |



<img src="https://miro.medium.com/v2/1*VS4sVTr6HBh-lEQ_Z8zHsg.png" width="600">