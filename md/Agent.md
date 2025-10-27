# Intelligent Agents

In **Artificial Intelligence (AI)**, an **agent** is **anything that can perceive its environment, make decisions, and act upon it to achieve specific goals**.

In simpler terms:

> An **AI agent** is an intelligent entity that **observes**, **thinks**, and **acts** — just like a human or robot trying to accomplish a task.

An **agent** can be defined as:

> **Agent = Perception + Reasoning + Action**

It **perceives** the environment through *sensors* and **acts** on the environment through *actuators*.

**Example**

| Agent Type                 | Sensors               | Actuators        | Task                             |
| -------------------------- | --------------------- | ---------------- | -------------------------------- |
| **Robot Vacuum (Roomba)**  | Bump sensors, cameras | Motors           | Clean the floor                  |
| **Self-driving Car**       | Cameras, radar, GPS   | Steering, brakes | Drive safely to destination      |
| **Chatbot (like ChatGPT)** | Text input            | Text output      | Answer questions or assist users |
| **Stock Trading AI**       | Market data           | Buy/sell orders  | Maximize profit                  |

---



---


<img src="https://media.licdn.com/dms/image/v2/D4D10AQH8H85O4nxC9g/image-shrink_800/image-shrink_800/0/1736869015888?e=2147483647&v=beta&t=xOLh8ZQzNnBnAOdC8sexg2IFuFthfIDlL7Zp6LJ5GcY" alt="meme" width="300">


---

## Table of Contents
- [Intelligent Agents](#intelligent-agents)
  - [Table of Contents](#table-of-contents)
  - [**The Agent–Environment Loop**](#the-agentenvironment-loop)
    - [Structure of Intelligent Agents](#structure-of-intelligent-agents)
  - [**Performance Measure \& Rationality**](#performance-measure--rationality)
  - [**Task Environment**](#task-environment)
    - [**PEAS – Components of a Task Environment**](#peas--components-of-a-task-environment)
    - [**Properties and Examples of Task Environments**](#properties-and-examples-of-task-environments)
- [**Types of Agents**](#types-of-agents)
  - [**Simple reflex agent:**](#simple-reflex-agent)
    - [**Simple Reflex Agent: Strengths and Weaknesses**](#simple-reflex-agent-strengths-and-weaknesses)
  - [**Model-Based Reflex Agent**](#model-based-reflex-agent)
    - [**Model-Based Reflex Agent: Strengths and Weaknesses**](#model-based-reflex-agent-strengths-and-weaknesses)
  - [**Goal-Based Agent**](#goal-based-agent)
    - [**Goal-Based Agent: Strengths and Weaknesses**](#goal-based-agent-strengths-and-weaknesses)
  - [**Utility-Based Agents**](#utility-based-agents)
    - [**Utility-Based Agents: Strengths and Weaknesses**](#utility-based-agents-strengths-and-weaknesses)
  - [**Learning Agent**](#learning-agent)
    - [**Learning Agent: Strengths and Weaknesses**](#learning-agent-strengths-and-weaknesses)
- [Comparison of AI Agent Types](#comparison-of-ai-agent-types)

---





## **The Agent–Environment Loop**

Every AI agent follows this cycle:

1. **Perceive** the environment (input)
2. **Think** or **decide** (reasoning, planning, or learning)
3. **Act** on the environment (output)
4. **Receive feedback** and repeat


<img src="https://www.kdnuggets.com/wp-content/uploads/joshi_understanding_agent_environment_ai_1.png" alt="AGENTFLOW" width="700">


### Structure of Intelligent Agents

* **Sensors:** Perceive the environment (e.g., cameras, microphones, temperature sensors).
* **Actuators:** Act upon the environment (e.g., motors, displays, speakers).
* **Agent Function:** Maps percept histories to actions — defines how the agent behaves in every situation.

> In theory, we could list every possible percept and its corresponding action in a massive table,but for most agents, this table would be **enormous (often infinite!)**.

> Instead of storing every possible “situation → action” pair, AI agents compute actions dynamically using algorithms, models, and memory.

---

## **Performance Measure & Rationality**

**Performance Measure in AI** defines how an agent’s success is evaluated.
It assesses the **effects of an agent’s actions** on the environment over time.
If the outcomes are desirable, the agent performs well; if not, it performs poorly.
It provides the **criterion for rational behavior** — guiding agents to act optimally.
In short, it is the **yardstick of success** for any intelligent agent.


Rationality means doing the right thing to achieve the best outcome.
It depends on four things:

1. The **performance measure** (how success is judged).
2. The **agent’s knowledge** about the environment.
3. The **actions** the agent can take.
4. The **percepts** (what the agent has observed so far).

A **rational agent** always chooses the action that gives the best expected result.
For example, if moving unnecessarily reduces points, a smart agent will avoid moving without reason.

---


## **Task Environment**

A **task environment** defines **everything that affects how an intelligent agent behaves**.

Formally:

> “A combination of performance measure, the environment, and the agent’s actuators and sensors.”

To describe a task environment, we use the **PEAS framework**:

### **PEAS – Components of a Task Environment**

| Component               | Description                                             | Example (Autonomous Taxi)                                |
| ----------------------- | ------------------------------------------------------- | -------------------------------------------------------- |
| **Performance Measure** | Criteria for success (what the agent tries to maximize) | Safe, fast, legal, comfortable driving; maximize profits |
| **Environment**         | The surroundings or world in which the agent operates   | Roads, traffic, pedestrians, weather, customers          |
| **Actuators**           | Devices that perform actions                            | Steering, accelerator, brake, horn, signal               |
| **Sensors**             | Devices that gather information from the environment    | Cameras, sonar, GPS, speedometer, accelerometer          |

---

### **Properties and Examples of Task Environments**

| **Property**                                         | **Description**                                                                                           | **Fully Observable Example**                                            | **Partially Observable Example**                                           |
| ---------------------------------------------------- | --------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| **Fully observable vs. Partially observable**        | Determines whether the agent has complete access to the environment’s state.                              | **Chess** – the entire board is visible.                                | **Driving** – can’t see hidden obstacles or other drivers’ intentions.     |
| **Deterministic vs. Non-deterministic (Stochastic)** | Checks if the next state is completely determined by the current state and action.                        | **Solving a math puzzle** – outcome fully determined by rules.          | **Stock market / Driving** – involves randomness and uncertainty.          |
| **Episodic vs. Sequential**                          | In episodic tasks, each decision is independent; in sequential tasks, past actions affect future ones.    | **Defect detection** – each product check is independent.               | **Playing chess / Driving** – each move affects future states.             |
| **Static vs. Dynamic**                               | In a static environment, the world doesn’t change while the agent is deciding; in a dynamic one, it does. | **Crossword puzzle** – puzzle stays the same while solving.             | **Football match / Driving** – environment changes continuously.           |
| **Discrete vs. Continuous**                          | Determines whether there are a finite or infinite number of possible states/actions.                      | **Turn-based board game (chess, tic-tac-toe)** – finite moves per turn. | **Real-world navigation / Driving** – continuous time, space, and control. |
| **Single-agent vs. Multi-agent**                     | Defines whether the agent operates alone or with other agents (cooperative or competitive).               | **Crossword solving** – only one agent involved.                        | **Chess / Football match** – involves multiple agents or opponents.        |


---

<br>
<br>
<br>
<br>
<br>


# **Types of Agents**

![types of agent](https://csveda.com/wp-content/uploads/2021/07/AI-Agents-Types.jpg)
<br>
<br>

## **Simple reflex agent:**

A **Simple Reflex Agent** is the **most basic type of intelligent agent** in Artificial Intelligence.
It **acts only based on the current percept (input from sensors)** — without considering the history of previous percepts.

* The agent **perceives** the environment through its sensors.
* It uses a set of **condition–action rules** (also called **if–then rules**) to decide what to do.
* It performs the **corresponding action** through its actuators.

> **Rule format:**
> *If condition is true → then perform action.*

The agent **does not store past information** and **cannot learn or plan** ahead.

<br>
<br>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20240513180031/ai3-1.webp" alt="AGENTFLOW" width="700">
<br>
<br>

> Example: A vacuum cleaner **sucks dirt if the square is dirty**, otherwise **moves to the next square**.
It **does not remember the past** or consider future consequences.


### **Simple Reflex Agent: Strengths and Weaknesses**

**Strengths:**

* Simple and easy to implement
* Fast and efficient
* Works well in well-defined, fully observable environments

**Weaknesses:**

* Limited adaptability
* Cannot learn from experience
* Requires a fully observable environment


---

## **Model-Based Reflex Agent**

A **Model-Based Reflex Agent** is an improved version of the **Simple Reflex Agent**.
It can handle **partially observable environments** by keeping track of **some internal state** — a model of the world — to remember past information.

* The agent maintains an **internal model** that represents the **current state of the world**.
* It updates this model based on **percepts (sensor inputs)** and **actions taken**.
* Decisions are still based on **condition–action rules**, but now these rules can depend on both **current percepts** and the **internal state**.


| **Feature**                 | **Description**                                                   |
| --------------------------- | ----------------------------------------------------------------- |
| **Memory**                  | Maintains internal state to track unseen parts of the environment |
| **Learning**                | Limited; can update internal model but not improve rules          |
| **Environment Suitability** | Works in **partially observable** and **dynamic** environments    |
| **Example**                 | Advanced vacuum cleaner, simple mobile robot                      |


<br>
<br>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/art1.png" alt="AGENTFLOW" width="700">
<br>
<br>


> Example: If the vacuum can’t see both rooms at once, it remembers which one was cleaned before:
>
> * If current square is dirty → **Suck dirt**
> 
> * If current square is clean and left room was dirty before → **Move left**
> 
> * Otherwise → **Move right**



---

### **Model-Based Reflex Agent: Strengths and Weaknesses**

**Strengths:**

* Works in partially observable environments
* Keeps track of unobserved information using memory

**Weaknesses:**

* More complex to design
* The agent’s performance relies heavily on the accuracy of its internal model
* Still limited in learning and adaptability

---

## **Goal-Based Agent**

A **Goal-Based Agent** is a more advanced type of intelligent agent that makes decisions not just based on current conditions, but also on a **desired goal or outcome** it wants to achieve.

* The agent uses its **percepts** (inputs) and **internal model** of the world.
* It checks what **actions** will help it **reach a specific goal**.
* It can **compare different possible actions** and **choose the one** that brings it closer to the goal.

> In short: It doesn’t just react — it **plans and chooses actions** to achieve a goal.


| **Feature**         | **Description**                                       |
| ------------------- | ----------------------------------------------------- |
| **Goal awareness**  | Can reason about future states and desired outcomes   |
| **Decision-making** | Chooses actions that help achieve a specific goal     |
| **Flexibility**     | Can change behavior when the goal changes             |
| **Example**         | Navigation system, chess-playing AI, self-driving car |

<br>
<br>
<img src="https://tutorialforbeginner.com/images/ai/goal-based-agent.png" alt="AGENTFLOW" width="700">
<br>
<br>


> Example: Autonomous Taxi
>
> * **Goal:** Drop the passenger safely at the destination.
> 
> * **Actions:** Plan route, avoid obstacles, follow traffic rules, adjust to road changes.



### **Goal-Based Agent: Strengths and Weaknesses**

**Strengths:**

* Can plan and make better decisions
* Flexible and adaptable to changing goals

**Weaknesses:**

* Requires goal definition and planning algorithms
* More computationally expensive than reflex agents
* If the agent doesn’t have complete information about the environment, its planning might be flawed

---

## **Utility-Based Agents**

A **Utility-Based Agent** is an advanced type of intelligent agent that doesn’t just aim to **achieve a goal**, but also tries to achieve it in the **best possible way** — maximizing performance, comfort, safety, or satisfaction.

It evaluates **how desirable each possible state (or outcome)** is, using a **utility function** that assigns a *numerical value* to each state.

1. The agent receives **percepts** from the environment.
2. It uses its **model** to predict possible future states.
3. For each state, it calculates a **utility value** (how good or useful that state is).
4. It chooses the **action that leads to the highest utility** (most desirable result).

> **In short:**
> 
> A goal-based agent asks: “Will this action reach my goal?”
> 
> A utility-based agent asks: “*Which* action will reach my goal *better*?”

| **Feature**          | **Description**                                                  |
| -------------------- | ---------------------------------------------------------------- |
| **Utility Function** | Measures how good or desirable a state is                        |
| **Decision-Making**  | Chooses action that gives the highest expected utility           |
| **Planning**         | Considers multiple possible outcomes                             |
| **Flexibility**      | Can handle trade-offs between competing goals                    |
| **Examples**         | Self-driving car, recommendation systems, financial trading bots |



<br>
<br>
<img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjPKFQ3VeVItAeHEuRKdluG7ZWx1s6TtI7HvK3CWlMv15fKGon6VU42GcnWLJXo0PE5zWPKpPQzpbUDh-hhSF4eSDP8_SYub8WKgsl0MRiSqEQsnGUbx_dQvd1bq-2-TZlSPT5zyEEwGtS6/s640/fig_2_14.jpg" alt="AGENTFLOW" width="700">
<br>
<br>





> Example: Self-Driving Car
>
> * **Goal-Based Agent:** “Reach the destination.”
> 
> * **Utility-Based Agent:** “Reach the destination *safely, quickly, and comfortably*.”

It might take a slightly longer route if it’s safer or has less traffic — because it **maximizes total utility**, not just goal completion.


### **Utility-Based Agents: Strengths and Weaknesses**

**Strengths:**

* Makes more **intelligent, balanced, and optimal decisions**
* Can handle **uncertain and complex environments**. These AI agents are flexible and adaptive
* Allows **fine-grained trade-offs** (e.g., safety vs. speed)
* Utility-based agents can consider factors like risk, time, and effort when evaluating different options

**Weaknesses:**

* Designing the utility function is complex
* Requires designing an accurate **utility function**
* **Computationally expensive** — must evaluate many possibilities
* There is a degree of uncertainty about the outcomes

---

## **Learning Agent**


A **Learning Agent** in AI is an agent that **improves its performance over time** by learning from its experiences, rather than relying solely on fixed rules like a simple reflex agent.


A learning agent **adapts its behavior** based on feedback from the environment. It can learn from **past actions and results** to make better decisions in the future.

A learning agent typically has **four main components**:

1. **Performance Element** – chooses actions based on current knowledge.
2. **Learning Element** – modifies the performance element based on experience.
3. **Critic** – provides feedback on how well the agent is performing.
4. **Problem Generator** – suggests actions that lead to new experiences for learning.


<br>
<br>
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20190704232940/learning-agent.png" alt="AGENTFLOW" width="700">
<br>
<br>



> Example: Robot Vacuum Cleaner (Learning Version)
>
>* Starts by randomly moving in the room.
>
>* Learns which areas are dirtier or more frequently visited.
>
>* Adapts its movement to clean efficiently over time.

### **Learning Agent: Strengths and Weaknesses**

**Strengths:**

* Can adapt to changes in the environment
* Improves performance through experience
* Handles complex and uncertain situations

**Weaknesses:**

* Needs time and data to learn
* May make mistakes while learning
* Requires more computational resources


> only learning agents update their behavior based on experience, while the others just follow pre-defined rules or plans.

---

<br>
<br>
<br>



# Comparison of AI Agent Types

| **Feature**                 | **Simple Reflex Agent**                                             | **Model-Based Reflex Agent**                          | **Goal-Based Agent**                         | **Utility-Based Agent**                                      | **Learning Agent**                                            |
| --------------------------- | ------------------------------------------------------------------- | ----------------------------------------------------- | -------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------- |
| **Basis of Action**         | Acts only on **current percept** using fixed condition–action rules | Acts on **current percept + internal state (memory)** | Acts to **achieve specific goals**           | Acts to **maximize utility (best possible outcome)**         | Acts based on **learned knowledge and experience**            |
| **Memory / Internal Model** | None                                                                | Maintains an **internal model** of the world          | Uses an internal model for planning          | Uses an internal model and evaluates multiple outcomes       | Continuously **updates its internal model through learning**  |
| **Learning Capability**     | No                                                                  | Very limited (only updates state)                     | No explicit learning                         | May adapt slightly using utility values                      | **Yes – learns from experience and feedback**                 |
| **Goal Awareness**          | No                                                                  | No                                                    | **Yes**                                      | **Yes (plus preferences)**                                   | **Yes (and learns to achieve goals better)**                  |
| **Decision-Making**         | Based on fixed **if–then** rules                                    | Based on rules + stored state                         | **Plans** actions to reach a goal            | **Evaluates** and selects best action using utility function | **Improves** decisions using past performance and learning    |
| **Adaptability**            | None                                                                | Limited                                               | Moderate (can change plan if goal changes)   | High (can balance multiple goals)                            | **Very high (adapts to environment and improves)**            |
| **Environment Type**        | **Fully observable, static**                                        | **Partially observable, dynamic**                     | **Dynamic and goal-oriented**                | **Dynamic, uncertain, multi-objective**                      | **Dynamic, uncertain, changing**                              |
| **Computation Complexity**  | Low                                                                 | Moderate                                              | High                                         | Very High                                                    | High (depends on learning algorithm)                          |
| **Knowledge Source**        | Fixed rules programmed by designer                                  | Rules + internal model of world                       | Goals + environment model                    | Goals + utility function                                     | Goals + learned knowledge                                     |
| **Flexibility**             | Very low                                                            | Low                                                   | High                                         | Very high                                                    | **Highest**                                                   |
| **Improvement Over Time**   | None                                                                | Limited (model updates)                               | None (until goal changes)                    | Possible (if utility function is updated)                    | **Continuous** — improves with experience                     |
| **Example**                 | Basic vacuum cleaner that cleans if dirt detected                   | Vacuum that remembers which room is dirty             | Taxi planning a route to reach destination   | Self-driving car optimizing safety, comfort, and speed       | Robot vacuum that learns best cleaning pattern over time      |
| **Strengths**               | Simple, fast, efficient in static environments                      | Handles partial observability                         | Plans and adapts to changing goals           | Makes optimal decisions balancing trade-offs                 | Learns and adapts automatically; improves efficiency          |
| **Weaknesses**              | No learning, no memory, limited to simple tasks                     | Relies on model accuracy, still no learning           | Needs goal definition and planning algorithm | Designing utility function is complex and costly             | Requires data, time, and computation; may make mistakes early |


---






 