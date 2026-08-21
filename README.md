# Pairs Trading Optimization

A quantitative finance project that identifies optimal pairs trading opportunities across Russell 1000 stocks using a mean-variance optimization framework.

## Overview

Pairs trading is a market-neutral strategy that involves simultaneously going long on one asset and short on another correlated asset. This project automates the process of:

1. **Data Loading & Preprocessing** — Cleans and prepares historical stock price data (forward/back-fill missing values, drop incomplete columns).
2. **Profit/Loss Calculation** — Computes P&L for a long-short pair given an initial investment amount `k`.
3. **Pair Optimization** — Evaluates all pairwise combinations using a risk-adjusted objective function: `mean(P&L) - θ × std(P&L)`, where `θ` controls risk aversion.
4. **Results Filtering** — Identifies pairs with negative objective values (indicating high-risk or loss-making pairs to avoid).

## Dataset

- **Russell1000.csv** — Historical closing prices for ~1,000 Russell 1000 constituent stocks.

## Parameters

| Parameter | Default | Description |
|-----------|---------|-------------|
| `theta` | 100,000 | Risk aversion coefficient |
| `k` | 10,000 | Initial investment amount per leg |

## Getting Started

### Prerequisites

- Python 3.8+
- Jupyter Notebook

### Installation

```bash
pip install -r requirements.txt
```

### Usage

Open the notebook and run all cells:

```bash
jupyter notebook pair-trading.py.ipynb
```

## Project Structure

```
Pair Trading/
├── pair-trading.py.ipynb    # Main analysis notebook
├── Russell1000.csv          # Historical price data
├── pairs-trading.pdf        # Reference documentation
├── requirements.txt         # Python dependencies
├── .gitignore               # Git ignore rules
└── README.md                # This file
```

## Methodology

The optimization iterates over all unique asset pairs (C(n,2) combinations) and computes a risk-adjusted objective value for each. Pairs are ranked by their objective value to identify the most favorable long-short opportunities.
