# Intelligent Agents

In **Artificial Intelligence (AI)**, an **agent** is **anything that can perceive its environment, make decisions, and act upon it to achieve specific goals**.

In simpler terms:

> An **AI agent** is an intelligent entity that **observes**, **thinks**, and **acts** — just like a human or robot trying to accomplish a task.

An **agent** can be defined as:

> **Agent = Perception + Reasoning + Action**

It **perceives** the environment through *sensors* and **acts** on the environment through *actuators*.

### **Example**

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
    - [**Example**](#example)
  - [Table of Contents](#table-of-contents)
  - [**The Agent–Environment Loop**](#the-agentenvironment-loop)
    - [Structure of Intelligent Agents](#structure-of-intelligent-agents)
      - [Key Components](#key-components)
  - [**Types of Agents**](#types-of-agents)
  - [**Performance Measure \& Rationality**](#performance-measure--rationality)
  - [**Environment Types**](#environment-types)
    - [**In summary**](#in-summary)

---





## **The Agent–Environment Loop**

Every AI agent follows this cycle:

1. **Perceive** the environment (input)
2. **Think** or **decide** (reasoning, planning, or learning)
3. **Act** on the environment (output)
4. **Receive feedback** and repeat


<img src="https://www.kdnuggets.com/wp-content/uploads/joshi_understanding_agent_environment_ai_1.png" alt="AGENTFLOW" width="700">


### Structure of Intelligent Agents

#### Key Components

* **Sensors:** Perceive the environment (e.g., cameras, microphones, temperature sensors).
* **Actuators:** Act upon the environment (e.g., motors, displays, speakers).
* **Agent Function:** Maps percept histories to actions — defines how the agent behaves in every situation.

> In theory, we could list every possible percept and its corresponding action in a massive table,but for most agents, this table would be **enormous (often infinite!)**.

> Instead of storing every possible “situation → action” pair, AI agents compute actions dynamically using algorithms, models, and memory.


---

## **Types of Agents**

| **Type**                     | **Description**                                                 | **Example**                                |
| ---------------------------- | --------------------------------------------------------------- | ------------------------------------------ |
| **Simple Reflex Agent**      | Acts only on the current situation using condition–action rules | Thermostat (“If temp > 25°C → Turn on AC”) |
| **Model-Based Reflex Agent** | Keeps track of part of the world it can’t see                   | Robot vacuum using room map                |
| **Goal-Based Agent**         | Acts to achieve specific goals                                  | GPS navigation system                      |
| **Utility-Based Agent**      | Maximizes happiness or performance measure                      | Stock trading bot optimizing profit        |
| **Learning Agent**           | Improves over time through experience                           | Self-learning game AI or ChatGPT           |

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

## **Environment Types**

Agents operate in different **environments**, which affect their design:

| **Property**             | **Example**                    |
| ------------------------ | ------------------------------ |
| **Fully Observable**     | Chess game (all info visible)  |
| **Partially Observable** | Driving (can’t see everything) |
| **Deterministic**        | Solving a math puzzle          |
| **Stochastic**           | Stock market                   |
| **Static**               | Crossword puzzle               |
| **Dynamic**              | Football match                 |
| **Discrete**             | Turn-based board game          |
| **Continuous**           | Real-world navigation          |

---

### **In summary**

> An **AI agent** is an intelligent entity that perceives its surroundings, reasons about what to do, and acts to achieve its goals.

Or simply:

> **Agent = Sensor + Intelligence + Actuator**

---

Would you like me to include a **diagram-based explanation** (in Markdown or image form) of the agent–environment interaction model next? It’s often used in AI textbooks (like Russell & Norvig).
