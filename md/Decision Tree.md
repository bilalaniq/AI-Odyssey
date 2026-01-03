# Decision Tree

A **Decision Tree** is a **supervised machine learning algorithm** used for:

* **Classification** (e.g., spam vs not spam) Used for binary as well as multiclass classification
* **Regression** (predicting numbers like price or temperature)

It works like a **flowchart**:

* You ask a series of questions
* Each answer leads to another question
* You end at a final decision (output)

**Simple Example**


<img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ0-gEvoFoyD5FnrMlss-d-OrGHTbp52SB1uA&s" width="400">

---


## Table of Contents
- [Decision Tree](#decision-tree)
  - [Table of Contents](#table-of-contents)
  - [Structure of a Decision Tree](#structure-of-a-decision-tree)
  - [How a Decision Tree Works](#how-a-decision-tree-works)
  - [Splitting Criteria](#splitting-criteria)
    - [Entropy](#entropy)
    - [Information Gain](#information-gain)
    - [Gini Index (Used in CART)](#gini-index-used-in-cart)
    - [Classification Error](#classification-error)
  - [Stopping Conditions](#stopping-conditions)
  - [Advantages of Decision Trees](#advantages-of-decision-trees)
  - [Disadvantages of Decision Trees](#disadvantages-of-decision-trees)
  - [Real-Life Applications](#real-life-applications)

---

## Structure of a Decision Tree

A decision tree has **four main components**:

**1. Root Node**

* The **first question**
* Contains the **entire dataset**
* Chosen using a **splitting criterion** (like entropy or Gini)

**2. Decision Nodes (Internal Nodes)**

* Nodes where the data is split further
* Each node represents a **test on a feature**

**3. Branches**

* Outcomes of a decision
* Connect nodes

**4. Leaf Nodes (Terminal Nodes)**

* Final output
* No further splitting
* Contains the **predicted class or value**


<img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRPp0u3G_qGzePa46mYDSkcrNetCcapvL4QRA&s" width="400">



---


## How a Decision Tree Works

1. Start with the full dataset
2. Choose the **best feature** to split the data
3. Split the data into subsets
4. Repeat the process for each subset
5. Stop when:

   * All data belongs to one class
   * Maximum depth is reached
   * No improvement is possible

![decision tree working](https://s3-ap-southeast-1.amazonaws.com/he-public-data/Decision-Tree-Boundary5b6c641.gif)


---

## Splitting Criteria

The tree chooses splits using **mathematical measures**.

### Entropy

Entropy measures **impurity or randomness**.

**Formula:**

$$
Entropy = -\sum p \log_2(p)
$$

* Entropy = 0 → Pure node
* Higher entropy → More disorder

Example:

* All students pass → Entropy = 0
* Half pass, half fail → Entropy = 1

---

### Information Gain

Information Gain tells us **how much entropy is reduced** after a split.

**Formula:**

$$
IG = \text{Entropy(parent)} - \text{Weighted Entropy(children)}
$$

* Higher IG = better feature
* Used to select the root node

---

### Gini Index (Used in CART)

Measures probability of **misclassification**.

**Formula:**

$$
Gini = 1 - \sum p^2
$$

where p = probability of a class in the dataset

$$
p = \frac{\text{number of samples in a class}}{\text{total number of samples}}
$$

* Gini = 0 → Perfect split
* Lower Gini is better

---

### Classification Error

Measures fraction of **misclassified samples** if we assign the majority class to a node.

**Formula:**

$$
Error = 1 - \max(p_i)
$$


where 
$$
p_i = \text{probability of class } i \text{ in the node}
$$ 

* Error = 0 → Pure node  
* Lower Error → Better split


<img src="https://sebastianraschka.com/images/faq/decisiontree-error-vs-entropy/Slide2.png" width="600">


---

## Stopping Conditions

A tree stops growing when:

* All samples belong to the same class
* Node contains too few samples
* Maximum depth is reached
* No feature improves the split


## Advantages of Decision Trees

* Easy to understand and visualize
* No need for data normalization
* Handles categorical and numerical data
* Fast prediction

---

## Disadvantages of Decision Trees

* Can overfit easily
* Sensitive to small data changes
* Not very accurate alone for complex problems

---

## Real-Life Applications

* Medical diagnosis
* Loan approval systems
* Spam detection
* Recommendation systems
* Game AI decision making

---
