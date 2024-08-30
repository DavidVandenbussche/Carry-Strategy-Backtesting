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

## References

This project on the carry strategy was informed by several key papers and articles:

## References

This project on the carry strategy was informed by several key papers and articles:

1. [Carry](https://research.cbs.dk/en/publications/carry-2) by Ralph S.J. Koijen, Tobias J. Moskowitz, Lasse Heje Pedersen, and Evert B. Vrugt. This paper extends the concept of carry, which has traditionally been studied in currency markets, to a wide range of asset classes including global equities, global bonds, commodities, US Treasuries, credit, and options. It decomposes a security’s expected return into its "carry" (an ex-ante, model-free characteristic) and expected price appreciation. The study finds that carry predicts returns both cross-sectionally and over time across various asset classes. The paper also challenges existing financial theories like Uncovered Interest Parity and the Expectations Hypothesis, suggesting that carry strategies are often exposed to risks related to global recession, liquidity, and volatility, though these risks do not fully explain the carry premium.

2. [Systematic Risk, Hedging Pressure, and Risk Premiums in Futures Markets](https://www.jstor.org/stable/2962144) by Hendrik Bessembinder, Arizona State University. This paper examines the uniformity of risk pricing in futures and asset markets. It finds that the "zero-beta" rate for futures is close to zero and that systematic risk premiums do not differ significantly across assets and futures. The study also presents evidence consistent with a model by Hirshleifer (1988), showing that returns in foreign currency and agricultural futures vary with the net holdings of hedgers, after controlling for systematic risk. These findings suggest a degree of market segmentation and support the idea that hedging pressure influences futures premiums.

3. [Hedging Pressure Effects in Futures Markets](https://www.jstor.org/stable/222458) by Frans A. de Roon, Theo E. Nijman, and Chris Veld. This paper presents a model suggesting that futures risk premia depend on both own-market and cross-market hedging pressures. Empirical evidence from 20 futures markets, divided into financial, agricultural, mineral, and currency groups, indicates that both own and cross-hedging pressures significantly affect futures returns, even after controlling for systematic risk. The study demonstrates that hedging pressure also provides explanatory power for returns on the underlying assets, supporting the model’s predictions.
