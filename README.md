# Investment Strategy Evaluation

A reproducible evaluation of a conventional 60/40 portfolio and a simple rules-based trend overlay. The project asks whether reducing exposure after a sustained market decline improves the portfolio's risk-adjusted outcome sufficiently to justify the loss of return and the additional implementation cost.

The accompanying report is intended as an analytical investment-product assessment, rather than investment advice or a recommendation to invest.

## Contents

| File | Purpose |
| --- | --- |
| `Investment Strategy Code.ipynb` | Full Python analysis: data collection, portfolio construction, backtest, robustness checks and charts. |
| `Investment_portfolio_analysis.pdf` | Written report setting out the research question, methodology, results, limitations and conclusion. |

## Approach

- **Assets:** SPY (US equities), IEF (7–10 year US Treasuries) and BIL (1–3 month US Treasury bills).
- **Sample:** daily adjusted close prices from January 2014 to December 2025, converted to month-end observations. The backtest runs from January 2015 to December 2025.
- **Baseline:** a monthly rebalanced 60% equity / 40% bond portfolio.
- **Overlay:** a 10-month moving-average rule, applied with a one-month signal lag. Assets below their moving average are moved to BIL; assets above it retain their strategic allocation.
- **Implementation:** portfolio drift is accounted for before rebalancing, with transaction-cost sensitivity tests included.

## Headline findings

Over the historical sample, the 10-month overlay reduced the maximum drawdown relative to the conventional 60/40 portfolio, but delivered lower annualised return, lower Sharpe ratio and substantially higher turnover. The report therefore does **not** present it as a superior replacement for a conventional balanced portfolio. Its potential role is narrower: a risk-sensitive client who values drawdown reduction and accepts lower expected return and higher implementation friction.

## Reproducing the analysis

1. Clone or download this repository.
2. Install Python 3.10+ and the required packages:

   ```bash
   pip install yfinance pandas numpy matplotlib
   ```

3. Open `Investment Strategy Code.ipynb` in Jupyter Notebook, JupyterLab or VS Code.
4. Run the notebook from top to bottom. It downloads the price data using `yfinance`, so results may change slightly if the underlying provider revises its data history.

## Important limitations

- The analysis is historical and does not demonstrate future performance.
- SPY, IEF and BIL are practical ETF proxies, not a full representation of every equity, bond or cash investment.
- Month-end signals can miss intra-month drawdowns.
- The transaction-cost assumptions are illustrative and do not fully model bid–ask spreads, market impact, taxes or operational constraints.

## Author note

AI tools supported the development of the Python implementation, including code structuring, debugging and technical explanation. The research question, model choices, code review, calculation verification, interpretation and final presentation were completed independently by the author, who retains sole responsibility for the analysis.
