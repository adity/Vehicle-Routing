

# Vehicle Routing Problem (VRP) Solver

A Python-based implementation of the **Vehicle Routing Problem (VRP)** using **Column Generation** and **Dynamic Programming**. This repository provides a set-partitioning formulation solver capable of handling standard VRPLIB instances, generating initial feasible routes via a Nearest Neighbor Heuristic, and visualizing the optimal vehicle paths.

## 🚀 Features
- **Column Generation Framework**: Efficiently solves the relaxed master problem and iteratively adds promising routes.
- **Dynamic Programming Pricing**: Solves the pricing subproblem to identify routes with negative reduced costs.
- **Multiple Solver Support**: Includes implementations for both **Gurobi** and **GAMS**.
- **VRPLIB Parser**: Natively reads standard VRPLIB format files (coordinates, demands, capacities, and dimensions).
- **Route Visualization**: Generates plots of the optimized routes using `networkx` and `matplotlib`.
- **Heuristic Initialization**: Uses a Nearest Neighbor strategy to generate an initial feasible solution for the master problem.

## 📦 Prerequisites & Installation

### Requirements
- Python 2.7 *(Note: The codebase uses Python 2 syntax such as `print` statements and `raw_input`)*
- Optimization Solvers:
  - [Gurobi](https://www.gurobi.com/) (required for `main.py` and `main_2.py`)
  - [GAMS](https://www.gams.com/) (optional, for `maingams.py`)
- Python Packages:
  - `numpy`
  - `matplotlib`
  - `networkx`
  - `gurobipy` (if using Gurobi)
  - `gams` (if using GAMS)

Install the required Python packages via pip:
```bash
pip install numpy matplotlib networkx gurobipy gams
```

## 💻 Usage

### 1. Running the Solver (Gurobi)
The primary entry point is `main_2.py`, which accepts a VRPLIB instance file as a command-line argument.

```bash
python main_2.py <path_to_vrplib_file.vrp>
```
*Example:*
```bash
python main_2.py P-n21-k2.vrp
```

### 2. Running with GAMS
If you prefer using GAMS for the optimization steps, run:
```bash
python maingams.py
```
*(Note: The input file path may need to be updated inside `maingams.py`)*

### 3. Output
Upon completion, the solver will:
- Print the optimal objective value and selected routes to the console.
- Generate a `path.png` file visualizing the vehicle routes.
- Optionally output the final LP/MIP model in `VRP.lp`.

## 📁 Project Structure
| File | Description |
|------|-------------|
| `main_2.py` | Main script for VRP solving using **Gurobi** and command-line input. |
| `main.py` | Alternative main script using Gurobi with a hardcoded instance path. |
| `maingams.py` | Main script for VRP solving using the **GAMS** API. |
| `NNH.py` | Nearest Neighbor Heuristic to generate initial feasible routes. |
| `readvrplib.py` | Parser for standard VRPLIB format instance files. |
| `plotsolution.py` | Visualization module using `networkx` and `matplotlib`. |

## ⚠️ Notes & Limitations
- The code is designed for research/academic purposes and relies on Python 2.7 syntax. For Python 3 compatibility, minor adjustments (e.g., adding parentheses to `print`, replacing `file.next()` with `next(file)`, and replacing `raw_input` with `input`) are required.
- The dynamic programming pricing subproblem includes a loop-breaking heuristic that may occasionally ignore symmetric solutions.
- Ensure your VRPLIB files contain standard sections: `NAME`, `CAPACITY`, `DIMENSION`, `DEMAND_SECTION`, and `NODE_COORD_SECTION`.

## 📜 License
This project is provided as-is for educational and research purposes.
