# README: CGO-based Bi-Objective Workflow Scheduler

# Chaos-Game-Optimization based Multi-Objective Task Scheduler

This repository implements a multi-objective task scheduling algorithm using *Chaos Game Optimization (CGO)*. It is designed for heterogeneous Fog-Cloud computing environments, aiming to minimize:

- *Makespan* (total execution time)
- *Energy consumption* (base, active, idle)

The algorithm schedules DAG-based workflows onto heterogeneous nodes while considering:
- Node processing speeds (MIPS)
- Power consumption (base, active, idle)
- Communication delays (bandwidth & propagation)

---

## ✨ Features

- HEFT-based semi-greedy initialization
- CGO triangle operator using *Dirichlet distribution*
- Population-level exploration via *mean-group vector*
- Mutation and clipping for diversity
- Pareto front analysis
- Gantt chart and DAG visualization
- Convergence tracking (Makespan vs Energy)

---

## 📁 File Structure


.
├── cgo_multiobjective_scheduler.py  # Main Python script
├── README.md                        # You're here!


---

## 🚀 How to Run

Make sure you have the required libraries:

bash
pip install matplotlib networkx numpy


Then run the script:

bash
python cgo_multiobjective_scheduler.py


---

## 📊 Visual Outputs

You will see:

1. *Task DAG* — showing task dependencies  
2. *Gantt Chart* — mapping of tasks to nodes with timing  
3. *Convergence Plot* — shows Makespan and Energy over generations  
4. *Pareto Front* — trade-off between makespan and energy in final population  

Console output also shows the *best task-node mapping* and total metrics.

---

## 📈 Example Output


Best mapping (task -> node): [2, 2, 2, 2, 2, 2]
Makespan = 5.000 s, Energy = 26.800 J

Task 0: Node 2 | Start 0.00s | End 0.75s
Task 1: Node 2 | Start 0.75s | End 1.38s
...


---

## ⚙ Customization

- Modify NUM_TASKS, NODES, or BW/PROP to simulate other environments
- Adjust POP_SIZE, MAX_GEN, MUTATE_P for different CGO behavior

---

## 📚 Reference

This implementation is inspired by:
> Chaos Game Optimization: A New Metaheuristic Algorithm for Solving Engineering Problems, Mirjalili et al.



