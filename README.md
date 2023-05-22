# Battery Operations Optimization with CVaR (Conditional Value at Risk)

This code provides a method to optimize battery operations with the consideration of risk averseness using Conditional Value at Risk (CVaR). The goal is to maximize profit while accounting for uncertain electricity prices in Texas.

## Prerequisites

To run this code, make sure you have the following dependencies installed:

- [Julia](https://julialang.org/) programming language
- [JuMP](https://github.com/jump-dev/JuMP.jl) package for mathematical optimization modeling
- [Gurobi](https://www.gurobi.com/) solver for solving the optimization problem
- [DataFrames](https://dataframes.juliadata.org/) package for handling tabular data

## Usage

1. Ensure that the necessary dependencies are installed.

2. Copy and paste the code into a Julia script or interactive environment.

3. Adjust the input parameters according to your specific problem:

   - `prices`: A matrix representing electricity prices over a time period. Each row corresponds to a scenario, and each column represents an hour. The matrix should have dimensions (num_scenarios, T).
   - `battery_capacity`: The maximum capacity of the battery in kilowatt-hours (kWh).
   - `max_power`: The maximum charging or discharging power of the battery in kilowatts (kW).
   - `charging_efficiency`: The efficiency of the battery when charging (a value between 0 and 1).
   - `discharging_efficiency`: The efficiency of the battery when discharging (a value between 0 and 1).
   - `α`: The confidence level (a value between 0 and 1) for calculating CVaR.
   - `β`: A weighting factor for the risk term in the objective function.

4. Call the function `optimize_battery_operations_cvar_ver3(prices, battery_capacity, max_power, charging_efficiency, discharging_efficiency, α, β)` to perform the optimization.

5. The function returns three outputs:

   - `results`: A DataFrame containing the results of the optimization, including scenario number, hour, price, state of charge (SOC), charge, and discharge values.
   - `objective_values`: A DataFrame containing the objective function values (profits) for each scenario.
   - `ζ_value`: The calculated value of ζ, which represents the CVaR.

6. Utilize the obtained results for further analysis or decision-making.

## Approach

The code formulates the battery operations as a mathematical optimization problem using JuMP and Gurobi. The objective function aims to maximize profit, considering the electricity prices and the CVaR risk measure. The decision variables include the state of charge (SOC), charge, discharge, ζ (CVaR auxiliary variable), and a binary variable (u) for controlling the battery power.

The code also incorporates various constraints, such as the initial SOC, SOC dynamics, power limits, and CVaR calculations.

## Note

Please ensure that you have a valid license for the Gurobi solver. If you don't have a Gurobi license, you can modify the code to use a different solver supported by JuMP.

For additional customization or modifications, refer to the documentation of the used packages.

## Acknowledgments

The code was developed to introduce risk averseness to battery operations in the context of Texas electricity prices. The underlying optimization approach and implementation were provided by [OpenAI](https://openai.com/) and the [Gurobi](https://www.gurobi.com/) team.
