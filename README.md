# CVaR Portfolio Optimization

An optimization course project on portfolio allocation under downside risk, with historical Conditional Value-at-Risk (CVaR) models, out-of-sample backtesting, and exploratory analysis of ten US stocks. A companion task implements an adaptive Adam optimizer for unconstrained optimization.

This is the portfolio edition maintained by [miracl-3](https://github.com/miracl-3). The project was developed collaboratively in [JarvisHunter/optimization_final_project](https://github.com/JarvisHunter/optimization_final_project). The original commit history and contributor attribution are preserved.

**Final report:** [Portfolio Optimization using Conditional Value-at-Risk](reports/Optimization_Final_Project_Report.pdf) (PDF, 23 pages).

![Out-of-sample cumulative portfolio wealth](figures/cumulative_wealth.png)

## Methods

The main notebook, [`task2.ipynb`](task2.ipynb), includes:

- Historical CVaR minimization at 95% confidence, formulated as a linear program and solved with SciPy.
- Mean-CVaR optimization with a minimum expected-return constraint.
- A chronological ten-year training window and three-year out-of-sample evaluation window.
- Five strategies: equal-weight buy-and-hold, static CVaR, monthly rolling CVaR, static mean-CVaR, and monthly rolling mean-CVaR.
- Exploratory analysis of price growth, return distributions, correlations, rolling volatility, asset risk and return, and principal components.
- Performance comparisons using cumulative wealth, drawdown, realized tail risk, volatility, and Sharpe ratio; allocation plots and a mean-CVaR frontier.

The portfolio universe is NVDA, AAPL, MSFT, AMZN, GOOGL, AVGO, META, TSLA, WMT, and AMD. The default constraints are fully invested, long-only portfolios. Transaction costs are configurable and default to zero.

[`task1_adam.py`](task1_adam.py) contains the team's adaptive Adam implementation and example benchmarks for Rosenbrock, Rastrigin, and an ill-conditioned quadratic.

## Contributions and provenance

- **miracl-3:** the `task2-namanh` development branch records six commits extending the portfolio notebook, exploratory analysis, figures, and reporting workflow.
- **JarvisHunter:** the original project setup and the optimizer task, including the later optimizer update and problem information sheet.
- The full team history, including merges, is retained. This repository presents collaborative coursework; it does not claim sole authorship of the project.

The portfolio edition starts from upstream commit [`57b9bec`](https://github.com/JarvisHunter/optimization_final_project/commit/57b9bec43183e5c6ba56ed1d18f1a53b72631019), which contains the merged course submission. Subsequent portfolio documentation is maintained here.

## Run locally

The original project environment used Python 3.11. From the repository root:

```bash
python -m venv .venv
```

Activate the environment with `.venv\Scripts\Activate.ps1` in Windows PowerShell or `source .venv/bin/activate` on macOS/Linux, then run:

```bash
python -m pip install -r requirements.txt
python -m jupyterlab task2.ipynb
```

In the notebook's configuration cell, select the bundled price snapshot to avoid downloading a changing dataset:

```python
LOCAL_PRICE_FILE = "Data/stock_data.csv"
```

The tracked path uses a capital **D** in `Data`, which matters on case-sensitive systems. The CSV covers May 6, 2013 through May 1, 2026. Run the notebook from its repository directory so the data and figure paths resolve correctly.

Leaving `LOCAL_PRICE_FILE = None` downloads prices through `yfinance`. Set a fixed `END_DATE` if using that mode for a reproducible experiment; the archived notebook defaults to the latest available data. Running the notebook with `EXPORT_FIGURES = True` overwrites the corresponding files in `figures/`.

To run the companion optimizer benchmarks:

```bash
python task1_adam.py
```

## Repository contents

| Path | Contents |
| --- | --- |
| `task2.ipynb` | Main portfolio optimization and backtesting notebook, with saved outputs |
| `task2_og.ipynb` | Earlier portfolio notebook retained from the course project |
| `task1_adam.py` | Adaptive Adam optimizer and benchmark examples |
| `Data/stock_data.csv` | Historical price snapshot |
| `figures/` | Saved exploratory analysis and portfolio comparison figures |
| `reports/Optimization_Final_Project_Report.pdf` | Final project report |
| `Optimization_Project_Problem1.pdf` | Original information sheet for the optimizer task |

## Interpretation and reproducibility

The figures and notebook outputs are archived course results. Backtest outcomes depend on the selected assets, data window, trading assumptions, and return target. The fixed ten-stock universe and default zero transaction costs limit how broadly those outcomes should be interpreted. Package versions were not locked in the original submission; the requirements file lists the direct packages needed to explore the project.

The course source and recorded outputs are preserved in this portfolio edition. No new performance claims are introduced.

## Academic CV description

**CVaR Portfolio Optimization — Collaborative course project, 2026.** Developed and evaluated historical CVaR and mean-CVaR portfolio models using linear programming, chronological out-of-sample backtesting, monthly rebalancing, and exploratory risk analysis in Python. Personal contributions are documented above and in the Git history.
