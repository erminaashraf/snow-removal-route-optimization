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
- NumPy / Pandas (if used)

## How to Run
This project requires Gurobi and an academic license.

1. Install dependencies:
```bash
pip install gurobipy pandas numpy matplotlib

