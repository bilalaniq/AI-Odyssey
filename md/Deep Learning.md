# Deep Learning

**Deep Learning (DL)** is a subfield of **Artificial Intelligence (AI)** that focuses on teaching computers to learn patterns from data using structures called **neural networks**, inspired by the human brain.

In simple terms:

> Deep Learning allows computers to learn from examples instead of being explicitly programmed.

Example:

* Instead of writing rules to recognize a cat 🐱,
* You show the computer **thousands of cat images**, and it **learns what makes a cat a cat**.

---

## Table of Contents
- [Deep Learning](#deep-learning)
  - [Table of Contents](#table-of-contents)
  - [**Artificial Neural Networks**](#artificial-neural-networks)
    - [How it all started (McCulloch \& Pitts – 1943)](#how-it-all-started-mcculloch--pitts--1943)
    - [**Linear Threshold Unit (LTU) / Artificial Neuron**](#linear-threshold-unit-ltu--artificial-neuron)
  - [**LTU as Logic Gates**](#ltu-as-logic-gates)
    - [**OR Gate using LTU**](#or-gate-using-ltu)
    - [**AND Gate using LTU**](#and-gate-using-ltu)
  - [**Why LTUs were important**](#why-ltus-were-important)
  - [**Birth of Learning: The Perceptron (1957)**](#birth-of-learning-the-perceptron-1957)
    - [**Output**](#output)
  - [**What does the Perceptron learning rule do?**](#what-does-the-perceptron-learning-rule-do)
  - [**Perceptron as a Linear Classifier**](#perceptron-as-a-linear-classifier)
  - [**Feed-Forward Network of Perceptrons**](#feed-forward-network-of-perceptrons)
  - [**Multi-Layer Perceptron (MLP)**](#multi-layer-perceptron-mlp)
  - [**Why Hidden Layers Matter**](#why-hidden-layers-matter)
  - [**Mathematical View of a Neural Network**](#mathematical-view-of-a-neural-network)
  - [**Activation Functions**](#activation-functions)
  - [**Training a Neural Network**](#training-a-neural-network)
  - [**Loss**](#loss)
  - [**Gradient Descent**](#gradient-descent)
  - [**Backpropagation**](#backpropagation)



---

## **Artificial Neural Networks**

### How it all started (McCulloch & Pitts – 1943)

In 1943, **McCulloch and Pitts** proposed a mathematical model inspired by **biological neurons**.
They showed that simple computational units could perform **logical operations** like AND and OR.

These units were called **Linear Threshold Units (LTUs)**.

This idea laid the **foundation of artificial neural networks**.

---


### **Linear Threshold Unit (LTU) / Artificial Neuron**

**Basic components of an LTU**

An LTU consists of:

* **Inputs**: (x1, x2)
* **Weights**: (w1, w2)
* **Bias**: (b)
* **Weighted sum**
* **Activation function**

**Mathematical model**

$$
z = \sum_i w_i x_i + b
$$

The output is:
$$
y =
\begin{cases}
1 & \text{if } z \ge \text{threshold} \
0 & \text{otherwise}
\end{cases}
$$

This activation function is a **step function**.

<img src="../img/ltu.png" width="500">


---

## **LTU as Logic Gates**

### **OR Gate using LTU**

Choose:

* (w_1 = 1), (w_2 = 1)
* (b = -0.5)

Then:
$$
z = x_1 + x_2 - 0.5
$$

This produces output **1 whenever at least one input is 1**, exactly like an OR gate.

<img src="../img/or_ltu.png" width="500">



---

### **AND Gate using LTU**

Choose:

* (w_1 = 1), (w_2 = 1)
* (b = -1.5)

Then:
$$
z = x_1 + x_2 - 1.5
$$

This produces output **1 only when both inputs are 1**, exactly like an AND gate.

<img src="../img/and_ltu.png" width="500">



---

## **Why LTUs were important**

* They behaved like **biological neurons**
* A network of LTUs could compute **Boolean functions**
* They were the **first artificial neurons**

**Major limitation**

* **Weights were manually chosen**
* **No learning mechanism**

---

## **Birth of Learning: The Perceptron (1957)**

In 1957, **Frank Rosenblatt** introduced the **Perceptron**.

**Key improvement**

* Introduced a **learning rule**
* Weights could be **automatically adjusted**

So now, the model could **learn from data**.


**Perceptron Model**

A perceptron is an **LTU with learning**.

### **Output**

$$
o = \text{step}\left(\sum_i w_i x_i + b\right)
$$

**Learning Rule**

$$
w_i \leftarrow w_i + \eta (t - o) x_i
$$

Where:

* $t$ = target (correct output)
* $o$ = computed output
* $\eta$ = learning rate


---

## **What does the Perceptron learning rule do?**

* If prediction is **wrong**, weights are updated
* If prediction is **correct**, little or no change happens
* The update is proportional to:

    * the **error** $(t - o)$
    * the **input value** $x_i$


👉 This is **training**

---

## **Perceptron as a Linear Classifier**

A perceptron separates data using a **straight line (or hyperplane)**.

That is why it is called a **linear binary classifier**.

Linear separable data is the Data that can be separated by **one straight line**.

**Limitations of the Perceptron**

* Can only learn **linearly separable data**
* Cannot solve problems like **XOR**
* Has **only one layer of weights**

This limitation caused a temporary **decline in neural network research**.

---

## **Feed-Forward Network of Perceptrons**

To overcome these limits, researchers connected **multiple perceptrons together**.

**Feed-forward**

* Information flows **only forward**
* No loops or feedback

This led to **Multi-Layer Perceptrons (MLPs)**.

---

## **Multi-Layer Perceptron (MLP)**

An MLP is a neural network with:

* **Input layer**
* **One or more hidden layers**
* **Output layer**

Each layer contains perceptrons (units).

![](https://ds055uzetaobb.cloudfront.net/brioche/uploads/hDeFaUxHWk-ann_flow.png?width=1200)


**Fully Connected Network**

A Fully Connected Network (also called a dense network) is a type of Multi-Layer Perceptron (MLP).

* Every unit in one layer connects to **all units in the next layer**
* No connections within the same layer


<img src="https://media.geeksforgeeks.org/wp-content/uploads/20250529112722673975/file.webp" width="500">



---

## **Why Hidden Layers Matter**

Hidden layers allow:

* Learning **non-linear relationships**
* Solving complex problems like XOR
* Approximating any function (with enough neurons)

This made neural networks **powerful**.

**Why is it Called “Deep”?**

The word **“deep”** refers to the **number of layers** in a neural network.

* Shallow model → 1–2 layers
* Deep model → many layers (sometimes hundreds)

More layers = ability to learn **more complex patterns**

---



## **Mathematical View of a Neural Network**

Let:

* ($a_i$) = output of unit (i)
* ($w_{i,j}$) = weight from unit (i) to unit (j)

**Output of unit (j)**

$$
a_j = g_j\left(\sum_i w_{i,j} a_i\right)
$$


Where:

* ($g_j$) is a **non-linear activation function**

---

## **Activation Functions**

An **activation function** is a mathematical function applied to the output of a neuron (after calculating the weighted sum of inputs). Its main purpose is to **introduce non-linearity** into the network so that it can learn complex patterns.

1. Non-linearity allows neural networks to learn **complex patterns** beyond straight lines.
2. Without it, multiple layers collapse into a single linear function, no matter how deep.
3. Real-world data (images, speech, text) is mostly **non-linear**, so linear models fail.
4. Non-linear activation functions (ReLU, Sigmoid, Tanh) enable networks to **model curves and interactions**.
5. It makes neural networks **powerful enough to solve problems like XOR and image recognition**.


**Common Activation Functions** :

1. **Step Function** – outputs 0 or 1 based on a threshold.
2. **Sigmoid Function** – outputs values between 0 and 1; useful for probabilities.
3. **Tanh Function** – outputs values between -1 and 1; zero-centered.
4. **ReLU (Rectified Linear Unit)** – outputs 0 for negative inputs and the input itself if positive; widely used in hidden layers.
5. **Leaky ReLU** – like ReLU but allows a small negative value for negative inputs.
6. **Softmax Function** – converts outputs into probabilities that sum to 1, used for multi-class classification.


<img src="https://i-blog.csdnimg.cn/direct/f864873f39fa4169a4f1f9a944147e67.png" width="800">


**Purpose:** Without an activation function, the neural network would behave like a linear model, no matter how many layers it has.


**Why not step function?**

* Not differentiable
* Cannot be used with gradient descent

**Why not linear function?**

* Multiple layers collapse into one
* Cannot learn non-linear patterns
  
---


## **Training a Neural Network**

**Goal**

Find weights ($w_i$) that **minimize loss (L)**.

**Steps**

1. Initialize weights
2. Forward pass → compute output
3. Compute loss
4. Compute gradients
5. Update weights

---


## **Loss**

Loss in a neural network is a numerical measure of how incorrect the model’s prediction is compared to the actual target value. It is calculated after the network produces an output during the forward pass. The main goal of training a neural network is to minimize this loss.

Different loss functions are used for different types of problems. For regression tasks, Mean Squared Error measures the average squared difference between predicted and true values. For binary classification, Binary Cross-Entropy measures how well the predicted probabilities match the correct labels. For multi-class classification, Categorical Cross-Entropy evaluates how close the predicted class probabilities are to the true class.

The computed loss is then used in backpropagation to calculate gradients, and gradient descent updates the weights and biases to reduce the loss over time.

Cross-entropy is a common loss function for multi-class classifications. But we can skip the details and just focus on a generic loss function `L`


---


## **Gradient Descent**


Gradient Descent is an **optimization algorithm** used to train neural networks by **minimizing the loss function**. Its goal is to find the best values of weights and biases that reduce the error between the predicted output and the target output.

During training, the network first performs a **forward pass** to compute the output and the loss. Then, using **backpropagation**, it calculates the **gradient of the loss** with respect to each weight and bias. These gradients show the **direction of steepest increase** of the loss.

To reduce the loss, the parameters are updated in the **opposite direction of the gradient**:

$$
w \leftarrow w - \eta \frac{\partial L}{\partial w}, \quad
b \leftarrow b - \eta \frac{\partial L}{\partial b}
$$

Here, $\eta$ is the **learning rate**, which controls how big each update step is. Repeating this process over many iterations gradually moves the network toward a **minimum loss**, resulting in better predictions.

In short, **gradient descent is how neural networks learn** by continuously adjusting their parameters to improve performance.

---



## **Backpropagation**

**Backpropagation** (short for **backward propagation of errors**) is an algorithm used to **train neural networks**. Its main goal is to **compute the gradient of the loss function with respect to each weight and bias** in the network.

* It allows the network to **know how to adjust weights and biases** to reduce the error.
* Works **layer by layer from output back to input** using the **chain rule**.

---

**Forward Pass**

For each neuron (j):

1. Compute the weighted sum:
$$
z_j = \sum_i w_{i,j} a_i + b_j
$$
2. Apply the activation function:
$$
a_j = g_j(z_j)
$$

* ($a_i$) = input from previous layer
* ($w_{i,j}$) = weight from neuron (i) to (j)
* ($b_j$) = bias of neuron (j)
* ($g_j$) = activation function of neuron (j)

Compute the **loss** (L) based on predicted outputs and targets.

---

**Compute Gradients at Output Layer**

For a neuron (k) in the output layer:

1. Compute the **error term**:
$$
\delta_k = \frac{\partial L}{\partial a_k} \cdot g'_k(z_k)
$$
2. Gradient of loss w.r.t weight (w_{j,k}):
$$
\frac{\partial L}{\partial w_{j,k}} = \delta_k \cdot a_j
$$
3. Gradient of loss w.r.t bias (b_k):
$$
\frac{\partial L}{\partial b_k} = \delta_k
$$

---

**Compute Gradients for Hidden Layers**

For a hidden neuron (j):

1. Compute error term using **backpropagated errors** from next layer:
$$
\delta_j = g'*j(z_j) \sum*{k} w_{j,k} \delta_k
$$

* Sum is over all neurons (k) in the next layer connected to (j).

2. Gradient of loss w.r.t weight (w_{i,j}):
$$
\frac{\partial L}{\partial w_{i,j}} = \delta_j \cdot a_i
$$

3. Gradient w.r.t bias (b_j):
$$
\frac{\partial L}{\partial b_j} = \delta_j
$$

---

**Update Weights and Biases**

After gradients are calculated, update parameters using **gradient descent**:

$$
w_{i,j} \leftarrow w_{i,j} - \eta \frac{\partial L}{\partial w_{i,j}}
$$

$$
b_j \leftarrow b_j - \eta \frac{\partial L}{\partial b_j}
$$

* ($\eta$) = learning rate
* Repeat for all layers and all training examples.



---





























<!-- 
## **18. Why Backpropagation is Needed**

* Output weights are easy to update
* Hidden layer weights are **indirectly related to loss**

👉 Use **Chain Rule**

---

## **19. Chain Rule (Core Idea)**

If:
[
z = f(y), \quad y = g(x)
]

Then:
[
\frac{dz}{dx} = \frac{dz}{dy} \cdot \frac{dy}{dx}
]

Backpropagation applies this **layer by layer**, from output to input.

---

## **20. Backpropagation**

### **What it does**

* Computes gradients efficiently
* Propagates error backward
* Updates all weights

### **Why the name**

> Backward propagation of error

---

## **21. Weight Update using Backpropagation**

For any weight:
[
w \leftarrow w - \eta \frac{\partial L}{\partial w}
]

Biases are updated **the same way**.

---

## **22. Final Big Picture**

* LTUs → Artificial neurons
* Perceptron → Learning introduced
* MLP → Non-linear learning
* Activation functions → Expressiveness
* Backpropagation → Efficient training
* Gradient descent → Optimization
* Deep learning → Many layers, powerful models

--- -->
