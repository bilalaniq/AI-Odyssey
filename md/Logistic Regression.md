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
  - [Decision Boundary](#decision-boundary)
  - [Cost Function (Log Loss)](#cost-function-log-loss)
  - [**Gradient Descent for Logistic Regression**](#gradient-descent-for-logistic-regression)
  - [Types of Logistic Regression](#types-of-logistic-regression)
  - [Assumptions](#assumptions)
  - [Advantages](#advantages)
  - [Disadvantages](#disadvantages)
  - [Evaluation metrics for classification](#evaluation-metrics-for-classification)
    - [Confusion Matrix](#confusion-matrix)
    - [Accuracy](#accuracy)
    - [Precision](#precision)
    - [Recall (also called **Sensitivity** or **True Positive Rate**)](#recall-also-called-sensitivity-or-true-positive-rate)
    - [F1 Score](#f1-score)



## Sigmoid (Logistic) Function

The **sigmoid function** is a mathematical function used in logistic regression to convert any real-valued number into a value between **0 and 1**. Because of this property, it is ideal for **binary classification**, where outputs represent probabilities.

$$
\sigma(z) = \frac{1}{1 + e^{-z}}
$$

**Why sigmoid is used**

* The output is always in the range **(0, 1)**
* It can be interpreted as a **probability**
* It is smooth and differentiable, which helps during model training

**Behavior of the sigmoid function**

* If $z \rightarrow +\infty$, then $\sigma(z) \rightarrow 1$
* If $z \rightarrow -\infty$, then $\sigma(z) \rightarrow 0$
* If $z = 0$, then $\sigma(z) = 0.5$

This means:

* Large positive $z$ → high probability of class 1
* Large negative $z$ → low probability of class 1

**Input to the Sigmoid Function**

$$
z = w_1x_1 + w_2x_2 + \dots + w_nx_n + b
$$

Here, $z$ is a **linear combination** of the input features and model parameters.

* Each feature $x_i$ is multiplied by its corresponding weight $w_i$
* All weighted features are summed
* A bias term $b$ is added to shift the result

This value $z$ can be any real number (positive, negative, or zero).

---

<img src="../img/sigmoid.gif" width="600">

The graph shows the **S-shaped curve** of the sigmoid function, illustrating how inputs are smoothly mapped to probabilities.


**Logistic Regression Model**

Logistic regression is a **linear model** combined with a **non-linear activation function (sigmoid)** to perform binary classification.

---

**Linear Combination**

$$
z = w^T x + b
$$

This is the **dot product** of the weight vector and the input feature vector plus the bias.

**Expanded form:**

$$
z = w_1x_1 + w_2x_2 + \dots + w_nx_n + b
$$

Where:

* $w^T$ is the transpose of the weight vector
* $x$ is the feature vector
* $b$ allows the decision boundary to shift

This step creates a **linear decision boundary** in the feature space.


**Apply Sigmoid**

$$
\hat{y} = \frac{1}{1 + e^{-z}}
$$

The sigmoid function transforms the linear output $z$ into a **probability**.

* $\hat{y}$ close to **1** → model predicts class 1
* $\hat{y}$ close to **0** → model predicts class 0

Typically:

* If $\hat{y} \ge 0.5$, predict class 1
* If $\hat{y} < 0.5$, predict class 0


**Where:**

* **$x$** = input features

* **$w$** = weights (learned during training)

* **$b$** = bias (intercept)

* **$\hat{y}$** = predicted probability of the positive class

---


## Decision Boundary

To convert probability into a class label:

$$
\hat{y} \geq 0.5 \Rightarrow \text{Class 1}
$$

$$
\hat{y} < 0.5 \Rightarrow \text{Class 0}
$$

This forms a **decision boundary**.

<img src="https://dorianbrown.dev/assets/images/logreg/prob_threshold.png" width="600">


<br>

Decision boundaries are **not necessarily straight lines**. They can be curves, circles, or more complex shapes depending on the features.

heres an simple example

**Circular Decision Boundary**

**Features**

* $(x_1, x_2)$ (two numbers for each point)

**Equation for boundary**

$$
z = x_1^2 + x_2^2 - 1
$$

* Decision boundary: $z = 0 \Rightarrow x_1^2 + x_2^2 = 1$
* **This is a circle**
* Points **outside the circle** → Class 1
* Points **inside the circle** → Class 0

**Sigmoid (probability)**

$$
\hat{y} = \frac{1}{1 + e^{-z}}
$$

* Sigmoid just converts $z$ into a **probability** between 0 and 1
* The **shape of the boundary** comes from $z$, not sigmoid

---

**Example Points**

| Point     | $x_1^2 + x_2^2$   | Class |
| --------- | ----------------- | ----- |
| (1,0)     | 1                 | 1     |
| (0,1)     | 1                 | 1     |
| (0.5,0.5) | 0.25 + 0.25 = 0.5 | 0     |
| (0,0)     | 0                 | 0     |


<img src="https://media.geeksforgeeks.org/wp-content/uploads/20190503112448/Logistics_Regression2-3.jpg" width="400">


---

## Cost Function (Log Loss)

Logistic Regression uses **Binary Cross-Entropy Loss**.


$$
J(w,b) = -\frac{1}{m} \sum_{i=1}^{m}
\left[
y_i \log(\hat{y}_i) + (1 - y_i)\log(1 - \hat{y}_i)
\right]
$$

* $m$ is the number of training examples
* $y_i \in {0,1}$ is the true label for example $i$
* $\hat{y}_i$ is the predicted probability that $y_i = 1$
* The loss is computed **per example** and then averaged

**How the formula works:**

* If $y_i = 1$, the loss becomes:
  $$
  -\log(\hat{y}_i)
  $$
  The loss is small when $\hat{y}_i$ is close to $1$ and large when $\hat{y}_i$ is close to $0$.

* If $y_i = 0$, the loss becomes:
  $$
  -\log(1 - \hat{y}_i)
  $$
  The loss is small when $\hat{y}_i$ is close to $0$ and large when $\hat{y}_i$ is close to $1$.

This formula measures how well the predicted probabilities $\hat{y}_i$ match the true labels $y_i$.

---


## **Gradient Descent for Logistic Regression**

Gradient Descent is an algorithm used to find the best-fitting **decision boundary** in logistic regression by minimizing the **log loss (binary cross-entropy)**.

Start with initial guesses for the weights $(w)$ and bias $(b)$.

Predict probabilities using the sigmoid function:
$$
\hat{y} = \sigma(z) = \frac{1}{1 + e^{-z}}, \quad z = w^T x + b
$$

Calculate the error for each data point: the difference between the predicted probability $\hat{y}$ and the true label $y$.

Compute the gradient: the direction in which the **loss function** increases with respect to $w$ and $b$.

Update the parameters by moving them slightly in the opposite direction of the gradient to reduce the loss:
$$
w := w - \alpha \frac{\partial J}{\partial w}
$$
$$
b := b - \alpha \frac{\partial J}{\partial b}
$$

* **$J$** is the **cost (loss) function** that measures how wrong the model’s predictions are.
* **$w$** represents the **weights (parameters)** that control how input features affect the prediction.
* **$b$** is the **bias (intercept)** term that shifts the decision boundary.
* Gradient Descent updates **$w$** and **$b$** to minimize **$J$**.

Repeat the prediction, loss calculation, gradient computation, and update steps until the loss becomes as small as possible.

**Key Idea:**
Gradient Descent in logistic regression is like rolling down a hill where the “hill” is the **log loss function**. The lowest point corresponds to parameters that best separate the two classes.

The learning rate $(\alpha)$ controls how big each step is.
The process gradually finds the parameters that minimize classification error by improving probability predictions.


<img src="https://miro.medium.com/v2/1*HtR3xMvJ-rOhKoER9QWPmg.jpeg" width="400">


---

## Types of Logistic Regression

**Binary Logistic Regression**

* Two classes (0, 1)

**Multinomial Logistic Regression**

* More than two classes
* Uses **Softmax**

**Ordinal Logistic Regression**

* Ordered categories

---

## Assumptions

1. Binary dependent variable
2. Independent observations
3. No multicollinearity
4. Linear relationship between features and log-odds
5. Large sample size

---

## Advantages

* Simple and efficient
* Probabilistic output
* Easy to interpret
* Fast training

---

## Disadvantages

* Cannot model complex non-linear data
* Sensitive to outliers
* Requires feature engineering

---


## Evaluation metrics for classification

Here’s a list of common **evaluation metrics for classification**:

1. **Confusion Matrix**
2. **Accuracy**
3. **Precision**
4. **Recall (Sensitivity / True Positive Rate)**
5. **F1 Score**


### Confusion Matrix

**Definition:**
A **confusion matrix** is a table that shows the performance of a classification model by comparing **predicted labels** with **actual labels**. It helps you see not just the correct predictions but also the types of errors.

**Structure (Binary Classification):**

|                     | Predicted Positive  | Predicted Negative  |
| ------------------- | ------------------- | ------------------- |
| **Actual Positive** | True Positive (TP)  | False Negative (FN) |
| **Actual Negative** | False Positive (FP) | True Negative (TN)  |

**Explanation of Terms:**

* **TP (True Positive):** Correctly predicted positive
* **TN (True Negative):** Correctly predicted negative
* **FP (False Positive):** Incorrectly predicted positive
* **FN (False Negative):** Incorrectly predicted negative

**Use case:**

* Provides the foundation to calculate **Accuracy, Precision, Recall, F1 Score**.
* Useful for **analyzing model errors**.

---



### Accuracy

**Definition:**
Accuracy measures the proportion of correctly predicted instances (both positive and negative) out of all predictions.

$$
\text{Accuracy} = \frac{\text{Number of Correct Predictions}}{\text{Total Number of Predictions}}
$$

Or using the confusion matrix:

$$
\text{Accuracy} = \frac{TP + TN}{TP + TN + FP + FN}
$$

Where:

* **TP** = True Positives
* **TN** = True Negatives
* **FP** = False Positives
* **FN** = False Negatives

**Use case:**

* Good when classes are **balanced**.
* Not reliable for **imbalanced datasets** (one class dominates).

---

### Precision

**Definition:**
Precision measures how many of the instances predicted as positive are actually positive. It tells us the **accuracy of positive predictions**.

$$
\text{Precision} = \frac{TP}{TP + FP}
$$

Where:

* **TP** = True Positives
* **FP** = False Positives

**Use case:**

* Important when **false positives are costly**.
* Example: Email spam detection → you don’t want to mark important emails as spam.

---

### Recall (also called **Sensitivity** or **True Positive Rate**)

**Definition:**
Recall measures how many of the actual positive instances were correctly predicted. It tells us the **ability of the model to find all positive cases**.

$$
\text{Recall} = \frac{TP}{TP + FN}
$$

Where:

* **TP** = True Positives
* **FN** = False Negatives

**Use case:**

* Important when **missing a positive case is costly**.
* Example: Disease detection → you want to catch as many sick patients as possible.

---

### F1 Score

**Definition:**
F1 Score is the **harmonic mean of Precision and Recall**. It balances the two metrics into a single score, especially useful when you need to consider both **false positives** and **false negatives**.

$$
\text{F1 Score} = 2 \cdot \frac{\text{Precision} \times \text{Recall}}{\text{Precision} + \text{Recall}}
$$

**Use case:**

* Useful when the dataset is **imbalanced**.
* Helps to find a balance between Precision and Recall rather than considering them separately.

---








