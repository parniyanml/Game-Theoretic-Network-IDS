# Game Theoretic Models for Network Intrusion Detection 🛡️♟️

This repository hosts a research project analyzing the application of **Game Theory** to enhance **Network Intrusion Detection Systems (IDS)**. The project models the interaction between an Attacker and the IDS as a strategic game to find optimal defense strategies.

**Author:** Parniyan Malekzadeh
**Course:** Game Theory (Supervisor: Dr. Narimani)
**University:** Isfahan University of Technology (IUT)

## 📄 Abstract
Traditional IDS often rely on static rules. This project investigates a dynamic approach where the interaction between the IDS and attacker(s) is modeled as a **Non-Cooperative Zero-Sum Game**. We utilized the **Minimax** theorem and **Max-Flow Min-Cut** duality to derive optimal sampling strategies for the IDS and routing strategies for the attacker.

## 🧠 Key Concepts Analyzed

### 1. Game Formulation
* **Players:** The IDS (Defender) vs. Smart Attacker(s).
* **Strategy:** The IDS allocates sampling budget across network links; the Attacker chooses paths to inject malicious packets.
* **Payoff:** Defined based on the probability of detection vs. successful intrusion.

### 2. Scenarios
* **Single Smart Attacker:** Analyzing optimal packet routing to evade detection.
* **Cooperative Attackers:** Modeling a coordinated attack where multiple adversaries collaborate to saturate the IDS.

### 3. Theoretical Solutions
* **Minimax Approach:** Determining the equilibrium where the IDS minimizes the maximum possible damage.
* **Max-Flow Min-Cut:** Proved that the optimal IDS strategy focuses sampling resources on the network's "Minimum Cut" (bottlenecks).

## 📊 Key Findings
The analysis demonstrates that a game-theoretic allocation of resources significantly outperforms uniform or random sampling, especially in networks with distinct bottlenecks.

## 📂 Repository Contents
* `report/`: Full technical report and mathematical proofs (PDF).
* `slides/`: (Optional) Presentation slides used for the project defense.

---
*This project is an analysis of the paper "Game theoretic models for detecting network intrusions" adapted for the Game Theory course.*
