# Optimal Execution Model with Stochastic Control

A Python implementation of stochastic control for optimal execution models, incorporating real financial data from `yfinance`. This project calculates the optimal trade execution path for any given equity, taking into account market impact, liquidity, and stochastic price movements.

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Theory and Background](#theory-and-background)
- [Installation](#installation)
- [Usage](#usage)
- [Example](#example)
- [Project Structure](#project-structure)
- [Dependencies](#dependencies)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgments](#acknowledgments)

## Introduction

This project implements an optimal execution strategy for trading large orders in financial markets. It uses stochastic control techniques, specifically within the Almgren-Chriss framework, to minimize the expected cost and risk associated with executing a large order over a finite time horizon.

The model accounts for:

- **Market Impact Costs**: Temporary and permanent impacts due to trading.
- **Timing Risk**: The risk of adverse price movements while executing the order.
- **Liquidity Profiles**: Adjusting trading strategies based on intraday volume patterns.
- **Real Market Data**: Incorporating historical and real-time data fetched via `yfinance`.

## Features

- Fetch historical and intraday market data for any equity using `yfinance`.
- Estimate model parameters dynamically based on fetched data.
- Calculate optimal trading trajectories using stochastic control.
- Simulate price paths and execution costs with enhanced market impact modeling.
- Adjust trading strategies based on intraday liquidity profiles.
- Modular codebase for easy extension and maintenance.
- Visualization of execution costs and trading trajectories.
- Placeholder for integration with broker APIs for real-market execution.

## Theory and Background

The project is based on the **Almgren-Chriss model** for optimal execution, which balances the trade-off between market impact costs and timing risk. The model formulates a stochastic control problem, aiming to minimize the expected execution cost plus a risk penalty.

Key components include:

- **Optimal Trading Trajectory**: Determined by solving the Hamilton-Jacobi-Bellman (HJB) equation.
- **Market Impact Modeling**: Incorporates both temporary and permanent impacts, potentially using nonlinear functions.
- **Stochastic Price Dynamics**: Asset prices modeled as stochastic processes (e.g., geometric Brownian motion).
- **Liquidity and Volume Profiling**: Adjusting strategies based on historical intraday volume patterns.

For detailed mathematical formulations and derivations, please refer to the Almgren-Chriss framework.

## Installation

1. **Clone the repository** from GitHub.

2. **Create a virtual environment** (optional but recommended).

3. **Install the required packages** using `pip` and the `requirements.txt` file.

   - Note: If `requirements.txt` is not available, manually install dependencies.

## Usage

Run the main script `optimal_execution.py`.

The program will prompt you for input:

- **Ticker Symbol**: The stock symbol (e.g., `AAPL`).
- **Start Date**: The start date for fetching historical data (format `YYYY-MM-DD`).
- **End Date**: The end date for fetching historical data (press Enter for today's date).
- **Total Shares to Trade**: The total number of shares you wish to buy or sell.
- **Trading Horizon**: The time horizon over which you want to execute the order (in days).
- **Number of Time Steps**: The number of intervals within the trading horizon (e.g., `390` for minute-by-minute trading).
- **Risk Aversion Parameter**: A parameter that balances cost vs. risk (e.g., `1e-6`).
- **Temporary Impact Coefficient (\( \eta \))**: Press Enter to estimate or provide a value.
- **Market Impact Exponent (\( \gamma \))**: Press Enter for linear impact or provide a value (e.g., `0.5`).
- **Number of Simulation Paths**: The number of simulations to run (e.g., `1000`).

After entering the required information, the program will:

- Fetch market data and estimate model parameters.
- Calculate the optimal trading trajectory.
- Simulate price paths and calculate execution costs.
- Display the average execution cost and its standard deviation.
- Plot the distribution of execution costs and the optimal trading trajectory.

## Example

Here's an example interaction:

- **Enter the ticker symbol**: `AAPL`
- **Enter the start date for historical data**: `2020-01-01`
- **Enter the end date for historical data**: *(press Enter)*
- **Enter the total shares to trade**: `500000`
- **Enter the trading horizon in days**: `1.0`
- **Enter the number of time steps**: `390`
- **Enter the risk aversion parameter**: `1e-6`
- **Enter the temporary impact coefficient eta**: *(press Enter)*
- **Enter the market impact exponent gamma**: `0.7`
- **Enter the number of simulation paths**: `1000`

After processing, the program will output results and display plots.

## Project Structure

- **`optimal_execution.py`**: Main script to run the program.
- **`market_data.py`**: Module for data fetching and processing.
- **`parameter_estimator.py`**: Module for parameter estimation.
- **`optimal_execution_model.py`**: Module for calculating optimal trajectories.
- **`simulation_engine.py`**: Module for simulations.
- **`execution_engine.py`**: Placeholder module for real-market execution.
- **`requirements.txt`**: List of dependencies.
- **`README.md`**: Project documentation.

## Dependencies

- Python 3.7 or higher
- numpy
- pandas
- yfinance
- matplotlib
- scipy

Install dependencies using the `requirements.txt` file.

## Contributing

Contributions are welcome! Please follow these steps:

1. **Fork the repository**.

2. **Create a new branch** for your feature or bug fix.

3. **Commit your changes**.

4. **Push to the branch**.

5. **Create a new Pull Request**.

Please ensure that your code follows best practices and includes appropriate tests.

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

## Acknowledgments

- **Almgren, R., & Chriss, N. (2000)**. *Optimal execution of portfolio transactions*. Journal of Risk, 3(2), 5-39.
- The open-source community and contributors to the libraries used in this project.

---

