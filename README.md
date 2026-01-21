# Snow Removal Route Optimization

Optimization model for municipal snow removal routing in Chomedey, Laval using Python and Gurobi (Mixed-Integer Programming).

## Project Overview
This project formulates and solves a mathematical optimization model to improve snow-clearing routes with the objective of minimizing total traffic delay penalties while respecting operational constraints.

The model captures real-world trade-offs faced by municipalities when prioritizing streets under different snowfall conditions.

## Methodology
- Formulated a Mixed-Integer Programming (MIP) model using **Python and Gurobi**
- Modelled street-level decision variables and sequencing constraints
- Built two scenarios:
  - Baseline snowfall
  - Heavy snowfall
- Derived cleaning times using distance–speed relationships
- Constructed penalty functions based on:
  - Traffic volume  
  - Peak vs off-peak periods  
  - Value-of-time economics  
- Performed sensitivity analyses on:
  - Snowfall severity  
  - Vehicle speed  
  - Priority streets (e.g., emergency routes)

## Tools Used
- Python  
- Gurobi Optimizer (`gurobipy`)  
- Jupyter Notebook  
- NumPy / Pandas 

## How to Run
This project requires Gurobi and an academic license.

1. Install dependencies:
```bash
pip install gurobipy pandas numpy matplotlib
```
2. Open the notebook:
   jupyter notebook

3. Run snow_removal_optimization.ipynb

## Results

The optimization model was solved using Gurobi across multiple scenarios, and optimal solutions were obtained in all cases.

### Scenario 1: Baseline (Normal Snowfall – 10 cm)
- The baseline scenario was constructed such that no lateness occurs relative to the theoretical schedule.
- As expected, the total penalty cost is **$0**, serving as a benchmark.
- Optimal route:
  Montgolfier → Saint-Martin → Notre-Dame → Curé-Labelle

This provides a consistent reference schedule for evaluating disruption under heavier snowfall.

---

### Scenario 2: Snowstorm (30 cm)
When snowfall intensity increased, reduced vehicle speed led to systematic lateness relative to the baseline schedule.

Key observations:
- Total penalty increased substantially compared to baseline.
- Peak periods produced higher penalties than off-peak periods due to higher value-of-time.
- The model selected a **different optimal route**:
  Notre-Dame → Saint-Martin → Curé-Labelle → Montgolfier

This indicates that worsening operational conditions lead not only to higher costs, but also to **structural changes in optimal routing decisions**.

---

### Sensitivity Analysis 1: Snowfall Severity (Speed Variation)
Two additional snowstorm conditions were tested:
- 20 cm snowfall (20 km/h)
- 40 cm snowfall (10 km/h)

Findings:
- Total penalty increases as speed decreases (slower operations → more lateness).
- However, the **optimal route remained unchanged** compared to the 30 cm scenario.

This suggests that the model’s routing solution is **robust to moderate parameter variation**, even though costs are highly sensitive.

---

### Sensitivity Analysis 2: Priority Street (Critical Infrastructure)
A policy-based scenario was introduced where Curé-Labelle was assigned higher importance (e.g., presence of a school and fire station), modeled via a higher penalty multiplier.

Findings:
- The optimal route changed to:
  Curé-Labelle → Notre-Dame → Saint-Martin → Montgolfier
- This demonstrates that the model can incorporate **policy priorities**, not just operational efficiency.

---

### Key Insights
- Snowfall severity strongly affects total system cost.
- Routing decisions are **more sensitive to priority weighting** than to moderate speed changes.
- The model provides a flexible framework for municipalities to test:
  - Emergency prioritization strategies  
  - Trade-offs between fairness and efficiency  
  - Peak vs off-peak operational policies
