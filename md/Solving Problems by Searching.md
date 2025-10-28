# Solving problems by searching

When an agent needs to achieve a goal it doesn’t know how to reach directly, it **looks ahead** by *searching* through a space of possible states and actions to find a sequence (a plan) that reaches the goal. This is the central idea of classical AI problem solving.

When the correct action to take is not immediately obvious, an agent may need to plan ahead
- To consider a sequence of actions that form a path to a goal state
- Such an agent is called a **problem-solving agent**
- The computational process it undertakes is called **search**

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
  - [**Types of Frontier Data Structures**](#types-of-frontier-data-structures)
  - [**Evaluating Search Strategies**](#evaluating-search-strategies)
    - [**Measured In Terms Of:**](#measured-in-terms-of)
- [**Search algorithms**](#search-algorithms)
  - [**Uninformed (Blind) Search**](#uninformed-blind-search)
  - [**Types**](#types)
    - [**1. Breadth-First Search (BFS)**](#1-breadth-first-search-bfs)
    - [**2. Depth-First Search (DFS)**](#2-depth-first-search-dfs)
    - [**3. Depth-Limited Search (DLS)**](#3-depth-limited-search-dls)
    - [**4. Iterative Deepening Search (IDS)**](#4-iterative-deepening-search-ids)
    - [**5. Bidirectional Search with Iterative Deepening**](#5-bidirectional-search-with-iterative-deepening)
    - [**6. Uniform Cost Search (UCS) Dijkstra’s algorithm**](#6-uniform-cost-search-ucs-dijkstras-algorithm)
    - [**Comparison of uninformed search algorithms**](#comparison-of-uninformed-search-algorithms)
  - [**Informed (heuristic) search:**](#informed-heuristic-search)
  - [**Heuristic Function (h(n))**](#heuristic-function-hn)
  - [**Types**](#types-1)
    - [1. **Best-First Search**](#1-best-first-search)
    - [2. **Greedy Best-First Search**](#2-greedy-best-first-search)
    - [3. A\* Search (A-Star Search)](#3-a-search-a-star-search)

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
<img src="https://raw.githubusercontent.com/Codecademy/docs/main/media/binary-tree-labeled.png" alt="alt" width="700">
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

The **frontier** (also known as the **open list**) contains all nodes that have been **generated but not yet expanded**.
It represents the **boundary** between explored and unexplored parts of the search tree.

Operations used for managing the frontier:

* `IS-EMPTY(frontier)` → True if the frontier has no nodes.
* `POP(frontier)` → Removes and returns the next node to expand.
* `TOP(frontier)` → Returns (but does not remove) the next node.
* `ADD(node, frontier)` → Inserts a node into the frontier according to the search strategy.

The **behavior of the frontier** (i.e., which node is expanded next) depends on the **type of data structure** used.

---

## **Types of Frontier Data Structures**

| **Data Structure**                   | **Node Selection Rule**                                                           | **Used In**                    |
| ------------------------------------ | --------------------------------------------------------------------------------- | ------------------------------ |
| **FIFO Queue** (First-In, First-Out) | Expands the **oldest generated** node first.                                      | **Breadth-First Search (BFS)** |
| **LIFO Stack** (Last-In, First-Out)  | Expands the **most recently generated** node first.                               | **Depth-First Search (DFS)**   |
| **Priority Queue**                   | Expands the node with the **lowest cost** or **best evaluation function `f(n)`**. | **Best-First Search**, **A***  |

> The **data structure chosen for the frontier** directly determines the **search order**, **time and space complexity**, and **optimality** of the algorithm.


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
<img src="../img/Search_alg.png" alt="alt" width="700">
<br>
<br>
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

**Characteristics**

* Does **not use a heuristic function**.
* Explores **all possibilities** in a uniform or systematic way.
* Works purely based on:

  * The **initial state**
  * The **goal state**
  * The **successor function** (actions available from each state)
* Typically used when **no prior knowledge** of the environment is available.
* Can be **inefficient** for large search spaces.

---

**Components Used in Uninformed Search**

1. **Initial State:** Where the search begins.
2. **Goal Test:** A function that checks if a given state is the goal.
3. **Successor Function:** Generates all possible next states from the current one.
4. **Path Cost (optional):** Used to measure the total cost from start to goal.

---

## **Types**

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

* At each level, expand all nodes before moving to the next depth.
* If a node is a goal state, return the path and stop.
* Add each child node to the **queue** (FIFO order).
* Assumes all actions have the same cost.

* Idea: The root node is explored first, then all the successors of the root node are expanded next, then their successors, and so on.

<br>
<img src="https://static-assets.codecademy.com/Courses/CS102-Data-Structures-And-Algorithms/Breadth-First-Search-And-Depth-First-Search/Breadth-First-Tree-Traversal.gif" alt="alt" width="700">
<br>

So the result will be:

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
<img src="https://static-assets.codecademy.com/Courses/CS102-Data-Structures-And-Algorithms/Breadth-First-Search-And-Depth-First-Search/Depth-First-Tree-Traversal.gif" alt="alt" width="700">
<br>

so the result will be:

`A → B → D → E → C → F → G`


---

### **3. Depth-Limited Search (DLS)**

* A modified DFS that stops when a **predefined depth limit (l)** is reached.
* Prevents infinite loops.

**Properties:**

* **Completeness:** Yes (if goal depth ≤ limit) otherwize No
* **Optimality:** No
* **Time Complexity:** O(b^l)
* **Space Complexity:** O(bl)

**Advantages:**

* Prevents infinite paths.
* Less memory usage.

**Disadvantages:**

* Must **know an appropriate limit** beforehand.
* May **miss the goal** if limit is too small.



<br>
<img src="https://miro.medium.com/v2/resize:fit:1400/1*vf9qkp9izJa5m39IThkhrA.gif" alt="alt" width="900">
<br>

> where d is the `limit` here

---

### **4. Iterative Deepening Search (IDS)**

* Combines the benefits of **BFS** and **DFS**.
* Repeatedly performs **Depth-Limited Search** with increasing depth limits.

**Properties:**

* **Completeness:** Yes for finite b
* **Optimality:** Yes (for uniform cost)
* **Time Complexity:** O(b^d)
* **Space Complexity:** O(bd)

**Advantages:**

* Uses less memory (like DFS).
* Guarantees finding the **shortest path** (like BFS).

**Disadvantages:**

* Repeats some nodes multiple times.



<br>
<img src="https://miro.medium.com/v2/resize:fit:1400/1*dA20GbXBrT6-BUPMLqJFKA.gif" alt="alt" width="900">
<br>


> IDS uses memory similar to DFS, not BFS.
> 
> Even though it restarts the search multiple times, each individual depth-limited search is depth-first, so it only keeps the current path and a few siblings in memory.


---

### **5. Bidirectional Search with Iterative Deepening**

Searches **forward from the start** and **backward from the goal**, meeting in the middle — and applies **iterative deepening** on both directions to limit memory use.

It expands nodes **layer by layer** in both directions.

---

**Properties:**

* **Completeness:** Yes (if branching factor is finite)   
* **Optimality:** Yes (if both searches use BFS/IDDFS with uniform step cost)
* **Time Complexity:** O(b^(d/2)) — MUCH better than O(b^d)        
* **Space Complexity:** O(b^(d/2)) — improved but more than IDDFS  

> *d = depth of the solution*

**Advantages**

* Major reduction in search time (meeting in the middle).
* Uses less memory than standard bidirectional BFS (due to iterative deepening).
* Good for large search spaces.

**Disadvantages**

* Hard to implement for problems where **goal state is not explicitly defined**.
* Requires **reverse successor function** (not always available).
* Synchronizing both searches can be tricky.




<br>
<img src="https://how.dev/api/edpresso/shot/6199751998963712/image/5139040078135296" alt="alt" width="700">
<br>


both `1` and `16` will intersect at node `9`

> note that there are many version of `Bidirectional Search` based on `BFS` & `DFS` but here we are only taking about `Bidirectional Search` based on `IDS`


---

### **6. Uniform Cost Search (UCS) Dijkstra’s algorithm**

* Expands the node with the **lowest path cost (g(n))**, not by depth.
* Works even when step costs differ.

**Properties:**

* **Completeness:** Yes (if cost > 0)
* **Optimality:** Yes
* **Time Complexity:** O(b^1+(C*/ε))
* **Space Complexity:** O(b^1+(C*/ε))

**Advantages:**

* Finds **least-cost paths**.
* Works with **non-uniform costs**.

**Disadvantages:**

* Can be slow when costs are similar or large.


lets say if we want to reach `G`

<br>
<img src="https://raw.githubusercontent.com/AghdamAmir/UCS-and-A-star-search/main/ucs-gif.gif" alt="alt" width="900">
<br>


so by using `Uniform Cost Search (UCS)` we can find the shortest path which is:

`A → C → F → G` with an total cost of `7.4`

---

### **Comparison of uninformed search algorithms**

| **Algorithm**                                     | **Uses Heuristic?** | **Complete?**                    | **Optimal?**               | **Time Complexity** | **Space Complexity** | **Data Structure**                    |
| ------------------------------------------------- | ------------------- | -------------------------------- | -------------------------- | ------------------- | -------------------- | ------------------------------------- |
| **Breadth-First Search (BFS)**                    | No                  | Yes                              | Yes (if unit cost)         | O(b^d)              | O(b^d)               | Queue (FIFO)                          |
| **Depth-First Search (DFS)**                      | No                  | No                               | No                         | O(b^m)              | O(bm)                | Stack (LIFO)                          |
| **Depth-Limited Search (DLS)**                    | No                  | Partial                          | No                         | O(b^l)              | O(bl)                | Stack (LIFO)                          |
| **Iterative Deepening Search (IDS)**              | No                  | Yes                              | Yes (if unit cost)         | O(b^d)              | O(bd)                | Stack (LIFO)                          |
| **Uniform Cost Search (UCS)**                     | No                  | Yes                              | Yes (for lowest path cost) | O(b^(C*/ε))         | O(b^(C*/ε))          | Priority Queue                        |
| **Bidirectional Search with Iterative Deepening** | No                  | Yes (if branching factor finite) | Yes (if both use BFS/IDS)  | O(b^(d/2))          | O(b^(d/2))           | Two frontiers (usually stacks/queues) |

---


<br>
<br>
<br>
<br>


## **Informed (heuristic) search:**

**Informed search** (also called *heuristic search*) uses extra problem-specific knowledge — a **heuristic function** — to guide the search toward the goal more efficiently than blind search. The heuristic provides an estimate of how “good” or how “close” a state is to the goal, allowing the algorithm to focus expansion on promising nodes.

---

## **Heuristic Function (h(n))**

A **heuristic function** is an estimate of the **cost from the current node** `n` to the **goal**.
It provides *guidance* to informed search algorithms (like **A*** and **Greedy Best-First Search**) so they can find solutions faster than uninformed methods.


In general, a **heuristic function** is evaluated based on how well it estimates the true cost to reach the goal.
The selected heuristic should be:

* **Admissible** → never overestimates the true cost (ensures optimality).
* **Consistent (Monotonic)** → satisfies `h(n) ≤ cost(n, n') + h(n')`.
* **Efficient to compute** → should be simple and fast to evaluate.
* **Problem-specific** → derived from domain knowledge of the problem.

In practice, the heuristic with the **best balance** of accuracy and computational efficiency is chosen.


> donot confuse your self with Heuristic Value & Path Cost both are an different thing

| Term                 | Symbol | Meaning                                                                                             | Type                      |
| -------------------- | ------ | --------------------------------------------------------------------------------------------------- | ------------------------- |
| **Path Cost**        | `g(n)` | The **actual cost** from the **start node** to the **current node** `n` (sum of step costs so far). | **Known / Actual**        |
| **Heuristic Value**  | `h(n)` | The **estimated cost** from the **current node** `n` to the **goal**.                               | **Estimated / Predicted** |
| **Total Evaluation** | `f(n)` | Combines both: `f(n) = g(n) + h(n)` (used in **A*** search).                                        | **Decision metric**       |


---


## **Types**


### 1. **Best-First Search**

Best-First Search is an **informed search strategy** that expands the node which appears to be the **most promising**, based on an **evaluation function** `f(n)`.

The algorithm always selects the node with the **lowest value of `f(n)`** from the frontier (open list).

**Evaluation Function:**

`f(n)` determines how desirable a node is.
Different choices of `f(n)` lead to different algorithms:

* **Greedy Best-First Search:** `f(n) = h(n)` (only heuristic)
* **A* Search:** `f(n) = g(n) + h(n)` (path cost + heuristic)


**Algorithm Steps:**

1. Place the start node in the **frontier**.
2. Select the node with the **lowest f(n)** value.
3. If it’s the **goal node**, stop.
4. Otherwise, **expand** it and add successors to the frontier.
5. Repeat until the goal is found or the frontier is empty.


**Properties:**

* **Complete:** Yes (if the search space is finite and no loops)
* **Optimal:** Depends on the evaluation function

  * Not guaranteed for `f(n) = h(n)`
  * Guaranteed for A* with admissible `h(n)`
* **Time Complexity:** Depends on heuristic accuracy
* **Space Complexity:** Can be large (stores all generated nodes)


**Advantages:**

* More efficient than uninformed searches.
* Can find solutions quickly with good heuristics.

**Disadvantages:**

* May get stuck in loops if not careful.
* Performance depends heavily on the heuristic.


<br>
<img src="https://d18l82el6cdm1i.cloudfront.net/uploads/X7rvS7Kbgc-dijkstra_animation.gif" alt="Best First Search Example" width="700">
<br>


we use: `f(n)=g(n)`

where:

`f(n)` = evaluation function (used to choose which node to expand next)
`g(n)` = total path cost from the start node to node n

it will chose the node with th `lowest f(n)` value


---


### 2. **Greedy Best-First Search**


* Greedy Best-First Search is a specific type of Best-First Search.
* Expands the node that **appears closest to the goal** based on the **heuristic value h(n)**.
* It **ignores path cost (g(n))** and relies only on the heuristic estimate.
* `f(n) = h(n)`


**Properties:**

* **Completeness:** No (can get stuck in loops)
* **Optimality:** No (does not guarantee shortest path)
* **Time Complexity:** Depends on the accuracy of `h(n)`
* **Space Complexity:** Can be high — stores all generated nodes


**Advantages:**

* Very **fast** if the heuristic is good.
* Can quickly find a **feasible (not necessarily optimal)** solution.

**Disadvantages:**

* May get **trapped in local minima**.
* **Not guaranteed to find the optimal path.**

> A local minimum is a point that looks better (cheaper or closer to goal) than all its neighbors — but it’s not actually the best path to reach the goal.



<br>
<img src="https://web.mit.edu/6.034/wwwbob/figures/BFS/A0.GIF" alt="Best First Search Example" width="700">
<br>


Each node (A, B, C, D, etc.) has an `h(n)` value — a heuristic that estimates the cost (or distance) from that node to the goal.
So, it chooses the next node purely by the smallest heuristic value (the one that looks nearest to the goal).

Path found (one possible): `C → O → I → Z`


> it will fisrt go to node `T` but it has no child nodes so it backtrack and moves to the next one but if the `T` node has infinite childs and sub childs so it will result in `inCompleteness`.

---




### 3. A* Search (A-Star Search)

* **A*** Search is an **informed search algorithm** that combines the strengths of **Uniform Cost Search (UCS)** and **Greedy Best-First Search**.
* It selects the next node based on the **lowest total estimated cost**:  
* f(n) = g(n) + h(n)

Where:

* `g(n)` = actual cost from the start node to the current node
* `h(n)` = estimated cost from the current node to the goal (heuristic)
* `f(n)` = total estimated cost of the cheapest solution through `n`


**Properties:**

* **Completeness:** Yes (if step cost > 0)
* **Optimality:** Yes (if `h(n)` is admissible — never overestimates)
* **Time Complexity:**  `O(b^d)` Exponential   , but better than uninformed search if heuristic is good
* **Space Complexity:** `O(b^d)` Can be large — keeps all generated nodes in memory


**Advantages:**

* **Guaranteed to find the optimal path** if heuristic is admissible.
* Balances **speed (heuristic)** and **accuracy (path cost)**.
* Works well even when costs differ.

**Disadvantages:**

* **Memory-intensive** — stores all nodes in the open and closed lists.
* **Performance depends** heavily on the quality of the heuristic.


> If the heuristic `h(n)` = 0, **A*** behaves exactly like **Uniform Cost Search**.
> 
> If the heuristic dominates (large `h(n)`), it behaves more like **Greedy Best-First Search**.



<br>
<img src="https://upload.wikimedia.org/wikipedia/commons/9/98/AstarExampleEn.gif" alt="A* Search Example" width="700">
<br>


| Node  | g(n) | h(n) | f(n)    |
| ----- | ---- | ---- | ------- |
| **a** | 1.5  | 4    | **5.5** |
| **b** | 3.5  | 2    | **5.5** |
| d     | 2    | 4.5  | 6.5     |
| e     | 5    | 2    | 7       |
| c     | 6.5  | 4    | 10.5    |

The NEXT node to chose is: `e` because it has smaller `f(n)` than `c` 

| Node     | g(n) | h(n) | f(n)  |
| -------- | ---- | ---- | ----- |
| **gaol** | 7    | 0    | **7** |

so the most optimal path would be:

`Start → a → b → d → e → Goal`


---
















































<!-- 

## 4. **Search Contours (f-contours / wavefronts)**

**Intuition:** A* expands nodes in increasing order of `f(n) = g + h`. Think of nodes lying on **contours of equal f-value** (like elevation contours). A* “floods” the state space by expanding nodes with the smallest f first, so the frontier roughly follows a contour of `f = constant` that moves outward until it reaches the goal’s `f = C*`.

* Nodes with `f < C*` will certainly be expanded.
* Nodes with `f = C*` may or may not be expanded depending on tie-breaking.
* Good heuristics compress the number of nodes with `f < C*` (steeper / closer contours to goal), reducing work.

This contour view helps understand why admissible heuristics that raise `h` (without overestimating) prune many nodes below the optimal contour.

---

## 5. **Heuristic Properties: Admissibility and Consistency**

### Admissible heuristic

* **Definition:** `h(n)` is *admissible* if for every node `n`: `h(n) ≤ h*(n)` where `h*(n)` is the true minimal cost from `n` to a goal.
* **Implication:** With admissible `h`, A* (tree-search) is **optimal** — it will return a least-cost solution.

### Consistent (monotone) heuristic

* **Definition:** `h` is *consistent* if for every node `n` and successor `n'` generated by action `a` with cost `c(n,a,n')`:

  ```
  h(n) ≤ c(n,a,n') + h(n')
  ```

  and for every goal state `n_goal`, `h(n_goal) = 0`.
* **Implication:** Consistency ⇒ admissibility. If `h` is consistent, then `f(n) = g(n) + h(n)` is **nondecreasing** along any path. This guarantees that when A* pops a node from the frontier, the best path to that node has been found — so nodes need not be re-expanded (graph-search is safe).

**Why these matter:**

* Use **admissible** heuristics to preserve optimality.
* Prefer **consistent** heuristics for simpler, more efficient A* implementations.

---

## 6. **Satisficing Search & Weighted A***

When you want a *good enough* solution quickly rather than the optimal one, use satisficing methods. **Weighted A*** is a popular approach.

**Weighted A*** uses:

```
f(n) = g(n) + w * h(n)
```

with weight `w > 1`.

* Larger `w` biases the search toward nodes with lower `h` (greedy behavior) — faster but may be suboptimal.
* `w = 1` reduces to A*.
* There are variants that use decreasing weights or perform post-processing to improve solution quality.

**Properties:**

* **Faster** and expands fewer nodes for `w > 1`.
* **Not optimal** unless `w = 1`.
* Often used in time-bounded planning: choose `w` to trade speed vs solution cost.

---

## 7. **Memory-Bounded Heuristic Search**

A*’s main practical limitation is **memory**. Several algorithms trade memory for time while keeping heuristic guidance.

### 7.1 Iterative-Deepening A* (IDA*)

**Idea:** combine A*’s `f`-based ordering with depth-first memory usage by performing repeated depth-first searches with increasing `f`-cost thresholds.

**Procedure:**

1. Set threshold = `f(start) = h(start)`.
2. Do a depth-first search that prunes nodes with `f(n) > threshold`.
3. If goal found, done. Otherwise, set threshold to the smallest `f` value that exceeded previous threshold and repeat.

**Properties:**

* **Memory:** linear in depth (like DFS) — O(bd).
* **Time:** may repeat work across iterations; worst-case similar to A* but often practical.
* **Optimality:** IDA* with admissible `h` finds optimal solution.
* **Good for:** large spaces where A* runs out of memory, e.g., game trees, 15-puzzle with good heuristics (pattern databases).

**Pseudocode (outline):**

```
threshold := h(start)
loop:
  t := dfs_limit(start, 0, threshold)
  if found_goal: return solution
  if t == ∞: return failure
  threshold := t   # smallest f that exceeded previous threshold
```

### 7.2 Recursive Best-First Search (RBFS)

**Idea:** RBFS is a memory-bounded best-first algorithm that uses recursion to keep track of the best alternative `f` along the path and backtracks when the current path’s `f` exceeds that alternative. It stores only a linear amount of memory (path + a few values).

**Properties:**

* **Memory:** linear in depth.
* **Time:** may re-generate nodes many times; performance typically worse than A* but better than pure DFS for heuristic guidance.
* **Behavior:** more complex to implement but useful when memory is limited.

### 7.3 Simplified Memory-Bounded A* (SMA*)

**Idea:** SMA* is an A*-like algorithm that uses all available memory; when memory is exhausted it deletes the worst frontier nodes (those with largest `f`), but remembers the best f-value among deleted descendants so it can re-generate them if needed.

**Properties:**

* **Memory-bounded** and will produce optimal solution if enough memory available; otherwise returns best possible given memory.
* More complex bookkeeping: must track pruned nodes' best-known f.

---

## 8. **When to Use Which Algorithm (Guidelines)**

* **A***: when you have a good admissible/consistent heuristic and enough memory — typical first choice for optimal solutions.
* **Greedy Best-First**: if you want a fast solution and optimality is not essential.
* **Weighted A***: to trade solution quality for speed (satisficing).
* **IDA***: when memory is severely limited but you still want optimality (useful with good heuristics).
* **RBFS / SMA***: when you need memory-bounded best-first behavior with different tradeoffs.
* **Heuristic design**: invest effort in a fast, admissible, informative heuristic (relaxed problems, pattern databases) — this often yields the largest speedup.

---

## 9. **Concrete Examples**

* **8-puzzle**:

  * Heuristics: misplaced tiles (admissible), Manhattan distance (better).
  * A* with Manhattan typically solves the 8-puzzle quickly.
  * For 15-puzzle, pattern databases or IDA* are common because of memory constraints.

* **Route finding**:

  * Heuristic: straight-line distance (Euclidean) — admissible.
  * A* with Euclidean distance finds shortest path efficiently.

* **Robot motion planning**:

  * Heuristics using lower bounds on control cost or relaxed kinematics.

---

## 10. **Summary — Key Takeaways**

* **Informed search** uses heuristics to focus search and dramatically reduce work compared to blind search.
* **A*** is the paradigmatic informed algorithm: optimal and complete with admissible/consistent heuristics, but memory-hungry.
* **Greedy Best-First** is fast but not optimal.
* **Satisficing** (Weighted A*) trades optimality for speed.
* **Memory-bounded** informed searches (IDA*, RBFS, SMA*) allow heuristic search when memory is the bottleneck.
* **Heuristic design** (admissibility, consistency, dominance) is central — a stronger admissible heuristic is the single most effective way to improve performance.

---

If you want, I can now:

* Show **A*** and **IDA*** implemented in Python for a small example (8-puzzle or grid pathfinding).
* Produce **visual diagrams** showing A* expanding contours and IDA* iterations.
* Provide a short exercise you can use in class or for practice.

Which of these would you like next? -->
