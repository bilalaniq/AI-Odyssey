# Naïve Bayes Classifier

A **Naïve Bayes classifier** is a **supervised machine learning algorithm** used for **classification**.

* It is **probabilistic** → based on **Bayes’ Theorem**
* It is **naïve** → assumes **features are conditionally independent**
* It is a **classifier** → predicts a **class label**

👉 Despite its “naïve” assumption, it performs **very well** in many real-world tasks.

---

## Table of Contents
- [Naïve Bayes Classifier](#naïve-bayes-classifier)
  - [Table of Contents](#table-of-contents)
  - [Why is it Called “Naïve”?](#why-is-it-called-naïve)
  - [Bayes’ Theorem (Core Formula)](#bayes-theorem-core-formula)
  - [Naïve Independence Assumption](#naïve-independence-assumption)
  - [Final Naïve Bayes Formula](#final-naïve-bayes-formula)
  - [Types of Naïve Bayes Classifiers](#types-of-naïve-bayes-classifiers)
  - [Laplace Smoothing (Important!)](#laplace-smoothing-important)
  - [Advantages of Naïve Bayes](#advantages-of-naïve-bayes)
  - [Disadvantages of Naïve Bayes](#disadvantages-of-naïve-bayes)
  - [Applications of Naïve Bayes](#applications-of-naïve-bayes)
  - [Why Naïve Bayes Still Works Well?](#why-naïve-bayes-still-works-well)


---




## Why is it Called “Naïve”?

Because it makes a **strong and unrealistic assumption**:

> **All features are independent of each other given the class**

Example:
In spam detection, Naïve Bayes assumes:

* The word **“free”** is independent of **“win”**
* The word **“win”** is independent of **“money”**

This is clearly **not true**, but the model still works well in practice.

---

## Bayes’ Theorem (Core Formula)

Naïve Bayes is based on **Bayes’ Theorem**:

$$
P(C|X) = \frac{P(X|C),P(C)}{P(X)}
$$

Where:

* (C) = Class (e.g., Spam / Not Spam)
* (X) = Input features
* (P(C)) = **Prior probability** of class
* (P(X|C)) = **Likelihood**
* (P(C|X)) = **Posterior probability**
* (P(X)) = Evidence (normalizing constant)


---

**Understanding Each Term**

* `P(C|X)`: `Posterior probability` i.e., probability of C given X
  * Estimate with the given X what is the probability of the class being C?

* `P(X|Y)`: `Likelihood` i.e., how likely we’d see this X if class is C
  * Calculated from given (“training”) data
  
* `P(C)`: `Prior` (belief about the class C before seeing the new X)
  * Calculated from given data

* `P(X)`: `Evidence` (or normalization term)
  * Skipped from the computation anyway!

👉 Goal: **Find the class with the highest posterior probability**


---

## Naïve Independence Assumption

Let features be:
$$
X = (x_1, x_2, x_3, ..., x_n)
$$

Naïve Bayes assumes:
$$
P(X|C) = P(x_1|C)\times P(x_2|C)\times ... \times P(x_n|C)
$$

This makes computation:

* **Fast**
* **Simple**
* **Scalable**

---

## Final Naïve Bayes Formula

$$
P(C|X) \propto P(C) \prod_{i=1}^{n} P(x_i|C)
$$

The predicted class is:

$$
\hat{C} = \arg\max_C \left[ P(C)\prod P(x_i|C) \right]
$$

---

**How Naïve Bayes Works**

**Training Phase:**

1. Calculate **prior probability** for each class
2. Calculate **likelihood** of each feature given each class

**Testing Phase:**

1. For a new input, compute posterior probability for each class
2. Choose class with **maximum probability**

---




## Types of Naïve Bayes Classifiers

1. **Gaussian Naïve Bayes**

  * Used for **continuous data**
  * Assumes features follow **normal distribution**
  * Example: height, weight, temperature

2. **Multinomial Naïve Bayes**

  * Used for **text classification**
  * Features are word counts
  * Example: spam detection, sentiment analysis

3. **Bernoulli Naïve Bayes**

  * Features are **binary (0/1)**
  * Example: word present or absent
  
---

## Laplace Smoothing (Important!)

Problem:

* If a feature never appears in training for a class
* Probability becomes **0**
* Entire product becomes **0**

Solution:
$$
P = \frac{count + 1}{total + k}
$$

This is called **Laplace (Add-1) smoothing**.

Before seeing data, we assume every feature has appeared once

---

## Advantages of Naïve Bayes

* Simple and easy to implement
* Very fast training and prediction
* Works well with **high-dimensional data**
* Requires **small training data**
* Performs well in text classification

---

## Disadvantages of Naïve Bayes

* Independence assumption often false
* Cannot learn interactions between features
* Poor performance if features are highly correlated

---

## Applications of Naïve Bayes

* Spam email filtering
* Sentiment analysis
* Document classification
* Medical diagnosis (basic)
* Recommendation systems
* Language detection

---

## Why Naïve Bayes Still Works Well?

* Uses **probability ranking**, not exact values
* Errors cancel out
* Class with strongest signal still wins
* Independence assumption simplifies learning

---
