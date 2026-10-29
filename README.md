# hk-stocks-pairs-trading

# HK Stocks Statistical Arbitrage & Pairs Trading Framework

A comprehensive Python-based quantitative research and backtesting framework designed for **statistical arbitrage** and **pairs trading** strategies using Hong Kong (HK) equity data. 

This project identifies price-correlated stock pairs within the same sector, establishes mean-reversion entry and exit thresholds using historical research data, and evaluates portfolio-level performance (including transaction costs and short interest).

---

## 🚀 Key Features

* **Sector & Liquidity Filtering:** Filters liquid HK equity names based on turnover and market capitalization, mapping stocks to their respective industries and sectors.
* **Correlation Analysis:** Supports both **Pearson** and **Spearman** correlation metrics to identify co-movement and robust mean-reversion candidates.
* **Automated Pair Identification:** Dynamically screens for high-correlation stock pairs above a custom user-defined threshold.
* **Backtesting Engine:** 
  * Calculates trading parameters (Entry divergence bands and Exit/Convergence points) using a dedicated research period.
  * Simulates trades across a test dataset with configurable dollar allocations, stop-loss rules, transaction commission rates, and short-position interest calculations.
* **Interactive Visualization:** Integrates `matplotlib`, `plotly`, and `ipywidgets` for intuitive visual exploration of stock pairs, price ratios, and trading signals.

---

## 🛠️ Tech Stack & Dependencies

* **Language:** Python 3
* **Data Manipulation & Analysis:** `pandas`, `numpy`, `pandas_datareader`
* **Data Source:** `yfinance` (Yahoo Finance API)
* **Visualization:** `matplotlib`, `plotly`
* **UI & Interactivity:** `ipywidgets`, Google Colab Data Tables (`google.colab`)

---

## 📂 Notebook Workflow

1. **Environment Setup & Helper Functions:** Import libraries, configure Chinese character font support (optional), and load core helper functions for signal generation and PnL tracking.
2. **Stock Info & Liquidity Sourcing:** Pull stock metadata, industry classifications, and filter out low-liquidity names/penny stocks based on a minimum turnover threshold.
3. **Price Data Sourcing:** Fetch daily adjusted close prices (Open, High, Low, Close, Volume) from Yahoo Finance.
4. **Pair Selection & Correlation:** Compute correlation matrices, visualize distributions, and select highly correlated pairs within matching sectors.
5. **Research & Parameter Tuning:** Establish baseline price ratios, mean convergence levels, and upper/lower divergence bands using historical research data.
6. **Backtesting & PnL Evaluation:** Run the backtest simulation over out-of-sample test data, computing net PnL, transaction costs, and short-selling interest expenses.

---

## 🚀 Getting Started & Running in Google Colab

This notebook is optimized for execution inside **Google Colab** to leverage built-in interactive widgets and data table formatters.

1. Open the notebook in Google Colab.
2. Run the initial configuration block to install dependencies and import helper functions.
3. Use the interactive dropdown widgets to inspect specific stock pairs, adjust correlation thresholds, and evaluate portfolio backtest performance.

---

## 📈 Strategy Overview

1. **Find Correlated Pairs:** Identify HK stocks within the same sector exhibiting high statistical price correlation.
2. **Signal Generation (Divergence):** 
   * **Short Stock A / Long Stock B** when the price ratio diverges outside the upper threshold (Stock A is relatively over-priced).
   * **Long Stock A / Short Stock B** when the price ratio diverges outside the lower threshold (Stock A is relatively under-priced).
3. **Mean Reversion (Exit):** Close positions when the price ratio converges back to its historical historical mean.
