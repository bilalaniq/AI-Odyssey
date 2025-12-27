# Linear Regression

**Linear Regression** is a **supervised learning algorithm** used to **predict a continuous numerical value** by modeling a **linear relationship** between input variables and the output.

**Example predictions**

* House price
* Temperature
* Salary
* Exam score

---

## Table of Contents
- [Linear Regression](#linear-regression)
  - [Table of Contents](#table-of-contents)
    - [**Hypothesis Function**](#hypothesis-function)
  - [Linear Regression: Loss Function vs Cost Function](#linear-regression-loss-function-vs-cost-function)
    - [Loss Function](#loss-function)
    - [Cost Function SSE (Sum of Squared Errors)](#cost-function-sse-sum-of-squared-errors)
  - [Best-Fitting Line in Linear Regression](#best-fitting-line-in-linear-regression)
    - [Normal Equation (Matrix Method)](#normal-equation-matrix-method)
    - [Gradient Descent](#gradient-descent)
  - [Assumptions of Linear Regression](#assumptions-of-linear-regression)
  - [Types of Linear Regression](#types-of-linear-regression)
  - [Evaluation Metrics](#evaluation-metrics)
  - [Advantages](#advantages)
  - [Limitations](#limitations)




**Basic Idea**

We assume that the output **y** depends on the input **x** in a **linear way**.

$$
y \approx f(x)
$$

Since the true function ( f(x) ) is unknown, we **approximate** it using a hypothesis:

$$
h(x) = mx + b
$$

Where:

* **m** → slope (weight)
* **b** → intercept (bias)


<img src="https://www.datarobot.com/wp-content/uploads/2022/02/word-image-5.png" alt="linear regression" width="400">





---

### **Hypothesis Function**

**Simple Linear Regression (one input)**

$$
h(x) = mx + b
$$

* **x** → input feature
* **h(x)** → predicted output

**Multiple Linear Regression (multiple inputs)**

$$
h(x) = w_1x_1 + w_2x_2 + \dots + w_nx_n + b
$$

**Vector form:**

$$
h(x) = \mathbf{w}^T \mathbf{x} + b
$$

---


**Goal of Linear Regression**

Find parameters **m** and **b** that **minimize the cost function**:

$$
\min_{m,b} J(m,b)
$$

---


## Linear Regression: Loss Function vs Cost Function

In **linear regression**, we try to fit a line (or hyperplane in multiple dimensions) that predicts a continuous target variable $y$ from input features $X$. To measure how good our predictions are, we use **loss functions** and **cost functions**. They are related but slightly different concepts.


### Loss Function

**Definition:** A loss function measures how well a model predicts a **single data point**. It tells us the “error” for one example.  

In linear regression, the most common loss function is the **squared error loss** (Mean Squared Error for one point):

$$
L(\hat{y}, y) = (\hat{y} - y)^2
$$

Where:  
- $\hat{y} = \theta_0 + \theta_1 x$ (predicted value)  
- $y$ = true value  
- $L(\hat{y}, y)$ = loss for **one data point**

💡 **Intuition:** The bigger the difference between predicted and actual, the bigger the loss. Squaring ensures the error is positive and penalizes larger errors more.

---

### Cost Function SSE (Sum of Squared Errors)

**Definition:** A cost function is the **average loss over the entire training dataset**. It tells us how well the model performs on all data.  

For linear regression, the most common cost function is **Mean Squared Error (MSE)** over all $m$ training examples:

$$
J(\theta_0, \theta_1) = \frac{1}{m} \sum_{i=1}^{m} (\hat{y}^{(i)} - y^{(i)})^2
$$

Where:  
- $m$ = number of training examples  
- $\hat{y}^{(i)} = \theta_0 + \theta_1 x^{(i)}$  
- $y^{(i)}$ = true value of the $i$-th example  

💡 **Intuition:** While the loss function measures error for **one example**, the cost function measures error for the **whole dataset**. During training, we minimize the cost function to find the best $\theta_0$ and $\theta_1$.


<img src="../img/sse.gif" alt="linear regression" width="400">

---

**Key Differences**

| Feature            | Loss Function                                | Cost Function                                          |
| ------------------ | -------------------------------------------- | ------------------------------------------------------ |
| Measures error for | **Single training example**                  | **All training examples (average)**                    |
| Used for           | Understanding prediction error for one point | Optimizing the model parameters                        |
| Example in LR      | $(\hat{y}-y)^2$                              | $\frac{1}{m}\sum_{i=1}^{m}(\hat{y}^{(i)}-y^{(i)})^2$  |

---


## Best-Fitting Line in Linear Regression

In **linear regression**, the goal is to find a line that best fits a set of data points.  
This line is represented as:

$$
\hat{y} = \theta_0 + \theta_1 x
$$

Where:

- $\theta_0$ = intercept  
- $\theta_1$ = slope  

The parameters are chosen to **minimize the error** between predicted values $\hat{y}$ and actual values $y$, using the **Least Squares** principle.

There are two main approaches to find the best-fitting line:

1. **Normal Equation (Matrix Method)** – analytical solution  
2. **Gradient Descent** – iterative optimization method  

---

### Normal Equation (Matrix Method)

The **Normal Equation** computes the optimal parameters directly using linear algebra.

**Formula:**

$$
\theta = (X^T X)^{-1} X^T y
$$

**Where:**

- $X$ = feature matrix (includes a column of 1’s for the intercept)  
- $y$ = vector of target values  
- $\theta$ = parameter vector $[\theta_0, \theta_1]^T$

**Intuition:**

- This method comes from minimizing the **Sum of Squared Errors (SSE)**.  
- By setting the derivative of the cost function with respect to $\theta$ to zero, we obtain the Normal Equation.  
- It provides an **exact solution** without iteration.

**Pros:**

- No learning rate required  
- Exact solution  

**Cons:**

- Computationally expensive for large datasets  
- Fails if $(X^T X)$ is non-invertible (can be fixed using the pseudo-inverse)

---

### Gradient Descent

**Gradient Descent** is an iterative algorithm that minimizes the cost function step by step.

**Cost Function (Mean Squared Error):**

$$
J(\theta_0, \theta_1) = \frac{1}{2m} \sum_{i=1}^{m} \big(\hat{y}^{(i)} - y^{(i)}\big)^2
$$

**Update Rule:**

For each parameter $\theta_j$, where $j \in \{0, 1\}$:

$$
\theta_j := \theta_j - \alpha \frac{\partial J(\theta_0, \theta_1)}{\partial \theta_j}
$$

**Where:**

- $\alpha$ = learning rate  
- $m$ = number of training examples  

**Intuition:**

- Think of the cost function as a **bowl-shaped surface**.  
- Gradient Descent moves downhill in small steps until it reaches the minimum.  
- Especially useful for **large datasets or multiple features**.

**Pros:**

- Scales well to large datasets  
- Works for multivariable regression  

**Cons:**

- Requires choosing a good learning rate  
- May converge slowly or oscillate if $\alpha$ is poorly chosen


























































## Assumptions of Linear Regression

Linear regression works best when these assumptions hold:

1. **Linearity** – relationship is linear
2. **Independence** – observations are independent
3. **Homoscedasticity** – constant variance of errors
4. **Normality of errors**
5. **No multicollinearity** (for multiple inputs)

---

## Types of Linear Regression

1. **Simple Linear Regression** – one input
2. **Multiple Linear Regression** – multiple inputs
3. **Polynomial Regression** – curved line using polynomial features
4. **Regularized Linear Regression**

   * Ridge (L2)
   * Lasso (L1)
   * Elastic Net

---

## Evaluation Metrics

To evaluate model performance:

* **Mean Squared Error (MSE)**
* **Root Mean Squared Error (RMSE)**
* **Mean Absolute Error (MAE)**
* **R² Score (Coefficient of Determination)**

---

## Advantages

* Simple and easy to understand
* Fast to train
* Interpretable coefficients
* Works well with linear data

---

## Limitations

* Cannot model complex non-linear patterns
* Sensitive to outliers
* Assumes linear relationship
* Poor performance if assumptions are violated

---
