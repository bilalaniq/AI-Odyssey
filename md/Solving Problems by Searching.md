# Solving problems by searching

When an agent needs to achieve a goal it doesn’t know how to reach directly, it **looks ahead** by *searching* through a space of possible states and actions to find a sequence (a plan) that reaches the goal. This is the central idea of classical AI problem solving.

When the correct action to take is not immediately obvious, an agent may need to plan ahead
- To consider a sequence of actions that form a path to a goal state
- Such an agent is called a **problem-solving agent**
- The computational process it undertakes is called **search**

![meme](https://content.imageresizer.com/images/memes/Scooby-Doo-Search-meme-2.jpg)



---

## **Table of Contents**

- [Solving problems by searching](#solving-problems-by-searching)
  - [**Table of Contents**](#table-of-contents)
  - [**Steps in Problem Solving by Searching**](#steps-in-problem-solving-by-searching)
    - [**1. Goal Formulation — Define What You Want to Achieve**](#1-goal-formulation--define-what-you-want-to-achieve)
    - [**2. Problem Formulation — Define How to Reach the Goal**](#2-problem-formulation--define-how-to-reach-the-goal)
    - [**3. Search — Explore Possible Action Sequences**](#3-search--explore-possible-action-sequences)
    - [**4. Execution — Carry Out the Plan**](#4-execution--carry-out-the-plan)
- [**Search Tree**](#search-tree)
  - [**Node Generation and Expansion**](#node-generation-and-expansion)
    - [**Terminology**](#terminology)
  - [**Search Data Structures**](#search-data-structures)
  - [**Frontier Management**](#frontier-management)
  - [**Types of Frontier Queues**](#types-of-frontier-queues)
  - [**Evaluating Search Strategies**](#evaluating-search-strategies)
    - [**Measured In Terms Of:**](#measured-in-terms-of)
- [**Search algorithms**](#search-algorithms)
  - [**Uninformed (Blind) Search**](#uninformed-blind-search)
  - [**Characteristics**](#characteristics)
  - [**Components Used in Uninformed Search**](#components-used-in-uninformed-search)
  - [**Types**](#types)
    - [**1. Breadth-First Search (BFS)**](#1-breadth-first-search-bfs)
    - [**2. Depth-First Search (DFS)**](#2-depth-first-search-dfs)
    - [**3. Depth-Limited Search (DLS)**](#3-depth-limited-search-dls)
      - [**Description:**](#description)
      - [**Properties:**](#properties)
      - [**Advantages:**](#advantages)
      - [**Disadvantages:**](#disadvantages)
    - [**4. Iterative Deepening Search (IDS)**](#4-iterative-deepening-search-ids)
      - [**Description:**](#description-1)
      - [**Properties:**](#properties-1)
      - [**Advantages:**](#advantages-1)
      - [**Disadvantages:**](#disadvantages-1)
    - [**5. Uniform Cost Search (UCS)**](#5-uniform-cost-search-ucs)
      - [**Description:**](#description-2)
      - [**Properties:**](#properties-2)
      - [**Advantages:**](#advantages-2)
      - [**Disadvantages:**](#disadvantages-2)
  - [**5. Comparison Table**](#5-comparison-table)

---





## **Steps in Problem Solving by Searching**

This process involves **four key steps**:

### **1. Goal Formulation — Define What You Want to Achieve**

This is where the agent determines **what the desired outcome is**.

* The **goal** defines the target or condition the agent wants to reach.
* It guides the agent’s decisions and filters which actions or states are relevant.

**Example:**
A navigation robot’s goal might be: *“Reach the destination point (x, y).”*
A chess-playing agent’s goal might be: *“Achieve a checkmate.”*

**Purpose:**
Without a clear goal, the agent has no direction — it cannot decide which states are “good” or “bad.”

---

### **2. Problem Formulation — Define How to Reach the Goal**

Once the goal is known, the agent must define the **problem space** or an  — i.e., the structure of the world it will search through.

This includes:

* **Initial state:** Where the agent starts.
* **Goal states:** states which satisfy the goal
* **State space**: the set of all states reachable from Initial state via actions.
* **Actions:** The possible moves the agent can take.
* **Transition model:** What state results from each action.
* **Goal test:** A way to check if the agent has reached the goal.
* **Path cost (Action cost function:):** A function that assigns a cost to each sequence of actions (used to find the *best* path).

**Example:**
In a route-finding problem:

* Initial state = Current location
* Actions = Move north, south, east, west
* Transition model = New location after each move
* Goal test = Is location = destination?
* Path cost = Distance or time

**Purpose:**
This step translates a real-world problem into a **searchable model** the agent can reason about.

---

### **3. Search — Explore Possible Action Sequences**

Now the agent uses a **search algorithm** to find a sequence of actions that leads from the **initial state** to a **goal state**.

* The search process can be visualized as exploring a **search tree**, where:

  * Nodes = possible states
  * Edges = actions that move between states
* The agent “looks ahead” by simulating the results of actions *before actually performing them.*

**Common search strategies:**

* **Uninformed (blind) search:**
  No knowledge of the goal location (e.g., Breadth-First Search, Depth-First Search).
* **Informed (heuristic) search:**
  Uses domain knowledge to guide the search (e.g., A*, Greedy Best-First Search).

**Purpose:**
This is where the agent **plans** — trying out hypothetical action sequences until it finds one that achieves the goal efficiently.

---

### **4. Execution — Carry Out the Plan**

Once the agent finds a valid solution (a sequence of actions), it **executes** those actions in the real world.

* The agent follows the chosen path **step-by-step**.
* It may re-check the environment between steps to ensure conditions haven’t changed.
* If the environment is dynamic, the agent may need to **replan**.

**Example:**
After computing the shortest path on a map, a delivery robot executes each move command until it reaches the destination.

**Purpose:**
This step turns the **planned solution** into **real-world behavior** that achieves the goal.

---


<br>
<br>


# **Search Tree**

* The **state space** represents all possible configurations (states) in the problem domain, along with the **actions** that transition one state to another.
* A **search tree** is built on top of this state space — it visualizes the **paths between states** as the agent searches for a route to the goal.
* Each **node** in the tree represents a state, and **edges** represent actions that move the agent from one state to another.
* The **root node** represents the initial state, and the **goal node** represents the state that satisfies the goal condition.

> The search tree “superimposes” a structure over the abstract state space to help visualize and manage the search process.


<br>
<img src="https://raw.githubusercontent.com/Codecademy/docs/main/media/binary-tree-labeled.png" alt="AGENTFLOW" width="700">
<br>

---

## **Node Generation and Expansion**

* At each node (representing a state), the agent may have **multiple choices of actions**.
* For each possible action, a **new (successor) node** is generated.
* When all successor nodes of a node have been generated, that node is said to be **expanded**.
* All nodes that are **generated or expanded** are said to have been **reached**.

### **Terminology**

| **Term**     | **Meaning**                                                                  |
| ------------ | ---------------------------------------------------------------------------- |
| **Interior** | Nodes that have been expanded (i.e., explored completely).                   |
| **Frontier** | Nodes that have been generated but not yet expanded.                         |
| **Exterior** | Nodes that have not been generated yet (unreached part of the search space). |

> In short:
> **Generated → Frontier → Expanded (Interior).**


<br>

![alt text](../img/Node%20Generation%20and%20Expansion.png)

<br>

here the `S0` is **Interior** and both the `S1` & `S2` are **Frontier** and rest are **Exterior** which are not generated yet.
  
---

## **Search Data Structures**

A search algorithm needs a **data structure** to keep track of the search tree as it’s being constructed.
For each node `n`, we maintain the following components:

| **Component** | **Description**                                         |
| ------------- | ------------------------------------------------------- |
| `n.STATE`     | The state the node represents.                          |
| `n.PARENT`    | The parent node that generated this node.               |
| `n.ACTION`    | The action applied to the parent to generate this node. |
| `n.PATH-COST` | The total cost from the initial state to this node.     |

This information allows the algorithm to **reconstruct the full path** from the start state to any node, including the goal.

---

## **Frontier Management**

The **frontier** (also known as the **open list**) contains all nodes that have been generated but **not yet expanded**.

Operations needed for managing the frontier:

* `IS-EMPTY(frontier)` → True if the frontier has no nodes.
* `POP(frontier)` → Removes and returns the next node to expand.
* `TOP(frontier)` → Returns (but does not remove) the next node.
* `ADD(node, frontier)` → Inserts a node into the queue.

The **type of queue** used for the frontier determines the **search strategy**.

---

## **Types of Frontier Queues**

| **Type of Queue**              | **Description**                                                                     | **Used In**                    |
| ------------------------------ | ----------------------------------------------------------------------------------- | ------------------------------ |
| **FIFO (First-In, First-Out)** | Expands the oldest generated node first.                                            | **Breadth-First Search (BFS)** |
| **LIFO (Last-In, First-Out)**  | Expands the most recently generated node first.                                     | **Depth-First Search (DFS)**   |
| **Priority Queue**             | Expands the node with the smallest cost according to an evaluation function `f(n)`. | **Best-First Search**, **A***  |

> The **choice of queue** directly affects **time, space, and optimality** of the search.

---

## **Evaluating Search Strategies**

When comparing different search algorithms, we evaluate them along **four major dimensions**:

| **Criterion**         | **Question**                                             | **Explanation**                                |
| --------------------- | -------------------------------------------------------- | ---------------------------------------------- |
| **Completeness**      | Will the algorithm always find a solution if one exists? | BFS is complete; DFS may not be.               |
| **Time Complexity**   | How long will it take to find a solution?                | Usually measured by number of states expanded. |
| **Space Complexity**  | How much memory does it require?                         | Depends on how many nodes are stored at once.  |
| **Optimality (Cost)** | Does it find the least-cost path?                        | A* and Uniform Cost Search are optimal.        |

### **Measured In Terms Of:**

* **b** – branching factor of the search tree (average number of successors per node)
* **d** – depth (number of actions) of the least-cost solution
* **m** – maximum depth of the state space (maximum number of actions in any path)

---

<br>
<br>

# **Search algorithms**


Search algorithms are strategies used by **intelligent agents** to explore possible **states** or **paths** in a problem space to reach a **goal state**.
They form the core of **problem-solving in Artificial Intelligence (AI)** — where the agent looks ahead, simulates actions, and evaluates possible outcomes.


<br>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20250722170443251667/Search-Algorithms.webp" alt="AGENTFLOW" width="700">
<br>


Search algorithms are divided into two main categories:

- Uninformed (Blind) Search
- Informed (Heuristic) Search


## **Uninformed (Blind) Search**

**Uninformed search**, also called **blind search**, refers to search strategies that have **no additional information** about the goal location or distance — **other than what is provided in the problem definition**.

The agent does not know **which direction is better**; it explores the search space **systematically** or **brute-force**, until it finds a solution.

In other words:

> The algorithm does not use any domain-specific knowledge (like heuristics). It only uses the information available in the problem itself — the states, actions, and goal test.

---

## **Characteristics**

* Does **not use a heuristic function**.
* Explores **all possibilities** in a uniform or systematic way.
* Works purely based on:

  * The **initial state**
  * The **goal state**
  * The **successor function** (actions available from each state)
* Typically used when **no prior knowledge** of the environment is available.
* Can be **inefficient** for large search spaces.

---

## **Components Used in Uninformed Search**

1. **Initial State:** Where the search begins.
2. **Goal Test:** A function that checks if a given state is the goal.
3. **Successor Function:** Generates all possible next states from the current one.
4. **Path Cost (optional):** Used to measure the total cost from start to goal.

---

## **Types**

Uninformed search has **five major types**, depending on how they explore the search space:


### **1. Breadth-First Search (BFS)**

* Explores all nodes at one **depth level** before moving to the next.
* Uses a **queue (FIFO)** data structure.

**Properties:**

* **Completeness:** Yes (it will find the goal if one exists)
* **Optimality:** Yes, if all step costs are equal
* **Time Complexity:** O(b^d)
* **Space Complexity:** O(b^d)

> `O(b^d)` means the number of nodes generated or visited grows exponentially with both the branching factor and the depth of the goal.

**Advantages:**

* Always finds the **shortest path** (minimum number of steps).
* Simple and systematic.

**Disadvantages:**

* **Memory-intensive**, since it stores all nodes at the current level.

**Steps**

* At each node, select the successor node `n` with the minimum value of some evaluation function `f(n)`
* If `n` is a goal state, return, else apply `EXPAND` to generate child nodes
* Add each child node to the frontier
* Assumes all actions have the same cost
* Idea: The root node is explored first, then all the successors of the root node are expanded next, then their successors, and so on


<br>
<img src="https://static-assets.codecademy.com/Courses/CS102-Data-Structures-And-Algorithms/Breadth-First-Search-And-Depth-First-Search/Breadth-First-Tree-Traversal.gif" alt="AGENTFLOW" width="700">
<br>


so the result will be:

`A → B → C → D → E → F → G`


---

### **2. Depth-First Search (DFS)**

* Explores as **deeply as possible** before backtracking.
* Uses a **stack (LIFO)** or recursion.

**Properties:**

* **Completeness:** No (may get stuck in infinite paths)
* **Optimality:** No
* **Time Complexity:** O(b^m)
* **Space Complexity:** O(bm)

**Advantages:**

* **Memory efficient**.
* Finds a solution without exploring the entire tree.

**Disadvantages:**

* May go infinitely deep.
* May find a **non-optimal** solution.





<br>
<img src="https://static-assets.codecademy.com/Courses/CS102-Data-Structures-And-Algorithms/Breadth-First-Search-And-Depth-First-Search/Depth-First-Tree-Traversal.gif" alt="AGENTFLOW" width="700">
<br>




---

### **3. Depth-Limited Search (DLS)**

#### **Description:**

* A modified DFS that stops when a **predefined depth limit (l)** is reached.
* Prevents infinite loops.

#### **Properties:**

* **Completeness:** Yes (if goal depth ≤ limit)
* **Optimality:** No
* **Time Complexity:** O(b^l)
* **Space Complexity:** O(bl)

#### **Advantages:**

* Prevents infinite paths.
* Less memory usage.

#### **Disadvantages:**

* Must **know an appropriate limit** beforehand.
* May **miss the goal** if limit is too small.

---

### **4. Iterative Deepening Search (IDS)**

#### **Description:**

* Combines the benefits of **BFS** and **DFS**.
* Repeatedly performs **Depth-Limited Search** with increasing depth limits.

#### **Properties:**

* **Completeness:** Yes
* **Optimality:** Yes (for uniform cost)
* **Time Complexity:** O(b^d)
* **Space Complexity:** O(bd)

#### **Advantages:**

* Uses less memory (like DFS).
* Guarantees finding the **shortest path** (like BFS).

#### **Disadvantages:**

* Repeats some nodes multiple times.

---

### **5. Uniform Cost Search (UCS)**

#### **Description:**

* Expands the node with the **lowest path cost (g(n))**, not by depth.
* Works even when step costs differ.

#### **Properties:**

* **Completeness:** Yes (if cost > 0)
* **Optimality:** Yes
* **Time Complexity:** O(b^(C*/ε))
* **Space Complexity:** O(b^(C*/ε))

#### **Advantages:**

* Finds **least-cost paths**.
* Works with **non-uniform costs**.

#### **Disadvantages:**

* Can be slow when costs are similar or large.

---

## **5. Comparison Table**

| **Algorithm**              | **Uses Heuristic?** | **Complete?** | **Optimal?**    | **Time Complexity** | **Space Complexity** | **Data Structure** |
| -------------------------- | ------------------- | ------------- | --------------- | ------------------- | -------------------- | ------------------ |
| Breadth-First Search       | No                  | Yes           | Yes (unit cost) | O(b^d)              | O(b^d)               | Queue (FIFO)       |
| Depth-First Search         | No                  | No            | No              | O(b^m)              | O(bm)                | Stack (LIFO)       |
| Depth-Limited Search       | No                  | Partial       | No              | O(b^l)              | O(bl)                | Stack (LIFO)       |
| Iterative Deepening Search | No                  | Yes           | Yes (unit cost) | O(b^d)              | O(bd)                | Stack (LIFO)       |
| Uniform Cost Search        | No                  | Yes           | Yes             | O(b^(C*/ε))         | O(b^(C*/ε))          | Priority Queue     |

---