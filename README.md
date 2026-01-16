# EcoFair-DSM: Hybrid LCA-ABMS Simulation Framework

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Python](https://img.shields.io/badge/Made%20with-Python-blue.svg)](https://www.python.org/)

**EcoFair-DSM** is a hybrid simulation framework that integrates **Lifecycle Assessment (LCA)** with **Agent-Based Modeling (ABMS)**. It is designed to evaluate the trade-offs between economic efficiency, environmental impact, and supplier fairness in digital marketplaces.

This repository contains the source code used for the case study and policy evaluation presented in the paper:
> **"A Hybrid LCA-ABMS Framework for Fairness-Aware Supply Chains: Evaluating Digital Product Passports Beyond Static Averages"**

---

## 🚀 Key Features

* **Hybrid Modeling:** Combines static/individualized environmental data (LCA) with dynamic agent behavior (ABMS).
* **DPP Integration:** Simulates **Individualized (DPP)** environmental data to test policy effectiveness beyond industry averages.
* **Fairness Mechanisms:** Implements **Jain’s Fairness Index**, Rotation Fairness, and Disparity Fairness to control supplier allocation.
* **Policy Simulation:** Built-in scenarios for **Carbon Pricing**, **Fairness-Weighted Ranking**, and **Combined Policies**.
* **Reproducibility:** Scripts to automatically generate the exact plots and LaTeX tables used in the paper.

---

## 📂 Project Structure

The project files are organized as follows:

* **Core Logic:**
  * `simulation.py`: Defines Agents (Supplier, Buyer), Modules (Environment, Fairness, Policy, Marketplace), and the main Simulation loop.
  * `scenarios.py`: Configuration for the specific policy scenarios (S1–S4).
  * `metrics.py` & `extract_metrics.py`: Logic for calculating Gini coefficients, emissions, and extraction of simulation KPIs.

* **Execution Scripts:**
  * `run_experiments.py`: The main script that runs all scenarios sequentially and saves data to `results.json`.
  * `main.py`: Utility to run a single scenario for quick testing or debugging.
  * `plot_results.py`: Generates the analysis figures (PNG/PDF) from the results.
  * `make_table.py`: Generates the results tables in LaTeX format.

---

## 🧪 Simulation Scenarios

The framework includes configurations for the following policy scenarios (see `scenarios.py`):

| Scenario | Description | Key Settings |
| :--- | :--- | :--- |
| **S1** | Baseline (Cost-driven, Static LCA) | No Tax, Sequential Allocation. |
| **S2A** | Carbon Pricing (Static LCA) | $\tau > 0$, Static Data. |
| **S2B** | Carbon Pricing (Individualized LCA) | $\tau > 0$, Individualized (DPP) Data. |
| **S3** | Fairness-Oriented | Fairness Weight $> 0$, Proportional Allocation. |
| **S4A** | Combined Policy (Balanced) | Combined Tax + Fairness. |
| **S4B** | Combined Policy (Disparity Only) | Variation of S4 focused on long-term equity. |
| **S4C** | Combined Policy (Rotation Only) | Variation of S4 focused on short-term turn-taking. |

---

## 🛠️ Installation & Usage

### Prerequisites
* Python 3.8+
* Required library: `matplotlib` (and standard libraries `json`, `random`, `math`)

### Setup
1.  Clone the repository:
    ```bash
    git clone [https://github.com/ShaiFernandez/EcoFair-DSM.git](https://github.com/ShaiFernandez/EcoFair-DSM.git)
    cd EcoFair-DSM
    ```
2.  Install dependencies:
    ```bash
    pip install -r requirements.txt
    ```

### 🔁 Reproducing the Results

To reproduce the full set of results from the paper, run the scripts in the following order:

**1. Run the Simulations**
Execute all scenarios (S1-S4) for $T=200$ timesteps. This will create a `results.json` file.
```bash
python run_experiments.py
