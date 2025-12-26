# Linear Regression

**Linear regression** is a **supervised learning algorithm** used to **predict a continuous numerical value** by modeling a **linear relationship** between input variables and the output.

Example predictions:

* House price
* Temperature
* Salary
* Exam score

---

## 2. Basic Idea

We assume that the output (y) depends on input (x) in a **linear way**.

[
y \approx f(x)
]

Since the true function (f(x)) is unknown, we **approximate** it using a hypothesis:

[
h(x) = mx + b
]

Where:

* (m) = slope (weight)
* (b) = intercept (bias)

---

## 3. Hypothesis Function

### Simple Linear Regression (one input)

[
h(x) = mx + b
]

* (x) → input feature
* (h(x)) → predicted output

### Multiple Linear Regression (multiple inputs)

[
h(x) = w_1x_1 + w_2x_2 + \dots + w_nx_n + b
]

In vector form:
[
h(x) = \mathbf{w}^T\mathbf{x} + b
]

---

## 4. Graphical Interpretation

* **Points (dots)** → training data
* **Straight line** → hypothesis
* Best line → minimizes prediction error

Each different line is a different hypothesis.

---

## 5. Cost (Loss) Function

Since predictions are rarely exact, we measure **error**.

### Mean Squared Error (MSE)

[
J(m,b) = \frac{1}{n}\sum_{i=1}^{n}(h(x_i) - y_i)^2
]

Why squared error?

* Penalizes large errors more
* Differentiable (easy to optimize)

---

## 6. Goal of Linear Regression

Find parameters (m) and (b) that **minimize the cost function**.

[
\min_{m,b} J(m,b)
]

---

## 7. How Do We Find the Best Line?

### Method 1: Gradient Descent

An **iterative optimization algorithm**.

#### Steps:

1. Initialize (m) and (b)
2. Compute error
3. Update parameters:
   [
   m := m - \alpha \frac{\partial J}{\partial m}
   ]
   [
   b := b - \alpha \frac{\partial J}{\partial b}
   ]

Where:

* (\alpha) = learning rate

Repeat until convergence.

---

### Method 2: Normal Equation (Analytical Solution)

Direct formula (no iteration):

[
\mathbf{w} = (X^TX)^{-1}X^Ty
]

Used when dataset is small.

---

## 8. Assumptions of Linear Regression

Linear regression works best when these assumptions hold:

1. **Linearity** – relationship is linear
2. **Independence** – observations are independent
3. **Homoscedasticity** – constant variance of errors
4. **Normality of errors**
5. **No multicollinearity** (for multiple inputs)

---

## 9. Types of Linear Regression

1. **Simple Linear Regression** – one input
2. **Multiple Linear Regression** – multiple inputs
3. **Polynomial Regression** – curved line using polynomial features
4. **Regularized Linear Regression**

   * Ridge (L2)
   * Lasso (L1)
   * Elastic Net

---

## 10. Evaluation Metrics

To check model performance:

* **Mean Squared Error (MSE)**
* **Root Mean Squared Error (RMSE)**
* **Mean Absolute Error (MAE)**
* **R² Score (coefficient of determination)**

---

## 11. Advantages

* Simple and easy to understand
* Fast to train
* Interpretable coefficients
* Works well with linear data

---

## 12. Limitations

* Cannot model complex non-linear patterns
* Sensitive to outliers
* Assumes linear relationship
* Poor performance if assumptions are violated

---

## 13. Real-Life Example

**Predicting house price**

Inputs:

* Size of house
* Number of rooms
* Location score

Output:

* Price

Linear regression learns how much each feature contributes to the final price.

---

## 14. One-Paragraph Exam Answer

> Linear regression is a supervised learning algorithm used to predict continuous values by fitting a straight line that minimizes the squared error between predicted and actual values. It uses a linear hypothesis function and optimizes parameters using methods like gradient descent or the normal equation.

---
