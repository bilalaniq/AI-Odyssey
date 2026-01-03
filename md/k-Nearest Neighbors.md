# k-Nearest Neighbors (k-NN)

**k-Nearest Neighbors (k-NN)** is a **supervised machine learning algorithm** used for:

* **Classification** (predicting a category)
* **Regression** (predicting a number)

It works by:

> Looking at the **k closest data points** to a new input and making a prediction based on them.

**Key idea:**

> *“Tell me who your neighbors are, and I’ll tell you who you are.”*

---


## Table of Contents
- [k-Nearest Neighbors (k-NN)](#k-nearest-neighbors-k-nn)
  - [Table of Contents](#table-of-contents)
  - [Why is it called “k-Nearest”?](#why-is-it-called-k-nearest)
  - [How k-NN Works](#how-k-nn-works)
  - [Feature Scaling](#feature-scaling)
  - [Advantages of k-NN](#advantages-of-k-nn)
  - [Disadvantages of k-NN](#disadvantages-of-k-nn)
  - [When Should You Use k-NN?](#when-should-you-use-k-nn)
  - [Real-World Applications](#real-world-applications)

---



## Why is it called “k-Nearest”?

* **k** → number of neighbors considered
* **Nearest** → closest data points
* **Neighbors** → points already in the dataset

Example:

* If `k = 3`, the algorithm looks at the **3 closest points** to make a decision.


<img src="https://miro.medium.com/v2/resize:fit:1400/1*_r-PcPEK7css8UDINDgkgg.gif" width="600">


---

## How k-NN Works

**Store the training data**

k-NN **does not build a model**.
It simply **stores all the training data**.

This is why k-NN is called a:

> **Lazy learning algorithm**


**Choose the value of k**

* Small k → sensitive to noise
* Large k → smoother, more stable predictions

Common choices:

* `k = 3, 5, 7`
* Usually an **odd number** (to avoid ties in classification)


**Calculate distance**

For a new data point, calculate its distance to **every point** in the training set.

Common distance measures:

1. **Euclidean Distance (most common)**

$$
d = \sqrt{(x_1 - y_1)^2 + (x_2 - y_2)^2}
$$

Used when data is numeric and continuous.

2. **Manhattan Distance**

$$
d = |x_1 - y_1| + |x_2 - y_2|
$$

3. **Minkowski Distance**

$$
d = \left(\sum_{i=1}^{n} |x_i - y_i|^p\right)^{\frac{1}{p}}
$$

General form that includes Euclidean and Manhattan.

* $p$=2 → Euclidean distance
* $p$=1 → Manhattan distance


**Find the k nearest neighbors**

* Sort distances
* Pick the **k smallest distances**


**Make a prediction**

**For Classification**:

* Use **majority voting**
* The class that appears most among neighbors is chosen

Example:

```
Neighbors: [Cat, Dog, Dog]
Prediction: Dog
```

**For Regression**:

* Take the **average** of the k neighbors’ values

Example:

```
Neighbors' values: [10, 12, 14]
Prediction: 12
```

---


## Feature Scaling

k-NN uses **distance**, so features must be on the same scale.

**Example problem**:

* Age: 10–60
* Salary: 10,000–1,000,000

Salary dominates distance ❌

**Solution**:

Use **Normalization** or **Standardization**

* Min-Max Scaling
* Z-Score Scaling

---

## Advantages of k-NN

* Simple and intuitive
* No training phase
* Works well with small datasets
* Can model complex decision boundaries

---

## Disadvantages of k-NN

* Slow for large datasets
* High memory usage
* Sensitive to noise
* Requires feature scaling
* Performance depends heavily on k


## When Should You Use k-NN?

Use k-NN when:

* Dataset is small to medium
* Features are meaningful
* Decision boundary is irregular
* You want a simple baseline model

Avoid k-NN when:

* Dataset is very large
* Real-time predictions are required
* Features are high-dimensional (curse of dimensionality)

**Curse of Dimensionality**

As dimensions increase:

* Distances become less meaningful
* All points appear “far away”

This reduces k-NN performance.

---

## Real-World Applications

* Recommendation systems
* Handwriting recognition
* Image classification
* Pattern recognition
* Medical diagnosis (with care)

---