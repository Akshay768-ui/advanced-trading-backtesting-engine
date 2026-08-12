# 🚀 Advanced Trading Strategy Backtesting Engine

A modular, extensible **Python-based quantitative trading backtesting framework** designed to research, simulate, and evaluate systematic rule-based trading strategies across **Forex and cryptocurrency markets**.

The engine separates **market data processing, strategy logic, portfolio/risk management, execution simulation, performance analytics, and visualization**, making it easy to develop and test new strategies without rewriting the core backtesting infrastructure.

> **Research-oriented project:** Backtest results are historical simulations and do not represent guaranteed future performance. Results may not fully account for live-market effects such as slippage, spread, liquidity, and transaction costs.

---

## 📌 Project Overview

The objective of this project is to provide a reusable framework for answering a fundamental quantitative trading question:

> **"Would this trading strategy have generated attractive risk-adjusted returns under historical market conditions?"**

Instead of manually testing individual strategies, the engine allows strategy rules to be defined programmatically and evaluated consistently across different assets and datasets.

### Core workflow

```text
Historical Market Data
        │
        ▼
Data Preprocessing
        │
        ▼
Strategy Signal Generation
        │
        ▼
Entry / Exit Logic
        │
        ▼
Position Sizing & Risk Management
        │
        ▼
Trade Execution Simulation
        │
        ▼
Portfolio / Equity Tracking
        │
        ▼
Performance Analytics
        │
        ▼
Reports & Visualizations
```

---

## ✨ Key Features

### 📊 Multi-Asset Backtesting

The framework can evaluate strategies across multiple instruments, including:

* BTCUSDT
* ETHUSDT
* SOLUSDT
* EURUSD

The architecture is designed so additional symbols and datasets can be incorporated without changing the core engine.

### 📈 Strategy Framework

Currently includes an **EMA 9/20 pullback strategy** incorporating:

* Fast/slow EMA trend alignment
* Pullback-based entries
* Confirmation-candle logic
* Trend-strength filtering
* Configurable entry and exit conditions
* Dynamic trade management

The strategy layer is separated from the backtesting engine, allowing additional strategies to be implemented independently.

### 🛡️ Risk Management

The engine supports configurable:

* Stop-loss
* Take-profit
* Position sizing
* Risk-per-trade
* Risk-reward parameters
* Trade management rules

This allows strategies to be evaluated not only on absolute returns but also on **risk exposure and drawdown characteristics**.

### 📐 Performance Analytics

The framework calculates key quantitative performance metrics:

| Metric           | Purpose                             |
| ---------------- | ----------------------------------- |
| Win Rate         | Percentage of profitable trades     |
| Profit Factor    | Gross profit relative to gross loss |
| Sharpe Ratio     | Risk-adjusted return measure        |
| Maximum Drawdown | Largest peak-to-trough decline      |
| Total Return     | Overall portfolio growth            |
| Average Trade    | Average P&L per trade               |
| Equity Curve     | Evolution of portfolio value        |

---

# 🧠 Strategy Implementation

The current implementation uses an **EMA 9/20 pullback methodology**.

### 1. Trend Identification

Two exponential moving averages are calculated:

```text
EMA Fast = 9 periods
EMA Slow = 20 periods
```

A bullish environment is identified when the fast EMA remains above the slow EMA, while the opposite relationship indicates bearish momentum.

### 2. Pullback Detection

Instead of entering immediately after a crossover, the strategy waits for price to retrace toward the EMA structure.

This attempts to avoid chasing extended moves and provides a more structured entry condition.

### 3. Confirmation

A confirmation candle is used to validate the potential continuation of the prevailing trend.

Conceptually:

```text
Trend
  │
  ▼
EMA Alignment
  │
  ▼
Price Pullback
  │
  ▼
Confirmation
  │
  ▼
Trade Entry
```

### 4. Trade Management

After entry, the engine manages the position according to predefined:

* Stop-loss
* Take-profit
* Position sizing
* Risk-reward parameters

This ensures that historical simulations follow the same predefined rules rather than discretionary decisions.

---

# 📊 Sample Backtest Results

The following results were generated from the current strategy implementation and are provided as **research examples**, not as claims of future profitability.

| Symbol  | Win Rate | Profit Factor | Sharpe Ratio | Return |
| :------ | -------: | ------------: | -----------: | -----: |
| BTCUSDT |    62.8% |          3.63 |         3.09 |   616% |
| ETHUSDT |    60.7% |          3.51 |         1.42 |   657% |
| SOLUSDT |    62.0% |          3.59 |         1.55 |   678% |

### Interpretation

The results demonstrate how the framework can compare strategy behavior across different assets.

For example:

* **BTCUSDT** achieved a 62.8% win rate with a 3.63 profit factor.
* **ETHUSDT** produced a 60.7% win rate and 3.51 profit factor.
* **SOLUSDT** produced a 62.0% win rate and 3.59 profit factor.

However, **high historical returns alone should not be interpreted as evidence of a robust trading strategy**. A proper evaluation should also consider out-of-sample performance, transaction costs, slippage, market regime changes, and parameter sensitivity.

---

# 📉 Risk & Performance Analysis

The engine is designed to evaluate strategies from multiple perspectives rather than relying solely on total return.

### Profitability

* Total return
* Net profit
* Profit factor
* Average trade
* Win rate

### Risk

* Maximum drawdown
* Risk per trade
* Risk-reward ratio
* Losing streaks

### Risk-Adjusted Performance

* Sharpe ratio
* Equity curve behavior
* Return relative to drawdown

This allows strategies to be compared based on **risk-adjusted performance rather than raw profitability**.

---

# 🖼️ Visualizations

The project generates visual outputs for analyzing backtest behavior, including:

* Equity curves
* Performance summary tables
* Trade-level analysis
* Strategy statistics
* Asset-level comparisons

These visualizations make it easier to identify:

* Drawdown periods
* Performance consistency
* Changes in strategy behavior
* Differences between assets

---

# 🏗️ Project Architecture

```text
advanced-trading-backtesting-engine/
│
├── strategy.py
│   └── Strategy definitions and trading signals
│
├── backtest_engine.py
│   └── Core backtesting and trade simulation engine
│
├── data.py
│   └── Market data loading and preprocessing
│
├── visualization.py
│   └── Equity curves, charts, and performance reports
│
├── main.py
│   └── Main execution entry point
│
├── *.csv
│   └── Trade logs and processed results
│
├── *.png
│   └── Generated visualizations
│
└── requirements.txt
    └── Python dependencies
```

---

# ⚙️ Technology Stack

### Programming

* **Python**

### Data & Numerical Computing

* **Pandas** — Data manipulation and time-series processing
* **NumPy** — Numerical computation and vectorized operations

### Visualization

* **Matplotlib** — Equity curves, performance charts, and analytical reports

### Methodology

* Quantitative trading research
* Historical backtesting
* Technical indicator analysis
* Risk management
* Statistical performance evaluation

---

# 🚀 Running the Project

### 1. Clone the repository

```bash
git clone https://github.com/Akshay768-ui/advanced-trading-backtesting-engine.git
cd advanced-trading-backtesting-engine
```

### 2. Create a virtual environment

```bash
python -m venv .venv
```

### 3. Activate the environment

**macOS / Linux**

```bash
source .venv/bin/activate
```

**Windows**

```bash
.venv\Scripts\activate
```

### 4. Install dependencies

```bash
pip install -r requirements.txt
```

### 5. Run the backtester

```bash
python main.py
```

Generated trade logs, performance statistics, and visualizations can then be inspected from the project output files.

---

# 🔬 Quantitative Research Considerations

A backtest can produce misleading results if historical simulations do not accurately represent live trading conditions.

Future evaluations should therefore consider:

### Transaction Costs

Include:

* Brokerage
* Exchange fees
* Commissions
* Bid-ask spread

### Slippage

Model the difference between theoretical execution price and actual execution price.

### Overfitting

Avoid optimizing parameters exclusively for historical data.

For example:

```text
Historical Data
      │
      ├── Training / Development
      │
      ▼
Parameter Selection
      │
      ▼
Out-of-Sample Testing
      │
      ▼
Robustness Evaluation
```

### Market Regimes

Strategy performance should be evaluated across:

* Trending markets
* Range-bound markets
* High-volatility periods
* Low-volatility periods

---

# 🛠️ Future Enhancements

Planned improvements include:

* [ ] Parameter optimization using Grid Search
* [ ] Bayesian optimization
* [ ] Walk-forward analysis
* [ ] Out-of-sample testing
* [ ] Transaction-cost modeling
* [ ] Spread and slippage simulation
* [ ] Monte Carlo trade-sequence analysis
* [ ] Portfolio-level backtesting
* [ ] Multi-strategy comparison
* [ ] Additional technical strategies
* [ ] Machine-learning-based signal generation
* [ ] Live market-data integration
* [ ] API-based paper/live execution

---

# 🎯 Research Objective

The long-term objective is to evolve the project from a simple strategy tester into a **research-oriented quantitative trading framework** capable of:

1. Developing systematic trading hypotheses
2. Testing them against historical data
3. Measuring statistical and risk-adjusted performance
4. Performing robustness and sensitivity analysis
5. Comparing strategies across assets and market regimes
6. Providing a structured foundation for further quantitative research

---

# ⚠️ Disclaimer

This project is intended for **educational and quantitative research purposes only**.

Backtested performance does not guarantee future results. Historical simulations may differ significantly from live trading because of market liquidity, spreads, slippage, transaction costs, latency, data quality, and changing market regimes.

The reported sample results should therefore **not be interpreted as investment advice or a guarantee of profitability**.

---

# 👨‍💻 Author

**Akshay Rao J**

B.Tech — Computer Science and Engineering
National Institute of Technology Puducherry
CGPA: **8.51/10**

**Focus:** Quantitative Trading · Financial Markets · Algorithmic Trading · Python · Statistical Analysis

[GitHub](https://github.com/Akshay768-ui)
