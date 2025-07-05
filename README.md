# README: CGO-based Bi-Objective Workflow Scheduler

## 📌 Overview

This project implements a bi-objective workflow scheduler that optimizes both Makespan and Energy Consumption. It utilizes:

* A Directed Acyclic Graph (DAG) representing task dependencies.
* Chaos Game Optimization (CGO) to evolve task priorities.
* EST & Upward Rank-based priority calculation inspired by NSGA-IIwithsemi-greedyinitialization
* Heterogeneous Virtual Machines (VMs).

The goal is to find Pareto-optimal task schedules across multiple generations.

---

## ⚙️ Features

* Supports input DAG with task execution times and dependencies
* Computes EST (Earliest Start Time) and upward rank for each task
* Constructs priority list using weighted combination:  α × EST + β × Rank
* Repairs priority list using topological sort to respect dependencies
* Applies CGO to explore solution space across generations
* Visualizes:

  * DAG of input workflow
  * Gantt chart of best schedule

---

## 📂 Project Structure

All logic is contained in a single Python script.
It uses matplotlib and networkx for plotting.

---

## 🔄 Algorithm Flow

1. 📥 Input Definition:

   * List of tasks: {id, exec\_time, dependencies}
   * List of VMs: {id, speed, energy\_factor}

2. 🧠 Compute Task Metrics:

   * EST: Forward traversal over DAG
   * RankU: Backward traversal for upward rank

3. 🧮 Initial Priority Generation:

   * For each task:
     priority = α × EST + β × rank  (α + β = 1, randomly generated)

4. 🛠 Repair Priority:

   * Priority list is repaired to obey topological constraints using DFS.

5. 🗓️ Schedule Evaluation:

   * Based on earliest ready time, VM assignment, and execution duration.
   * Fitness = \[Makespan, Energy]

6. 🔁 Chaos Game Optimization:

   * For each generation:

     * Select elite solutions from previous generation
     * Randomly apply chaotic update to priority list using logistic map
     * Repair updated priorities
     * Re-evaluate fitness

7. ✅ Output:

   * Best schedule with lowest makespan and energy
   * Gantt chart for visualization

---

## 📊 Output Example

* Input DAG (T1 → T2,T3 → T4 → T5)
* Gantt chart showing task execution across VMs
* Console output:

  ```
  Best Makespan: 46.67, Energy: 124.50
  ```

---

## 📦 Dependencies

Install required packages:

```bash
pip install matplotlib networkx
```

---

## 🚀 How to Run

1. Open the script
2. Customize task/VM definitions if needed
3. Run using:

```bash
python your_script.py
```

---

## 🔧 Customization

* Modify tasks and VM definitions in the main section.
* Adjust population size or number of generations.
* Add your own cost functions (e.g., deadline, reliability).

---

## 📚 References
* CGO: Chaos Game Optimization technique for exploration
* DAG + Topological Repair ensures valid execution order

---


# 🐦 Cuckoo Search with Simulated Annealing and Lévy Flight for Optimizing Healthcare IoT in Fog Networks  

## 📌 Project Overview  
This project implements an **optimized Cuckoo Search Algorithm (CSA)** combined with **Simulated Annealing (SA)** and **Lévy Flight (LF)** to **minimize bandwidth usage and latency** in **Healthcare IoT (HIoT) within Fog Computing environments**.  

### **Key Features**  
✔️ **Cuckoo Search Algorithm (CSA)** for task allocation  
✔️ **Lévy Flight-based exploration** for global optimization  
✔️ **Simulated Annealing (SA)** for local optimization  
✔️ **Energy and cost analysis** for optimized task scheduling  
✔️ **Scalable implementation** with synthetic data generation  

---

## 🏥 Why This Project?  
Fog computing in **Healthcare IoT (HIoT)** involves managing tasks efficiently to **reduce**:  

📉 **Bandwidth Usage** 🚀 *(Less data transfer to the cloud)*  
⏳ **Latency** *(Faster processing at the fog layer)*  
🔋 **Energy Consumption** *(Optimized resource utilization)*  
💰 **Cost** *(Less operational expenses)*  

By using **CSA+SA+LF**, we achieve **optimal task scheduling** for **efficient resource allocation** in **fog networks**.

---

## 📊 How It Works?  

### **Algorithmic Flow:**  
```mermaid
graph TD;
    A[Initialize Population of Cuckoos] --> B[Generate Lévy Flights for Exploration]
    B --> C[Evaluate Fitness (Latency, Bandwidth, Energy, Cost)]
    C --> D[Apply Simulated Annealing for Local Optimization]
    D --> E[Replace Worst Solutions with New Ones]
    E --> F[Check Stopping Criteria]
    F -->|Not Satisfied| B
    F -->|Satisfied| G[Return Optimal Task Allocation]
