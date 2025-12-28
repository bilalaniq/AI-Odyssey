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
  - [Assumptions of Linear Regression](#assumptions-of-linear-regression)
  - [Types of Linear Regression](#types-of-linear-regression)
  - [Advantages](#advantages)
  - [Limitations](#limitations)
  - [Performance Metrics for Linear Regression](#performance-metrics-for-linear-regression)
    - [1. Mean Absolute Error (MAE)](#1-mean-absolute-error-mae)
    - [2. Mean Squared Error (MSE)](#2-mean-squared-error-mse)
    - [3. Root Mean Squared Error (RMSE)](#3-root-mean-squared-error-rmse)
    - [4. R-squared (R²) Score](#4-r-squared-r-score)
  - [Comparison of Regression Performance Metrics](#comparison-of-regression-performance-metrics)




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


$$
J(\theta_0, \theta_1) = \frac{1}{2m} \sum_{i=1}^{m} \left( h_\theta(x^{(i)}) - y^{(i)} \right)^2
$$


where the hypothesis (prediction) function is:


$$
h_\theta(x^{(i)}) = \theta_0 + \theta_1 x^{(i)}
$$



Where:  
- $m$ = number of training examples  
- $y^{(i)}$ = true value of the $i$-th example  

💡 **Intuition:** While the loss function measures error for **one example**, the cost function measures error for the **whole dataset**. During training, we minimize the cost function to find the best $\theta_0$ and $\theta_1$.


<img src="../img/sse.gif" alt="linear regression" width="400">

---

**Key Differences**

| Feature            | Loss Function                                | Cost Function                                          |
| ------------------ | -------------------------------------------- | ------------------------------------------------------ |
| Measures error for | **Single training example**                  | **All training examples (average)**                    |
| Used for           | Understanding prediction error for one point | Optimizing the model parameters                        |
| Example in LR      | $(\hat{y}-y)^2$                              | $\frac{1}{2m} \sum_{i=1}^{m} \left( h_\theta(x^{(i)}) - y^{(i)} \right)^2$  |

---


## Best-Fitting Line in Linear Regression

Gradient Descent is an **algorithm to find the best-fitting line** in linear regression by minimizing the prediction error.

1. **Start with initial guesses** for the slope ($\theta_1$) and intercept ($\theta_0$).
2. **Predict the outputs** using the current line: $\hat{y} = \theta_0 + \theta_1 x$
3. **Calculate the error** for each data point: difference between predicted and actual value.
4. **Compute the gradient**: the direction in which the error increases.
5. **Update the parameters**: move the slope and intercept slightly in the **opposite direction of the gradient** to reduce error.
6. **Repeat** steps 2–5 until the error is as small as possible.

**Key Idea:** Gradient Descent is like **rolling down a hill** to reach the lowest point. The “hill” is the cost function (error), and the lowest point is where the line fits the data best.

- The **learning rate** ($\alpha$) controls how big each step is.
- The process gradually finds the **line that minimizes prediction errors**.


![gradiant decent](https://www.startertutorials.com/blog/wp-content/uploads/2021/09/Gradient_Descent_Animation.gif)






















































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


## Performance Metrics for Linear Regression

To evaluate the performance of a linear regression model, the following metrics are commonly used:

### 1. Mean Absolute Error (MAE)

Mean Absolute Error (MAE) measures the **average magnitude of errors** between predicted values and actual values, without considering their direction.

$$
\text{MAE} = \frac{1}{n} \sum_{i=1}^{n} \left| \hat{y}^{(i)} - y^{(i)} \right|
$$

where n represents the number of data points (samples) in the dataset.

**Explanation**

- Computes the absolute difference between each prediction and the true value  
- Averages these absolute errors over all data points  
- Treats all errors equally (no squaring)

**Interpretation**

- Lower MAE indicates better model performance  
- MAE is expressed in the **same units as the target variable**, making it easy to interpret

**Advantages**

- Simple and intuitive  
- Less sensitive to outliers compared to Mean Squared Error (MSE)

**Disadvantages**
- Does not penalize large errors as strongly as MSE  
- Not differentiable at zero (can affect some optimization methods)

### 2. Mean Squared Error (MSE)

Mean Squared Error (MSE) measures the **average of the squared differences** between predicted values and actual values.

$$
\text{MSE} = \frac{1}{n} \sum_{i=1}^{n} \left( \hat{y}^{(i)} - y^{(i)} \right)^2
$$

**Explanation**
- Calculates the difference between prediction and true value  
- Squares each error to make all values positive  
- Averages the squared errors over all data points

**Interpretation**
- Lower MSE indicates better model performance  
- Larger errors are penalized more heavily due to squaring

**Advantages**
- Differentiable and easy to optimize  
- Emphasizes large errors, which can be useful in many applications

**Disadvantages**
- Sensitive to outliers  
- Expressed in squared units of the target variable



### 3. Root Mean Squared Error (RMSE)

Root Mean Squared Error (RMSE) measures the **square root of the average squared differences** between predicted values and actual values.

$$
\text{RMSE} = \sqrt{\frac{1}{n} \sum_{i=1}^{n} \left( \hat{y}^{(i)} - y^{(i)} \right)^2}
$$

**Explanation**
- Computes the squared error for each prediction  
- Averages the squared errors (MSE)  
- Takes the square root to return to the original unit

**Interpretation**
- Lower RMSE indicates better model performance  
- RMSE is expressed in the **same units as the target variable**

**Advantages**

- Penalizes large errors more than MAE  
- Easier to interpret than MSE

**Disadvantages**

- Sensitive to outliers  
- Larger errors have a stronger influence due to squaring


### 4. R-squared (R²) Score

R-squared (R²) measures how well a regression model explains the **variance in the target variable**.

$$
R^2 = 1 - \frac{\sum_{i=1}^{n} \left( y^{(i)} - \hat{y}^{(i)} \right)^2}{\sum_{i=1}^{n} \left( y^{(i)} - \bar{y} \right)^2}
$$



**Explanation**
- Compares the model’s prediction errors to the errors of a simple baseline model  
- The baseline model always predicts the mean of the target values ($\bar{y}$)

**Interpretation**

- $R^2 = 1$: Perfect fit  
- $R^2 = 0$: Model performs no better than predicting the mean  
- $R^2 < 0$: Model performs worse than the mean prediction

**Advantages**

- Easy to interpret  
- Shows how much variance is explained by the model

**Limitations**
- Does not indicate whether predictions are accurate  
- Can be misleading for non-linear relationships  
- Increases when more features are added, even if they are irrelevant

---


## Comparison of Regression Performance Metrics

| Metric                             | What it Measures                                                | Error Sensitivity               | Units                   | Interpretation                   | Key Advantage                             | Key Limitation                                  |
| ---------------------------------- | --------------------------------------------------------------- | ------------------------------- | ----------------------- | -------------------------------- | ----------------------------------------- | ----------------------------------------------- |
| **MAE (Mean Absolute Error)**      | Average absolute difference between predicted and actual values | Low (treats all errors equally) | Same as target variable | Lower value = better performance | Simple, robust to outliers                | Large errors not strongly penalized             |
| **MSE (Mean Squared Error)**       | Average of squared prediction errors                            | High (large errors dominate)    | Squared units of target | Lower value = better performance | Easy to optimize, emphasizes large errors | Very sensitive to outliers, harder to interpret |
| **RMSE (Root Mean Squared Error)** | Square root of average squared errors                           | High (penalizes large errors)   | Same as target variable | Lower value = better performance | Interpretable, highlights large mistakes  | Sensitive to outliers                           |
| **R² (R-squared Score)**           | Proportion of variance explained by the model                   | Indirect (variance-based)       | Unitless                | Closer to 1 = better fit         | Shows overall explanatory power           | Does not measure prediction accuracy            |

**Quick Usage Guide**

* **Use MAE** → when robustness to outliers is important
* **Use MSE** → when large errors must be heavily penalized
* **Use RMSE** → when error size matters and interpretability is needed
* **Use R²** → when you want to understand how well the model explains the data

---
