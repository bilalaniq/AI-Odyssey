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
  - [Cost Function](#cost-function)
  - [3. Key Differences](#3-key-differences)
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

## Cost Function

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

<video width="520" height="300" controls>
  <source src="../img/sse.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>


---

## 3. Key Differences

| Feature            | Loss Function                                | Cost Function                                          |
| ------------------ | -------------------------------------------- | ------------------------------------------------------ |
| Measures error for | **Single training example**                  | **All training examples (average)**                    |
| Used for           | Understanding prediction error for one point | Optimizing the model parameters                        |
| Example in LR      | $(\hat{y}-y)^2$                              | $\frac{1}{m}\sum_{i=1}^{m}(\hat{y}^{(i)}-y^{(i)})^2$  |

---






































































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
