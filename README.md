# mwg-vnm-risk-return-capm-var
# Risk–Return Analysis and Portfolio Optimisation of MWG and VNM (CAPM & VaR)

**Evidence from the Vietnamese stock market, January 2023 – December 2025**

Course project for *Financial Risk Management*, Advanced Education Program, National Economics University (NEU), Hanoi. Class: Corporate Finance 65A. Lecturer: Dr. Dinh Thi Hong Theu.

All calculations are done in Excel with live formulas, so every result is traceable back to the raw data.

---

## Overview

This project analyses the risk and return of two large-cap stocks listed on HOSE, **Mobile World Investment Corporation (MWG)** and **Vietnam Dairy Products JSC (VNM)**, over 748 trading sessions (3 Jan 2023 – 31 Dec 2025). The two stocks are both exposed to Vietnamese household consumption but sit at opposite ends of the cycle: MWG is a cyclical, recovery-driven retailer, while VNM is a mature, defensive dairy leader.

The analysis uses the VN-Index as the market benchmark and the 10-year government bond yield as the risk-free rate.

## Research questions

1. How did MWG and VNM perform, in return and risk, relative to the VN-Index?
2. How large is their systematic risk (beta), and did they earn the return CAPM requires?
3. Can a portfolio of the two stocks improve the risk–return trade-off, and what is the optimal allocation?
4. How large are the downside risks (VaR), and how sensitive are required returns and portfolio values to changes in interest rates, risk premia, and market falls?

## Methods

- Daily simple returns, annualised with 252 trading days; Sharpe ratio
- Correlation and covariance matrices (including a stress-period correlation on days when the VN-Index moved more than 2%)
- Long-only two-asset efficient frontier, minimum-variance portfolio, tangency portfolio, and Capital Allocation Line
- Single-index regression (beta, alpha, R², t-statistics, confidence intervals), with systematic vs. non-systematic risk decomposition
- CAPM required return, Security Market Line, and Jensen's alpha
- Value at Risk: parametric and historical (95% / 99%), expected shortfall, √t scaling for 10-day VaR, and backtesting
- Scenario and sensitivity analysis (risk-free rate, market risk premium, market-fall losses)

## Data

| Item | Detail |
|---|---|
| Stocks | MWG, VNM (daily closing prices, HOSE) |
| Benchmark | VN-Index (daily close) |
| Risk-free rate | Vietnam 10-year government bond yield (average 3.16% p.a. over the sample) |
| Sample | 3 Jan 2023 – 31 Dec 2025: 748 prices, 747 daily returns per series |
| Source | Historical price tables from Investing.com |

**Data validation** (sheet `Data Check`, all checks passed): ascending dates, 0 duplicated dates, 0 error or missing cells across 2,992 price and yield cells, 0 daily returns beyond the HOSE ±7% limit, and plausible correlation with the VN-Index (0.649 for MWG, 0.526 for VNM), which confirms the rows are correctly aligned.

## Key findings

| Metric (annualised) | MWG | VNM | VN-Index |
|---|---|---|---|
| Mean return | 29.32% | -2.90% | 19.61% |
| Volatility | 32.11% | 21.43% | 17.37% |
| Sharpe ratio (Rf = 3.16%) | 0.814 | -0.283 | 0.947 |
| Holding-period return | 104.7% | -14.3% | 70.9% |
| Beta | 1.200 | 0.648 | 1.000 |
| Share of variance explained by the market (R²) | 42.1% | 27.6% | n/a |
| 1-day parametric VaR (95%) | 3.21% | 2.23% | n/a |

- **MWG was rewarded for its risk, VNM was not.** MWG earned the highest return but with almost twice the index's volatility; VNM lost money despite lower volatility. The VN-Index achieved a higher Sharpe ratio than either stock.
- **Optimal allocation depends on the objective.** Because VNM's excess return was negative, the long-only tangency portfolio is 100% MWG, while the minimum-variance portfolio holds 21.7% MWG and 78.3% VNM.
- **Diversification weakens under stress.** The MWG–VNM correlation is 0.217 in normal conditions but rises to 0.758 on the 42 days when the VN-Index moved more than 2%.
- **Normal-distribution VaR understates extreme losses.** Parametric VaR is reasonable at 95%, but at 99% MWG recorded 13 exceptions against 7.5 expected, so tail risk is higher than the normal model suggests (fat tails confirmed by Jarque–Bera tests).
- **Most risk is stock-specific.** The market explains only about 42% (MWG) and 28% (VNM) of variance, so firm-specific risk dominates.

## Repository structure

```
.
├── README.md
├── report/
│   └── MWG_VNM_Risk_Return_Report.pdf      # Full written report (also provided as .docx)
└── model/
    └── MWG_VNM_Risk_Return_Calculate.xlsx  # Excel workbook with all calculations
```

## Workbook map

| Group | Sheets |
|---|---|
| Summary | `Summary` |
| Raw data | `MWG - Raw`, `VNM - Raw`, `VNindex - Raw`, `Bond Yield 10 year - Raw`, `Raw Data` |
| Validation | `Data Check` |
| Returns and statistics | `Return`, `Port Returns`, `Descriptive` |
| Correlation and portfolio | `Covariance và Correlation`, `Portfolio`, `CAL` |
| Market model | `Regression`, `CAPM & SML` |
| Risk | `VaR`, `Stress Corr`, `Scenarios` |

## How to use

1. Download `MWG_VNM_Risk_Return_Calculate.xlsx` and open it in Excel.
2. Start from the `Summary` sheet, then follow the sheets in the order above.
3. Every result is a formula linked to the raw-data sheets. To update the analysis, paste new price data into the raw sheets and the downstream sheets will recalculate.
4. Read the report for the full theory, context, and interpretation of the results.

## Limitations

- The sample covers only three years and two stocks, so estimates of beta, alpha, and optimal weights are sensitive to the chosen window.
- Parametric VaR assumes normally distributed returns, which the data reject (fat tails).
- Portfolio optimisation is long-only and uses historical averages as expected returns, which are noisy.
- The market return in CAPM is the sample mean of the VN-Index, so the result reflects a strong market period.


## Disclaimer

This project was prepared for educational purposes only and does not constitute investment advice. Price data were obtained from Investing.com and remain the property of their respective owners.
