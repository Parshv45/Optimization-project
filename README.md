# Delivery Optimization Project

## Project Overview
This project implements a sophisticated **Multi-Courier Delivery Optimization** solution. It uses a **Ruin & Recreate (R&R)** metaheuristic to solve the Vehicle Routing Problem with Pickups and Deliveries (VRPPD). The algorithm efficiently assigns deliveries to multiple couriers and optimizes their visit sequences to minimize the total delivery time while respecting constraints such as courier capacity, time windows, and maximum route duration.

## Algorithm: Ruin & Recreate (R&R)
The optimization engine is based on the **Ruin & Recreate** metaheuristic, an iterative approach that explores the solution space by:
- **Ruin Phase**: Removing a subset of deliveries from the current solution using strategies like **Radial Ruin** (removing nearby deliveries) or **Random Ruin**.
- **Recreate Phase**: Reinserting the removed deliveries into the best possible positions across all courier routes using a **Greedy Best-Insertion** heuristic.
- **Acceptance Criterion**: Utilizing a **Threshold Accepting** mechanism (similar to Simulated Annealing) to allow temporary acceptance of worse solutions, helping the algorithm escape local optima and converge toward a global minimum.

## Project Structure
The project is designed to handle multiple scenarios across 12 distinct instances. Each instance folder contains its specific input data, results, and visualizations.

```
.
├── algorithm.py              # Main Python script implementing the R&R solver
├── instance_1/               # Data and results for Instance 1
│   ├── couriers.csv          # Courier capacity and starting locations
│   ├── deliveries.csv        # Delivery requirements (pickup/dropoff locations, time windows)
│   ├── traveltimes.csv       # Travel time matrix between all locations
│   ├── result.csv            # Final optimized assignments and sequences
│   └── graphs/               # Visualizations specific to Instance 1
│       ├── route_map.png     # Geographic visualization of routes
│       └── ...
├── instance_2/               # Data and results for Instance 2
│   └── ...
├── ...
├── instance_12/              # Data and results for Instance 12
│   └── ...
├── Untitled.ipynb            # Interactive Jupyter Notebook for development and testing
└── README.md                 # Project documentation (this file)
```

### File Descriptions:
- **`algorithm.py`**: The standalone script that processes an instance folder, runs the R&R optimization, and saves the output to `result.csv` and the `graphs/` directory.
- **`instance_X/`**: Dedicated folders for each of the 12 test cases.
  - **`couriers.csv`**: Defines courier IDs, their starting locations, and load capacities.
  - **`deliveries.csv`**: Details each delivery's ID, capacity requirement, pickup location, dropoff location, and time window start.
  - **`traveltimes.csv`**: A symmetric matrix providing travel times between all location IDs.
  - **`result.csv`**: The output file containing the optimized sequence of stops for each courier.
- **`Untitled.ipynb`**: A comprehensive notebook that mirrors the algorithm's logic, used for detailed analysis and generating the final optimization results.

## Key Features
- **Flexible Constraint Handling**: Supports courier capacity limits, time window constraints for pickups, and maximum route duration.
- **Advanced Optimization**: Employs both Radial and Random ruin operators to balance local search and global exploration.
- **Multi-Instance Support**: Easily scales to process multiple delivery scenarios independently.
- **Detailed Reporting**: Provides a summary of total delivery time (T_min), feasibility checks, and improvement statistics after optimization.

## Usage
To run the optimization for a specific instance:
1. Ensure all input CSVs are present in the target instance folder (e.g., `instance_1/`).
2. Run the solver (either via the notebook or the `algorithm.py` script).
3. Review the `result.csv` for the optimized courier routes and check the `graphs/` folder for visual analysis.

## Author
Rounak Sambhwani and Parshv Shah
