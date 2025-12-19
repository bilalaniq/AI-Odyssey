# Machine learning

Machine learning is a subdomain of computer science that focuses on algorithms which help a computer learn from data without explicit programming

**Explicit** programming means writing hard-coded, rule-based instructions that tell the computer exactly what to do in every situation.


## Table of Contents
- [Machine learning](#machine-learning)
  - [Table of Contents](#table-of-contents)
  - [Features](#features)
  - [Types of Machine Learning](#types-of-machine-learning)
    - [Supervised learning](#supervised-learning)
    - [UnSupervised learning](#unsupervised-learning)



## Features 

Features are the individual measurable attributes or properties of data that are used as input to a machine learning model.

In simple words: Features are the information (variables) that help a model learn and make decisions.

Features can be 

- **Qualitative data**: Qualitative data refers to information that can be sorted into categories or groups.
For example: gender (girl or boy). 

 Qualitative data refers to non-numerical information that can be classified into categories or groups, such as gender (male/female). Numeric values like 0 and 1 may be used only as labels for processing.

  **Nominal data** (no inherent data): Nominal data is a type of categorical data where values represent names or labels without any inherent order or ranking. for example: countries 

  To feed nominal data to our computer we use ONE-HOT ENCODING

  One-Hot Encoding is a technique used in machine learning to convert categorical (nominal) data into numerical form so that it can be used by ML algorithms.

  it does not work like 

  `Red = 1, Blue = 2, Green = 3` ❌

  we use 

  ```bash
  Red   Blue  Green     ✅
  1     0     0
  0     1     0        
  0     0     1
  ```

 
  **ordinal data**(inherent order): Ordinal data is categorical data with an inherent order or ranking among categories, but without a measurable or equal difference between them.

  for example: `Satisfaction level: Low → Medium → High`


- **Quantitative Data**: Quantitative data refers to numerical data that represents measurable quantities.
It answers questions like “how much?”, “how many?”, or “how often?”. 






## Types of Machine Learning

1. Supervised learning - uses labeled inputs (meaning the input has a corresponding output label) to train models and learn outputs
2. Unsupervised learning - uses unlabeled data to learn about patterns in data
3. Reinforcement learning - agent learning in interactive environment based on rewards and penalties


### Supervised learning

**Supervised learning** is a type of machine learning where a model is trained using **labeled data**—that is, data where the **correct output is already known**.

In supervised learning:

* Each training example consists of **input features** and a **known output (label)**.
* The algorithm learns a **mapping** from inputs to outputs.
* After training, the model can **predict outputs for new, unseen data**.

**Example**

Suppose you want to predict whether an email is spam.

| Email Text        | Label    |
| ----------------- | -------- |
| “Win a prize”     | Spam     |
| “Meeting at 3 PM” | Not Spam |

The model learns patterns that distinguish spam from non-spam emails.


### UnSupervised learning

**Unsupervised learning** is a type of machine learning where the model is trained on **unlabeled data**, meaning **no correct output is provided**. 

In unsupervised learning:

* The data contains **only input features**
* The algorithm tries to **discover hidden patterns, structures, or relationships**
* There are **no predefined labels or answers**

**Example**

Suppose you have customer data with:

* Age
* Income
* Shopping behavior

But **no information** about customer types.

The algorithm automatically groups similar customers together.

















![supervised vs unsupervised](https://upload.wikimedia.org/wikipedia/commons/thumb/4/4d/Supervised_and_unsupervised_learning.png/500px-Supervised_and_unsupervised_learning.png)