# Beta of a single index model of a portfolio in Python

import pandas as pd
import numpy as np
import pandas_datareader as web
from scipy import stats

# Define the tickers and weights of the portfolio
tickers = ['TICKER1', 'TICKER2', 'TICKER3']  # Replace with actual tickers
weights = np.array([0.4, 0.3, 0.3])  # Replace with actual weights
# Download historical price data
price_data = web.get_data_yahoo(tickers, start='start_date', end='end_date')['Adj Close']
# Calculate daily returns
ret_data = price_data.pct_change().dropna()
# Calculate portfolio returns
port_ret = (ret_data * weights).sum(axis=1)
# Download benchmark data (e.g., S&P 500)
benchmark_data = web.get_data_yahoo('SPY', start='start_date', end='end_date')['Adj Close']
benchmark_ret = benchmark_data.pct_change().dropna()
# Perform linear regression to calculate beta
(beta, alpha) = stats.linregress(benchmark_ret.values, port_ret.values)[0:2]
print(f"The portfolio beta is: {beta:.4f}")
print(f"The portfolio alpha is: {alpha:.5f}")
