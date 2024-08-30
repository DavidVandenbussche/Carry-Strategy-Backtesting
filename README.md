# Carry Strategy Implementation and Backtesting

This repository contains an implementation and backtesting of a financial trading strategy known as the "Carry Strategy". The strategy is applied to futures contracts, leveraging the concept of "carry," which reflects the cost or benefit of holding a financial instrument until a later date.

## Overview

The carry strategy aims to exploit differences between the futures price of an asset and its expected future spot price. This strategy is based on the assumption that the difference, or "carry," can provide insights into future price movements, allowing for profitable trades.

### Key Features

- **Data Handling**: The code reads and processes historical data for futures contracts, including prices and hedging pressure variables.
- **Carry Calculation**: The strategy calculates the carry by comparing the near-term and far-term futures contract prices.
- **Backtesting**: The strategy is backtested using historical data to evaluate its performance over time.
- **Visualization**: Key results and performance metrics are plotted to provide visual insights into the strategy's effectiveness.

## Project Structure

- `Data/`: Directory where the input data files (`S_price.csv` and `S_hp.csv`) are stored.
- `code.ipynb`: The main Jupyter Notebook containing the implementation of the carry strategy, including data processing, strategy computation, and backtesting.

## Getting Started

### Prerequisites

To run this project, you need the following Python packages:

- `pandas`
- `numpy`
- `matplotlib`

You can install the required packages using pip:

```bash
pip install pandas numpy matplotlib
```

## Running the Notebook

### Clone this repository:

``bash
git clone https://github.com/yourusername/carry-strategy.git
cd carry-strategy
``

Place your data files (`S_price.csv` and `S_hp.csv`) in the `Data/` directory.

### Open and run the `code.ipynb` notebook using Jupyter:

``bash
jupyter notebook code.ipynb
``

## Understanding the Code

### 1. Data Manipulation

The notebook begins by importing the required libraries and loading the data. It processes the closing prices of two futures contracts and calculates the carry as follows:

``python
s['carry'] = (s['Close1'] - s['Close2']) / s['Close1']
``

### 2. Hedging Pressure

The code integrates hedging pressure data, which can be used as a factor in the strategy. Missing values are handled by forward-filling:

``python
for i in range(1, s.shape[0]):
    if np.isnan(s.iloc[i, 3]):
        s.iloc[i, 3] = s.iloc[i-1, 3]
``

### 3. Strategy Backtesting

The carry strategy is backtested by applying the computed carry values over the historical data, providing insights into its performance.

## Contributing

Contributions are welcome! Please feel free to submit a pull request or open an issue if you have suggestions or encounter any issues.

## References

This project on the carry strategy was informed by several key papers and articles:

1. [Carry](https://research.cbs.dk/en/publications/carry-2) - A research publication on the concept and implementation of the carry strategy.
2. [Currency Carry Trades](https://www.jstor.org/stable/2962144) - An article that explores the mechanics and implications of currency carry trades.
3. [The Cross-Section of Foreign Currency Risk Premia and Consumption Growth Risk](https://www.jstor.org/stable/222458) - A detailed analysis of foreign currency risk premia in the context of consumption growth risk.

