# supervised learning

## Table of Contents
- [supervised learning](#supervised-learning)
  - [Table of Contents](#table-of-contents)
  - [Hypothesis \& Hypothesis Space](#hypothesis--hypothesis-space)
  - [Bias and Variance](#bias-and-variance)
    - [Bias](#bias)
    - [Variance](#variance)
    - [Underfitting vs Overfitting](#underfitting-vs-overfitting)
  - [supervised learning tasks](#supervised-learning-tasks)
  - [Supervised Learning Algorithms](#supervised-learning-algorithms)
    - [**Parametric Algorithms**](#parametric-algorithms)
    - [**Non-Parametric Algorithms**](#non-parametric-algorithms)



## Hypothesis & Hypothesis Space

* A **hypothesis** is **one rule or formula** used by a model to make predictions.
* It is the model’s **current guess**.
* A hypothesis is written as h(x)
* It takes an input x and gives an output (prediction)

`h(x)≈f(x)`

Where:
- f(x) → true function (unknown)
- h(x) → our guessed function

**How Do We Choose a Good Hypothesis?**

If the output is a number (like price, temperature, height):

- Exact matches are unlikely
- We look for a best-fit function
- We want h(xᵢ) to be as close as possible to yᵢ



* The **hypothesis space** is **all the rules or formulas** the model is allowed to choose from.
* It is decided **before training**.

**Example:**

H={h1​,h2​,h3​,…}

This set is the hypothesis space.


<img src="https://media.geeksforgeeks.org/wp-content/uploads/20191014210129/pic82-e1571070331775.png" width="400">


- The dots (points) → training data
- The axes → input and output values
- The lines/curves → hypotheses
- Each single line = one hypothesis
- All possible lines together = hypothesis space


**Why Do We Need Hypothesis Space?**

The machine:

- Looks at training data
- Tries many hypotheses from H
- Chooses the best hypothesis that minimizes error

📌 The learning algorithm does not invent rules randomly
It only chooses from the hypothesis space.


---

## Bias and Variance

### Bias

* Bias means the model is **too simple**.
* It cannot learn patterns properly.
* This causes **underfitting**.

**Example:**
Using a straight line for curved data.

---

### Variance

* Variance means the model is **too complex**.
* It learns noise in the data.
* This causes **overfitting**.

**Example:**
A curve that passes through every data point.

### Underfitting vs Overfitting

* **Underfitting:**
  High bias, low variance
  Poor on training and test data

* **Overfitting:**
  Low bias, high variance
  Very good on training, poor on test data


**Bias–Variance Trade-off**

* Simple model → high bias, low variance
* Complex model → low bias, high variance
* **Goal:** choose a balanced model that works well on new data

**Occam’s Razor**

* Simpler models usually work better on unseen data
* But too simple is also bad


![bias & variance](https://i.sstatic.net/PbGau.png)

---

## supervised learning tasks

- classification - predict discrete classes
  - Binary classification
  - Multiclass classification

   ![b vs M](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRoxWNMHjFlyq04NqraOOkBbiCyf8kPNX0UFg&s) 

- Regression - predict continuous values instead of predicting different categories we come up with a no


<br>

<img src="https://spotintelligence.com/wp-content/uploads/2023/05/regression-vs-classification.jpg" width="400">

---


## Supervised Learning Algorithms

### **Parametric Algorithms**

* **Definition:** They assume a **fixed formula** for how input relates to output.
* **Learn:** A **fixed number of parameters** (like weights or probabilities).
* **Pros:** Fast to train and predict.
* **Cons:** Can’t capture very complex patterns.

**Examples:**

* [Linear Regression](./Linear%20Regression.md) → learns weights and bias
* [Logistic Regression](./Logistic%20Regression.md) → learns weights and bias
* [Naïve Bayes](./Naïve%20Bayes.md) → learns probabilities

**Think of it like:** Fitting a **straight line** to data.

---

### **Non-Parametric Algorithms**

* **Definition:** They **don’t assume a formula**. The model **grows with data**.
* **Learn:** Patterns directly from data; more data = more complexity.
* **Pros:** Can handle very complex patterns.
* **Cons:** Slower to train and predict.

**Examples:**

* [k-Nearest Neighbors](./k-Nearest%20Neighbors.md) (k-NN)
* Decision Trees
* Random Forests

**Think of it like:** Drawing a **curve that goes through all points**.

---

