# Pairs Trading Strategy

This project demonstrates a **Pairs Trading** strategy, a market-neutral trading approach that leverages cointegration between two financial instruments. The strategy profits from relative price movements between two cointegrated securities, rather than their absolute price movements.

## Overview

Pairs trading involves identifying pairs of securities with a statistical relationship, often through cointegration. The strategy works as follows:

1. **Cointegration Testing**: Identify pairs whose price movements are cointegrated.
2. **Trading Strategy**:
   - Go "long" on the underperforming security and "short" on the outperforming one when the spread widens beyond a threshold.
   - Exit positions when the spread reverts to its mean.
3. **Market Neutrality**: The strategy is immune to overall market movement.

## Key Concepts

- **Cointegration**: A statistical relationship between two time series where their spread oscillates around a constant mean.
- **Z-Score**: A normalized metric to identify extreme deviations in the spread.

## Methodology

1. **Data Simulation**: Artificially generate cointegrated time series for testing.
2. **Testing for Cointegration**: Using statistical tests to ensure pairs are cointegrated.
3. **Z-Score Analysis**: Compute a z-score for the price ratio to signal trade opportunities.
4. **Backtesting**:
   - Simulate the strategy over historical data.
   - Calculate profitability metrics.

## Requirements

Install the required Python libraries:

```bash
!pip install statsmodels --user
!pip install pandas==0.24.2 --user
!pip install matplotlib --user
!pip install auquan_toolbox --user
```

### How It Works

1. **Simulated Data**: Create two synthetic securities, one with price movements derived from the other plus noise.
2. **Cointegration Testing**:
   - Use the `statsmodels.tsa.stattools.coint` test to identify pairs.
3. **Signal Generation**:
   Compute a rolling z-score of the price ratio.
   Enter positions based on z-score thresholds.
4. **Backtesting**:
   Evaluate performance using a simple profit-and-loss (PnL) calculation
5. **Optimization**:
   - Tune parameters like rolling window lengths for better performance.
   - Avoid overfitting through validation on unseen data.

## Results
   The strategy demonstrates profitability in simulated and historical test data. Further optimization and validation are possible through parameter tuning and advanced machine learning models.

## Example Code
Below is an example snippet to install dependencies and start working with cointegration testing:
```bash
!pip install statsmodels --user  
!pip install pandas==0.24.2 --user

import numpy as np
import pandas as pd
from statsmodels.tsa.stattools import coint

np.random.seed(107)
# Simulate price data for testing
```

## Notes
1. Avoid Multiple Comparison Bias: Only test pairs with strong theoretical backing to reduce false positives.
2. Beware of Overfitting: Over-optimization can lead to poor performance on unseen data.