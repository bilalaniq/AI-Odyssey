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

---
