# Game-Theoretic-Network-IDS

**A research analysis on applying Game Theory (Zero-Sum Games & Minimax) to optimize Network Intrusion Detection Systems (IDS) against smart attackers.**

## Project Overview

This project explores the intersection of cybersecurity and game theory. It addresses the challenge of detecting network intrusions when the Intrusion Detection System (IDS) is constrained by a limited sampling budget and faces intelligent adversaries.

Traditional IDS approaches often rely on random or uniform packet sampling, which can be inefficient against sophisticated attacks. This research models the interaction between the Attacker and the IDS as a non-cooperative, zero-sum game with complete information. The objective is to derive an optimal sampling strategy that maximizes the probability of detection while adhering to resource constraints.

## Table of Contents

* [Network Model](#network-model)
* [Game Scenarios](#game-scenarios)
* [Mathematical Formulation](#mathematical-formulation)
* [Key Findings](#key-findings)
* [Reference Paper](#reference-paper)
* [Credits](#credits)

## Network Model

The network is modeled as a directed graph $G=(N,E)$, where $N$ represents nodes (routers/hosts) and $E$ represents edges (links).

* **IDS Constraints:** The IDS cannot analyze every packet due to resource limitations. It operates under a fixed global sampling budget, $B_s$.
* **Sampling Rate:** The IDS assigns a sampling rate $s_e$ to each link $e$, such that $\sum_{e \in E} s_e \le B_s$.
* **Attack Flow:** The intruder aims to send malicious packets from a source node to a target node without detection.

## Game Scenarios

The research analyzes two distinct adversarial scenarios:

### 1. Single Smart Intruder (Flow Fragmentation)
In this scenario, a single intelligent intruder splits an attack into $n$ distinct fragments (packets).
* The attacker routes these fragments through different paths to evade detection.
* To successfully detect the intrusion, the IDS must capture at least $m$ out of the $n$ fragments.
* The optimal number of fragments required for detection ($m$) is derived as a function of the detection probability $\alpha$, specifically $m = n\alpha$.

### 2. Cooperative Intruders
In this scenario, a group of distributed attackers ($|\Omega|$) coordinate to target a single victim.
* The attack is distributed among multiple malicious actors.
* The IDS must optimize the average probability of detection across all attackers.
* The total sampling budget is effectively divided among the potential attackers to handle the distributed threat.

## Mathematical Formulation

The core of the analysis utilizes the **Minimax Theorem** and **Linear Programming Duality**. The interaction is defined as:

$$\theta = \max_{p \in U} \min_{q \in V} \text{Payoff}(p, q)$$

Where:
* $p$ is the IDS sampling strategy.
* $q$ is the attacker's path selection strategy.

### The Max-Flow Min-Cut Solution
The analysis demonstrates that the optimal strategy for the IDS corresponds to the **Max-Flow Min-Cut** theorem.

1.  **Attacker Strategy:** Perform a flow decomposition on the Maximum Flow ($MF$) from the source to the target. The attacker distributes traffic probability proportional to the flow on available paths.
2.  **IDS Strategy:** Identify the **Minimum Cut** sets of the network. The optimal sampling budget should be concentrated entirely on the edges belonging to these minimum cuts, as they represent the network bottlenecks.

The optimal sampling rate for an edge $e$ in the minimum cut is calculated as:
$$s_e = B_s \frac{f_e}{MF}$$
Where $f_e$ is the traffic flow on edge $e$ and $MF$ is the maximum flow value.

## Key Findings

Numerical simulations yield the following conclusions regarding the proposed Game-Theoretic model compared to Random and Uniform sampling methods:

1.  **Superior Detection Rates:** The Game-Theoretic model consistently achieves a higher probability of detection compared to random or uniform sampling strategies for the same budget.
2.  **Budget Efficiency:** By concentrating resources on "cut" edges (bottlenecks), the IDS ensures that the attacker cannot bypass the surveillance mechanism without traversing a monitored link.
3.  **Cooperative Limit:** In scenarios with a very high number of cooperative intruders (e.g., exceeding 50% of network nodes), the performance of the game-theoretic model degrades. This occurs because the union of minimum cuts grows to encompass nearly the entire network, diluting the concentrated budget advantage.

## Reference Paper

This project is an analysis and implementation based on the following research:

> Otrok, H., Mehrandish, M., Assi, C., Debbabi, M., & Bhattacharya, P. (2008). **"Game Theoretic Models for Detecting Network Intrusions."** *Computer Communications*, 31(14), 3352-3362.

## Credits

**Analysis & Report By:** Parniyan Malekzadeh
**Supervisor:** Dr. Narimani
**Institution:** Isfahan University of Technology
