# EcoFair-DSM: Hybrid LCA-ABMS Simulation Framework

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python](https://img.shields.io/badge/Made%20with-Python-blue.svg)](https://www.python.org/)

**EcoFair-DSM** is a hybrid simulation framework that integrates **Lifecycle Assessment (LCA)** with **Agent-Based Modeling (ABMS)**. It is designed to evaluate the trade-offs between economic efficiency, environmental impact, and supplier fairness in digital marketplaces.

This repository contains the source code used for the case study and policy evaluation presented in the paper: **"A Hybrid LCA-ABMS Framework for Fairness-Aware Supply Chains: Evaluating Digital Product Passports Beyond Static Averages."**

---

## 🚀 Key Features

* **Hybrid Modeling:** Combines static/individualized environmental data (LCA) with dynamic agent behavior (ABMS).
* **DPP Integration:** Simulates **Individualized (DPP)** environmental data to test policy effectiveness beyond industry averages.
* **Fairness Mechanisms:** Implements **Jain’s Fairness Index**, Rotation Fairness, and Disparity Fairness to control supplier allocation.
* **Policy Simulation:** Built-in scenarios for **Carbon Pricing**, **Fairness-Weighted Ranking**, and **Combined Policies**.
* **Modular Architecture:** Distinct modules for Agents, Environmental Data, Fairness Logic, and Marketplace Matching.

---

## 📂 Project Structure

The project is organized into cohesive modules mirroring the framework design:

* `src/agents/`: Definitions for Suppliers, Buyers, and the Regulator.
* `src/environment/`: Modules for Static vs. Individualized (DPP) emission data.
* `src/marketplace/`: Core logic for Matchmaking, Scoring, and Allocation (Sequential vs. Proportional).
* `src/fairness/`: Algorithms for calculating Rotation and Disparity fairness signals.
* `src/analysis/`: Tools for data logging and generating the results graphs.

---

## 🧪 Simulation Scenarios

The framework allows you to run the four specific policy scenarios analyzed in the paper:

| Scenario | Description | Key Settings |
| :--- | :--- | :--- |
| **S1 (Baseline)** | Cost-driven selection with Static LCA data. | No Carbon Tax, Sequential Allocation. |
| **S2A** | Carbon pricing applied to Static LCA data. | $\tau > 0$, Static Data. |
| **S2B** | Carbon pricing applied to **Individualized (DPP)** data. | $\tau > 0$, Individualized Data. |
| **S3 (Fairness)** | Fairness-oriented allocation (Proportional). | Fairness Weight $> 0$, Proportional Allocation. |
| **S4 (Combined)** | Combined Carbon Tax + Fairness mechanisms. | $\tau > 0$, Fairness Weight $> 0$. |

---

## 🛠️ Installation & Usage

### Prerequisites
* Python 3.8+
* Required libraries: `numpy`, `pandas`, `matplotlib` (see `requirements.txt`)

### Setup
1.  Clone the repository:
    ```bash
    git clone [https://github.com/your-username/EcoFair-DSM.git](https://github.com/your-username/EcoFair-DSM.git)
    ```
2.  Install dependencies:
    ```bash
    pip install -r requirements.txt
    ```

### Running a Simulation
To execute the main simulation loop for all scenarios:

```bash
python main.py --steps 200 --scenarios all
