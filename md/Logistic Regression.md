# Logistic Regression

Logistic Regression is a **supervised machine learning algorithm** used for **classification**, mainly **binary classification**.

Examples:

* Spam vs Not Spam
* Pass vs Fail
* Yes vs No

Although it is called *regression*, it is a **classification algorithm**.

**Why Not Linear Regression?**

Linear Regression produces outputs from **−∞ to +∞**, which cannot represent probabilities.

Classification needs values between **0 and 1**.

Logistic Regression solves this using the **Sigmoid function**.


---

## Table of Contents
- [Logistic Regression](#logistic-regression)
  - [Table of Contents](#table-of-contents)
  - [Sigmoid (Logistic) Function](#sigmoid-logistic-function)
  - [4. Logistic Regression Model](#4-logistic-regression-model)
    - [Step 2: Apply Sigmoid](#step-2-apply-sigmoid)
  - [5. Decision Boundary](#5-decision-boundary)
  - [6. Cost Function (Log Loss)](#6-cost-function-log-loss)
  - [7. Training Using Gradient Descent](#7-training-using-gradient-descent)
    - [Weight Update Rule:](#weight-update-rule)
    - [Bias Update Rule:](#bias-update-rule)
  - [8. Types of Logistic Regression](#8-types-of-logistic-regression)
    - [Binary Logistic Regression](#binary-logistic-regression)
    - [Multinomial Logistic Regression](#multinomial-logistic-regression)
    - [Ordinal Logistic Regression](#ordinal-logistic-regression)
  - [9. Regularization](#9-regularization)
    - [L1 Regularization (Lasso)](#l1-regularization-lasso)
    - [L2 Regularization (Ridge)](#l2-regularization-ridge)
  - [10. Assumptions](#10-assumptions)
  - [11. Advantages](#11-advantages)
  - [12. Disadvantages](#12-disadvantages)
  - [13. Logistic vs Linear Regression](#13-logistic-vs-linear-regression)
  - [14. Summary](#14-summary)





## Sigmoid (Logistic) Function

The sigmoid function maps any real number to a value between **0 and 1**.

$$
\sigma(z) = \frac{1}{1 + e^{-z}}
$$

Where:

$$
z = w_1x_1 + w_2x_2 + \dots + w_nx_n + b
$$

<img src="../img/sigmoid.gif" width="600">


---

## 4. Logistic Regression Model

**Linear Combination**

$$
z = w^T x + b
$$

### Step 2: Apply Sigmoid

$$
\hat{y} = \frac{1}{1 + e^{-z}}
$$

Where:

* $x$ = input features
* $w$ = weights
* $b$ = bias
* $\hat{y}$ = predicted probability

---

## 5. Decision Boundary

To convert probability into a class label:

$$
\hat{y} \geq 0.5 \Rightarrow \text{Class 1}
$$

$$
\hat{y} < 0.5 \Rightarrow \text{Class 0}
$$

This forms a **decision boundary**.

---

## 6. Cost Function (Log Loss)

Logistic Regression uses **Binary Cross-Entropy Loss**.

$$
J(w,b) = -\frac{1}{m} \sum_{i=1}^{m}
\left[
y_i \log(\hat{y}_i) + (1 - y_i)\log(1 - \hat{y}_i)
\right]
$$

Why this loss?

* Penalizes confident wrong predictions
* Convex function
* Works well with probabilities

---

## 7. Training Using Gradient Descent

We minimize the cost function by updating parameters.

### Weight Update Rule:

$$
w := w - \alpha \frac{\partial J}{\partial w}
$$

### Bias Update Rule:

$$
b := b - \alpha \frac{\partial J}{\partial b}
$$

Where:

* $\alpha$ = learning rate

---

## 8. Types of Logistic Regression

### Binary Logistic Regression

* Two classes (0, 1)

### Multinomial Logistic Regression

* More than two classes
* Uses **Softmax**

### Ordinal Logistic Regression

* Ordered categories

---

## 9. Regularization

To prevent overfitting:

### L1 Regularization (Lasso)

$$
J = J + \lambda \sum |w|
$$

### L2 Regularization (Ridge)

$$
J = J + \lambda \sum w^2
$$

---

## 10. Assumptions

1. Binary dependent variable
2. Independent observations
3. No multicollinearity
4. Linear relationship between features and log-odds
5. Large sample size

---

## 11. Advantages

* Simple and efficient
* Probabilistic output
* Easy to interpret
* Fast training

---

## 12. Disadvantages

* Cannot model complex non-linear data
* Sensitive to outliers
* Requires feature engineering

---

## 13. Logistic vs Linear Regression

| Feature       | Linear Regression | Logistic Regression |
| ------------- | ----------------- | ------------------- |
| Output        | Continuous        | Probability         |
| Loss Function | MSE               | Log Loss            |
| Use Case      | Prediction        | Classification      |

---

## 14. Summary

Logistic Regression is a classification algorithm that uses a sigmoid function to model probabilities. It learns parameters by minimizing log loss using gradient descent and is widely used due to its simplicity and interpretability.

---

If you want:

* **README with diagrams**
* **Python code section**
* **LaTeX-heavy version**
* **Interview / exam notes**

Just say the word 🚀
